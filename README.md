# Zimbra-commerical-SSL-certificate-install


 
 Create CSR via, adminconsole on 7071 port.
 
Login to admin panel (zimbra)

And there, go to Home-Configure-certificates-select the domain you want create .csr
right click (Install certificate)
 
1) Select The target server- choose which domain you want to do create CSR.

2) Choose the Installation Option 
select
 Generate the CSR fir the commerical certificate authorize3) Generate the certificate singing Request

Provide required details
Then download the CSR or you can also access the csr on below path
  
 vi /opt/zimbra/ssl/zimbra/commercial/commercial.csr

Once brought the certificate from the service provider.

The certificate should be contains below files.
1. AddTrustExternalCARoot.crt
2. COMODORSAAddTrustCA.crt
3. COMODORSADomainValidationSecureServerCA.crt
4. mail_xxxx_com.crt


  cd tmp
 
  #ls
  
  Make certificate directory and copy the 4 files to in it.
  
   cd certificate/

  #cat AddTrustExternalCARoot.crt COMODORSAAddTrustCA.crt COMODORSADomainValidationSecureServerCA.crt > /tmp/commercial_ca.crt
  
  #cp mail_xxxx_com.crt /tmp/commercial.crt
  #cd ..
  #ls
  come back and check the newly created files exist??


  # [root@mail tmp]# /opt/zimbra/bin/zmcertmgr verifycrt comm /opt/zimbra/ssl/zimbra/commercial/commercial.key /tmp/commercial.crt /tmp/commercial_ca.crt
#               /opt/zimbra/bin/zmcertmgr deploycrt comm /tmp/commercial.crt /tmp/commercial_ca.crt
zimbra@$          zmtlsctl redirect
#              su zimbra
#     zmcontrol restart
#              exit
