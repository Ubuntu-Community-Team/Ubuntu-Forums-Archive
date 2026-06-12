---
title: "Citrix client - Verisign Class 3"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by adityabankar on 2009-04-29
Hi,

I followed this HowTo:[http://ubuntuforums.org/showthread.php?t=85398&page=4]("http://ubuntuforums.org/showthread.php?t=85398&page=4")
and installed citrix on my ubuntu 9.04. Citrix starts by says 'You have not chosen to trust "Verisign.....".
After searching the message on google I got this link: [http://www.verisign.com/support/verisign-intermediate-ca/secure-site-intermediate/index.html]("http://www.verisign.com/support/verisign-intermediate-ca/secure-site-intermediate/index.html")

I copied the certificate text in /usr/lib/ICAClient/keystore/cacerts/Class3.cer. But still I get the same message saying that 'You have not chosen...". Should the filename of certificate be something else?

Thanks,
-Aditya

---

### Post by adityabankar on 2009-05-03
I did this too to copy all the available certificates, but no luck.
sudo cp -i /etc/ssl/certs/* /usr/lib/ICAClient/keystore/cacerts/

Any suggestions?

-Aditya

---

### Post by KaiO on 2009-05-05
I think the certificate needs to be a .crt file (not .cer).
It should be put in the /usr/lib/ICAClient/keystore/cacerts/
as root (sudo).
You may have to do some googelin' to fint the .crt fil you need unless this works for you:
[https://www.verisign.com/support/thawte-roots.zip](https://www.verisign.com/support/thawte-roots.zip)

---

### Post by adityabankar on 2009-05-08
I was not able to get anything different in that path. Still trying.

---

### Post by nicholas_22 on 2009-05-09
I managed to get it to work by following the following steps:

1) Install Citrix Server ICA client (linuxx86.tar.gz) from Citrix website
2) Save the Verisign Class 3 Secure Server CA certificate I attached
3) Save as/rename it to class3.crt
4) Move this file to your ICAClient/linuxx86/keystore/cacerts folder 
5) Try again now, it should work.

Regards
Nick T.

ps: Tested with success on Kubuntu 9.04 and openSUSE 11 (Mozilla v3+)

---

### Post by adityabankar on 2009-05-13
This caused the following error
*** glibc detected *** /usr/lib/ICAClient/wfica: double free or corruption (top): 0x089ce480 ***
======= Backtrace: =========
...
..Many more lines
...
I refered this: [http://ubuntuforums.org/showthread.php?t=175050](http://ubuntuforums.org/showthread.php?t=175050)
and again I get what I used to get.

-Aditya

---

### Post by ariel on 2009-05-16
> **nicholas_22 said:**
> I managed to get it to work by following the following steps:

1) Install Citrix Server ICA client (linuxx86.tar.gz) from Citrix website
2) Copy and paste Verisign Class 3 Certificate to text file (include ----...----- lines)
----BEGIN CERTIFICATE-----
MIIEnDCCBAWgAwIBAgIQdTN9mrDhIzuuLX3kRpFi1DANBgkqhkiG9w0BAQUFADBf
MQswCQYDVQQGEwJVUzEXMBUGA1UEChMOVmVyaVNpZ24sIEluYy4xNzA1BgNVBAsT
LkNsYXNzIDMgUHVibGljIFByaW1hcnkgQ2VydGlmaWNhdGlvbiBBdXRob3JpdHkw
HhcNMDUwMTE5MDAwMDAwWhcNMTUwMTE4MjM1OTU5WjCBsDELMAkGA1UEBhMCVVMx
FzAVBgNVBAoTDlZlcmlTaWduLCBJbmMuMR8wHQYDVQQLExZWZXJpU2lnbiBUcnVz
dCBOZXR3b3JrMTswOQYDVQQLEzJUZXJtcyBvZiB1c2UgYXQgaHR0cHM6Ly93d3cu
dmVyaXNpZ24uY29tL3JwYSAoYykwNTEqMCgGA1UEAxMhVmVyaVNpZ24gQ2xhc3Mg
MyBTZWN1cmUgU2VydmVyIENBMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKC
AQEAlcMhEo5AxQ0BX3ZeZpTZcyxYGSK4yfx6OZAqd3J8HT732FXjr0LLhzAC3Fus
cOa4RLQrNeuT0hcFfstG1lxToDJRnXRkWPkMmgDqXkRJZHL0zRDihQr5NO6ziGap
paRa0A6Yf1gNK1K7hql+LvqySHyN2y1fAXWijQY7i7RhB8m+Ipn4G9G1V2YETTX0
kXGWtZkIJZuXyDrzILHdnpgMSmO3ps6wAc74k2rzDG6fsemEe4GYQeaB3D0s57Rr
4578CBbXs9W5ZhKZfG1xyE2+xw/j+zet1XWHIWuG0EQUWlR5OZZpVsm5Mc2JYVjh
2XYFBa33uQKvp/1HkaIiNFox0QIDAQABo4IBgTCCAX0wEgYDVR0TAQH/BAgwBgEB
/wIBADBEBgNVHSAEPTA7MDkGC2CGSAGG+EUBBxcDMCowKAYIKwYBBQUHAgEWHGh0
dHBzOi8vd3d3LnZlcmlzaWduLmNvbS9ycGEwMQYDVR0fBCowKDAmoCSgIoYgaHR0
cDovL2NybC52ZXJpc2lnbi5jb20vcGNhMy5jcmwwDgYDVR0PAQH/BAQDAgEGMBEG
CWCGSAGG+EIBAQQEAwIBBjApBgNVHREEIjAgpB4wHDEaMBgGA1UEAxMRQ2xhc3Mz
Q0EyMDQ4LTEtNDUwHQYDVR0OBBYEFG/sr6DdiqTv9SoQZy0/VYK81+8lMIGABgNV
HSMEeTB3oWOkYTBfMQswCQYDVQQGEwJVUzEXMBUGA1UEChMOVmVyaVNpZ24sIElu
Yy4xNzA1BgNVBAsTLkNsYXNzIDMgUHVibGljIFByaW1hcnkgQ2VydGlmaWNhdGlv
biBBdXRob3JpdHmCEHC65B0Q2Sk0tjjKewPMur8wDQYJKoZIhvcNAQEFBQADgYEA
w34IRl2RNs9n3Nenr6+4IsOLBHTTsWC85v63RBKBWzFzFGNWxnIu0RoDQ1w4ClBK
Tc3athmo9JkNr+P32PF1KGX2av6b9L1S2T/L2hbLpZ4ujmZSeD0m+v6UNohKlV4q
TBnvbvqCPy0D79YoszcYz0KyNCFkR9MgazpM3OYDkAw=
-----END CERTIFICATE-----
3)Save it as Class3.crt
4)Move this file to your ICAClient/linuxx86/keystore/cacerts folder (or very similar)
5)Try again now, it should work.

Regards
Nick T.

I started seeing this problem a week or so ago on my 9.04 box. The above method didn't solve the issue. Actually I also tried downloading all certificates directly from verisign ([https://knowledge.verisign.com/support/ssl-certificates-support/index?page=content&id=AR657](https://knowledge.verisign.com/support/ssl-certificates-support/index?page=content&id=AR657)) and installing them in the cacerts folder, and it also didn't help.

What fixed this problem for me was: in firefox, Edit > Preferences > Advanced > Encryption > View Certificates, browse the list to find the VeriSign entries, then export the ones that are Class 3 (In my case there are 7), one by one, in format X509 (PEM), and store them in your "cacert" folder with the ".crt" extension (you have to manually add the extension when you save the certificates).

You don't need to restart firefox nor re-login into your citrix portal, just try launching any citrix app again, this time it should work.

---

### Post by nicholas_22 on 2009-05-16
> **ariel said:**
> I started seeing this problem a week or so ago on my 9.04 box. The above method didn't solve the issue. Actually I also tried downloading all certificates directly from verisign ([https://knowledge.verisign.com/support/ssl-certificates-support/index?page=content&id=AR657](https://knowledge.verisign.com/support/ssl-certificates-support/index?page=content&id=AR657)) and installing them in the cacerts folder, and it also didn't help.

What fixed this problem for me was: in firefox, Edit > Preferences > Advanced > Encryption > View Certificates, browse the list to find the VeriSign entries, then export the ones that are Class 3 (In my case there are 7), one by one, in format X509 (PEM), and store them in your "cacert" folder with the ".crt" extension (you have to manually add the extension when you save the certificates).

You don't need to restart firefox nor re-login into your citrix portal, just try launching any citrix app again, this time it should work.

My post assumes that you are able to properly copy and paste from this forum and/or the VeriSign website (are you using K-based text editors which alter your formatting?)
If it didn't work, some characters were altered, simple as that, because what you're doing is the same principle. 
I edited the post and have included an attachment, for those having difficulties navigating this with copy and paste (see above)

FYI, if you're going to follow the Firefox export methodology, there is no need for the brute force approach of exporting all certificates,
the "Verisign Class 3 Secure Server CA" (which you can obtain from VeriSign or my above post) will do.

Regards
Nick T.

---

### Post by adityabankar on 2009-05-22
:D You are correct. After exporting the certificate from Firefox the client is working fine. Many Many thanks.
Last time when you posted the file I didn't use any editor for copy-paste. I used cat > Class3.crt, then selected the entire text and middle clicked on the terminal. I think the change in format would have caused that crash "glibc detected..."

Thanks,
Aditya

---

### Post by mca1954 on 2009-11-20
:D Many thanks, copy Verisign Class 3 cert and rename solve all problem with using Citrix client. This works also under Ubuntu 9.10 //mca1954

---

### Post by pigphish on 2010-01-28
> **ariel said:**
> 
What fixed this problem for me was: in firefox, Edit > Preferences > Advanced > Encryption > View Certificates, browse the list to find the VeriSign entries, then export the ones that are Class 3 (In my case there are 7), one by one, in format X509 (PEM), and store them in your "cacert" folder with the ".crt" extension (you have to manually add the extension when you save the certificates).



sweet fix, worked for me. I just did one... the one with the exact same name as the error.

---

