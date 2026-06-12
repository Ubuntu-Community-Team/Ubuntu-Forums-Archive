---
title: "BUG: Thawte_Premium_Server_CA.pem  is not right version in Kubuntu 11.04"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by cppcdr on 2011-05-18
Hello, I am posting this as all variants even though I am running in Kubuntu 11.04 since this may be an error which affects all versions of ubuntu. I have seen some posts here that say that WPA is not working for some people, and this may be the cause.

I installed Kubuntu 11.04 yesterday from an iso which was created about 5 days ago. All available updates were installed also. I can access WEP and non-secured networks with no problems, however my workplace wifi which uses WPA PEAP with MSCHAPV2 was unable to connect. The certificate used at my workplace is Thawte_Premium_Server_CA.pem. Every time I tried to connect, it said that my password was wrong.

At first, I thought that the problem may have been with the KDE network manager, and so I uninstalled it and installed WICD since this had solved issues like this in the past. However, I got the same problem.

I then went on the Thawte website and downloaded a copy of the latest version of Thawte_Premium_Server_CA.pem and to my surprise this is what I got:

For the original version (the one supplied with Kubuntu 11.04) I get this:
>openssl x509 -text -in Thawte_Premium_Server_CA.pem.
backCertificate:
    Data:
        Version: 3 (0x2)
        [COLOR=Red]Serial Number: 1 (0x1)
        Signature Algorithm: md5WithRSAEncryption[/COLOR]
        Issuer: C=ZA, ST=Western Cape, L=Cape Town, O=Thawte Consulting cc, OU=Certification Services Division, CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
        Validity
            Not Before: Aug  1 00:00:00 1996 GMT
            Not After : Dec 31 23:59:59 2020 GMT
        Subject: C=ZA, ST=Western Cape, L=Cape Town, O=Thawte Consulting cc, OU=Certification Services Division, CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
            RSA Public Key: (1024 bit)
                Modulus (1024 bit):
                    00:d2:36:36:6a:8b:d7:c2:5b:9e:da:81:41:62:8f:
                    38:ee:49:04:55:d6:d0:ef:1c:1b:95:16:47:ef:18:
                    48:35:3a:52:f4:2b:6a:06:8f:3b:2f:ea:56:e3:af:
                    86:8d:9e:17:f7:9e:b4:65:75:02:4d:ef:cb:09:a2:
                    21:51:d8:9b:d0:67:d0:ba:0d:92:06:14:73:d4:93:
                    cb:97:2a:00:9c:5c:4e:0c:bc:fa:15:52:fc:f2:44:
                    6e:da:11:4a:6e:08:9f:2f:2d:e3:f9:aa:3a:86:73:
                    b6:46:53:58:c8:89:05:bd:83:11:b8:73:3f:aa:07:
                    8d:f4:42:4d:e7:40:9d:1c:37
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Basic Constraints: critical
                CA:TRUE
    Signature Algorithm: md5WithRSAEncryption
        26:48:2c:16:c2:58:fa:e8:16:74:0c:aa:aa:5f:54:3f:f2:d7:
        c9:78:60:5e:5e:6e:37:63:22:77:36:7e:b2:17:c4:34:b9:f5:
        08:85:fc:c9:01:38:ff:4d:be:f2:16:42:43:e7:bb:5a:46:fb:
        c1:c6:11:1f:f1:4a:b0:28:46:c9:c3:c4:42:7d:bc:fa:ab:59:
        6e:d5:b7:51:88:11:e3:a4:85:19:6b:82:4c:a4:0c:12:ad:e9:
        a4:ae:3f:f1:c3:49:65:9a:8c:c5:c8:3e:25:b7:94:99:bb:92:
        32:71:07:f0:86:5e:ed:50:27:a6:0d:a6:23:f9:bb:cb:a6:07:
        14:42
-----BEGIN CERTIFICATE-----
MIIDJzCCApCgAwIBAgIBATANBgkqhkiG9w0BAQQFADCBzjELMAkGA1UEBhMCWkEx
FTATBgNVBAgTDFdlc3Rlcm4gQ2FwZTESMBAGA1UEBxMJQ2FwZSBUb3duMR0wGwYD
VQQKExRUaGF3dGUgQ29uc3VsdGluZyBjYzEoMCYGA1UECxMfQ2VydGlmaWNhdGlv
biBTZXJ2aWNlcyBEaXZpc2lvbjEhMB8GA1UEAxMYVGhhd3RlIFByZW1pdW0gU2Vy
dmVyIENBMSgwJgYJKoZIhvcNAQkBFhlwcmVtaXVtLXNlcnZlckB0aGF3dGUuY29t
MB4XDTk2MDgwMTAwMDAwMFoXDTIwMTIzMTIzNTk1OVowgc4xCzAJBgNVBAYTAlpB
MRUwEwYDVQQIEwxXZXN0ZXJuIENhcGUxEjAQBgNVBAcTCUNhcGUgVG93bjEdMBsG
A1UEChMUVGhhd3RlIENvbnN1bHRpbmcgY2MxKDAmBgNVBAsTH0NlcnRpZmljYXRp
b24gU2VydmljZXMgRGl2aXNpb24xITAfBgNVBAMTGFRoYXd0ZSBQcmVtaXVtIFNl
cnZlciBDQTEoMCYGCSqGSIb3DQEJARYZcHJlbWl1bS1zZXJ2ZXJAdGhhd3RlLmNv
bTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEA0jY2aovXwlue2oFBYo847kkE
VdbQ7xwblRZH7xhINTpS9CtqBo87L+pW46+GjZ4X9560ZXUCTe/LCaIhUdib0GfQ
ug2SBhRz1JPLlyoAnFxODLz6FVL88kRu2hFKbgifLy3j+ao6hnO2RlNYyIkFvYMR
uHM/qgeN9EJN50CdHDcCAwEAAaMTMBEwDwYDVR0TAQH/BAUwAwEB/zANBgkqhkiG
9w0BAQQFAAOBgQAmSCwWwlj66BZ0DKqqX1Q/8tfJeGBeXm43YyJ3Nn6yF8Q0ufUI
hfzJATj/Tb7yFkJD57taRvvBxhEf8UqwKEbJw8RCfbz6q1lu1bdRiBHjpIUZa4JM
pAwSremkrj/xw0llmozFyD4lt5SZu5IycQfwhl7tUCemDaYj+bvLpgcUQg==
-----END CERTIFICATE-----


For the new downloaded version I get :
>openssl x509 -text -in Thawte_Premium_Server_CA.pem
Certificate:
    Data:
        Version: 3 (0x2)
        [COLOR=Red]Serial Number:
            36:12:22:96:c5:e3:38:a5:20:a1:d2:5f:4c:d7:09:54
        Signature Algorithm: sha1WithRSAEncryption[/COLOR]
        Issuer: C=ZA, ST=Western Cape, L=Cape Town, O=Thawte Consulting cc, OU=Certification Services Division, CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
        Validity
            Not Before: Aug  1 00:00:00 1996 GMT
            Not After : Jan  1 23:59:59 2021 GMT
        Subject: C=ZA, ST=Western Cape, L=Cape Town, O=Thawte Consulting cc, OU=Certification Services Division, CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
            RSA Public Key: (1024 bit)
                Modulus (1024 bit):
                    00:d2:36:36:6a:8b:d7:c2:5b:9e:da:81:41:62:8f:
                    38:ee:49:04:55:d6:d0:ef:1c:1b:95:16:47:ef:18:
                    48:35:3a:52:f4:2b:6a:06:8f:3b:2f:ea:56:e3:af:
                    86:8d:9e:17:f7:9e:b4:65:75:02:4d:ef:cb:09:a2:
                    21:51:d8:9b:d0:67:d0:ba:0d:92:06:14:73:d4:93:
                    cb:97:2a:00:9c:5c:4e:0c:bc:fa:15:52:fc:f2:44:
                    6e:da:11:4a:6e:08:9f:2f:2d:e3:f9:aa:3a:86:73:
                    b6:46:53:58:c8:89:05:bd:83:11:b8:73:3f:aa:07:
                    8d:f4:42:4d:e7:40:9d:1c:37
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Basic Constraints: critical
                CA:TRUE
    Signature Algorithm: sha1WithRSAEncryption                                          
        65:90:ac:88:0f:56:d9:e6:30:34:d4:26:c7:d0:50:f1:92:de:                          
        6b:d4:39:88:09:22:c6:a6:63:83:03:f7:99:77:d8:b2:e5:18:                          
        b8:5d:63:f3:d4:73:fb:6c:9c:99:78:f1:4b:78:7d:19:24:c3:                          
        2b:02:84:f8:bc:22:d9:8a:22:d7:a0:fc:71:ec:91:87:20:f1:                          
        b8:ec:b1:e5:55:80:ac:3d:52:c8:39:0e:c2:f0:c0:05:4f:d6:
        82:75:8c:bd:5f:d2:dc:76:9a:05:12:c9:af:72:c3:dc:25:7e:
        a4:4d:8e:17:a5:e0:87:7f:e1:9a:5a:e1:60:dc:64:23:3c:42:
        2e:4d
-----BEGIN CERTIFICATE-----
MIIDNjCCAp+gAwIBAgIQNhIilsXjOKUgodJfTNcJVDANBgkqhkiG9w0BAQUFADCB
zjELMAkGA1UEBhMCWkExFTATBgNVBAgTDFdlc3Rlcm4gQ2FwZTESMBAGA1UEBxMJ
Q2FwZSBUb3duMR0wGwYDVQQKExRUaGF3dGUgQ29uc3VsdGluZyBjYzEoMCYGA1UE
CxMfQ2VydGlmaWNhdGlvbiBTZXJ2aWNlcyBEaXZpc2lvbjEhMB8GA1UEAxMYVGhh
d3RlIFByZW1pdW0gU2VydmVyIENBMSgwJgYJKoZIhvcNAQkBFhlwcmVtaXVtLXNl
cnZlckB0aGF3dGUuY29tMB4XDTk2MDgwMTAwMDAwMFoXDTIxMDEwMTIzNTk1OVow
gc4xCzAJBgNVBAYTAlpBMRUwEwYDVQQIEwxXZXN0ZXJuIENhcGUxEjAQBgNVBAcT
CUNhcGUgVG93bjEdMBsGA1UEChMUVGhhd3RlIENvbnN1bHRpbmcgY2MxKDAmBgNV
BAsTH0NlcnRpZmljYXRpb24gU2VydmljZXMgRGl2aXNpb24xITAfBgNVBAMTGFRo
YXd0ZSBQcmVtaXVtIFNlcnZlciBDQTEoMCYGCSqGSIb3DQEJARYZcHJlbWl1bS1z
ZXJ2ZXJAdGhhd3RlLmNvbTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEA0jY2
aovXwlue2oFBYo847kkEVdbQ7xwblRZH7xhINTpS9CtqBo87L+pW46+GjZ4X9560
ZXUCTe/LCaIhUdib0GfQug2SBhRz1JPLlyoAnFxODLz6FVL88kRu2hFKbgifLy3j
+ao6hnO2RlNYyIkFvYMRuHM/qgeN9EJN50CdHDcCAwEAAaMTMBEwDwYDVR0TAQH/
BAUwAwEB/zANBgkqhkiG9w0BAQUFAAOBgQBlkKyID1bZ5jA01CbH0FDxkt5r1DmI
CSLGpmODA/eZd9iy5Ri4XWPz1HP7bJyZePFLeH0ZJMMrAoT4vCLZiiLXoPxx7JGH
IPG47LHlVYCsPVLIOQ7C8MAFT9aCdYy9X9LcdpoFEsmvcsPcJX6kTY4XpeCHf+Ga
WuFg3GQjPEIuTQ==
-----END CERTIFICATE-----


The first thing that caught my attention was the serial number, and then the signature algorithm. The version supplied with Kubuntu is not the same as that supplied by the official website. Once I installed the new version that I had just downloaded, WICD was able to connect to my workplace network with no problems.

I don't know if this has been reported already and I was wondering if I should file a bug report with ubuntu and/or kubuntu? If this bug has not been reported, it might be worth looking at all the certs and making sure they are updated.

---

### Post by cppcdr on 2011-05-24
Small update:

I just installed Ubuntu 11.04 on another computer and checked the certificates. The default certificate works fine (the one with md5, the original one from kubuntu). So maybe this is an issue with the network manager in kubuntu.

---

