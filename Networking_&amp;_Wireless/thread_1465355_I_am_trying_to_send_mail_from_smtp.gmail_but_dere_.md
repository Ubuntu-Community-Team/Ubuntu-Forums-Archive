---
title: "I am trying to send mail from smtp.gmail but dere is some problem with 'data' command"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by H.om on 2010-04-29
This is what I did:


myname@myname:~$openssl s_client -connect smtp.gmail.com:465
CONNECTED(00000003)
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
verify error:num=20:unable to get local issuer certificate
verify return:1
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
verify error:num=27:certificate not trusted
verify return:1
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
verify error:num=21:unable to verify the first certificate
verify return:1
---
Certificate chain
0 s:/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
i:/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.co…
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDYzCCAsygAwIBAgIQUR2EgGT4+hGKEhCgLM…
zjELMAkGA1UEBhMCWkExFTATBgNVBAgTDFdlc3…
Q2FwZSBUb3duMR0wGwYDVQQKExRUaGF3dGUgQ2…
CxMfQ2VydGlmaWNhdGlvbiBTZXJ2aWNlcyBEaX…
d3RlIFByZW1pdW0gU2VydmVyIENBMSgwJgYJKo…
cnZlckB0aGF3dGUuY29tMB4XDTA3MDczMDAwMD…
aDELMAkGA1UEBhMCVVMxEzARBgNVBAgTCkNhbG…
dW50YWluIFZpZXcxEzARBgNVBAoTCkdvb2dsZS…
Z21haWwuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4…
tcwDjpp6dJGifjiR5M2DbEbrsIOlth80nk5A7x…
s3hWep05ybyiCmOzGL5K0zy3jIq0vOWy+4pLv2…
WF4p0/Kl014+wnukIpj4MdF35rIkgQIDAQABo4…
AQUFBwMBBggrBgEFBQcDAjBABgNVHR8EOTA3MD…
YXd0ZS5jb20vVGhhd3RlUHJlbWl1bVNlcnZlck…
MCQwIgYIKwYBBQUHMAGGFmh0dHA6Ly9vY3NwLn…
BAIwADANBgkqhkiG9w0BAQUFAAOBgQBeNYOZwM…
52e8bLnWqd03mWgn/+TQtrwbE1E6pVuQaZJY33…
xwArHo20iAss3MLQR8tDXWfBoH2Lk9BBsEKDRP…
v97epiiFBA==
-----END CERTIFICATE-----
subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
issuer=/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.co…
---
No client certificate CA names sent
---
SSL handshake has read 1017 bytes and written 300 bytes
---
New, TLSv1/SSLv3, Cipher is RC4-MD5
Server public key is 1024 bit
Compression: NONE
Expansion: NONE
SSL-Session:
Protocol : TLSv1
Cipher : RC4-MD5
Session-ID: 5CACB3FFABA01D9EDF92C34A82DB5405804D59B4…
Session-ID-ctx:
Master-Key: DA23D6F9F6870B11BB1A22CF4756D19660B72D55…
Key-Arg : None
Start Time: 1272464640
Timeout : 300 (sec)
Verify return code: 21 (unable to verify the first certificate)
---
220 mx.google.com ESMTP 24sm236516bkr.18
helo testname
250 mx.google.com at your service
auth login
334 VXNlcm5hbWU6
YdsadfudksUQ==
334 UGFzc3dvcmQ6
MDJkdiMKdOdkkdsTE=
235 2.7.0 Accepted
data
503 5.5.1 MAIL first. 24sm236516bkr.18
mail from:<testemail@gmail.com>
250 2.1.0 OK 24sm236516bkr.18
data
503 5.5.1 RCPT first. 24sm236516bkr.18
rcpt to:<testemail@gmail.com>
250 2.1.5 OK 24sm236516bkr.18
data
354 Go ahead 24sm236516bkr.18
I am typing here
but it never ends
I am putting a . in next line
.
still the data is not ending
what shhoul I do
.

----------------------------
Now i am entering a '.' in data part but still its expecting more data.How to end data?

---

