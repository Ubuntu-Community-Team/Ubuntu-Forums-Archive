---
title: "VPN AnyConnect - CERT_VerifyCertificateNow SEC_ERROR_CA_CERT_INVALID"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by pmdserrano on 2009-10-28
Good Day,

I was trying to connect through vpn anyconnect and have an popup error message of "Unable to establish VPN". I tried looking at the logs and found these lines

Oct 28 22:43:24 paul-laptop vpnui: [p:5024  pp:1]: error - Certificates/NSSCertificate.cpp:299 (ffffe024) CERT_VerifyCertificateNow SEC_ERROR_CA_CERT_INVALID
Oct 28 22:43:24 paul-laptop vpnui: [p:5024  pp:1]: error - Certificates/NSSCertificate.cpp:299 (ffffe024) CERT_VerifyCertificateNow SEC_ERROR_CA_CERT_INVALID
Oct 28 22:43:24 paul-laptop vpnui: [p:5024  pp:1]: error - Certificates/NSSCertStore.cpp:402 (fe220011) Verify
Oct 28 22:43:24 paul-laptop vpnui: [p:5024  pp:1]: warning - Certificates/CertHelper.cpp:129 (fe220011) CCertStore::VerifyServerCertificate
Oct 28 22:43:24 paul-laptop vpnui: [p:5024  pp:1]: ConnectMgr.cpp:2046 (0) ConnectMgr :: setPromptAttributes CA is disabled
Oct 28 22:43:30 paul-laptop vpnui: [p:5024  pp:1]: ConnectIfc.cpp:930 (0) ConnectIfc::connect Auth Cookie acquired
Oct 28 22:43:30 paul-laptop vpnui: [p:5024  pp:1]: ConnectIfc.cpp:939 (0) ConnectIfc::connect Config Cookie acquired
Oct 28 22:43:30 paul-laptop vpnui: [p:5024  pp:1]: ConnectMgr.cpp:1128 (0) processIfcData Authentication succeeded
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: warning - ConnectIfc.cpp:1178 (0) ConnectIfc::getUpdateFileContent Unable to locate Update file
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: warning - ConnectIfc.cpp:1009 (0) ConnectIfc::getDownloader Unable to locate downloader
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: ConnectMgr.cpp:4443 (0) ConnectMgr :: launchdownloader Successfully downloaded the downloader
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: ConnectMgr.cpp:4495 (0) ConnectMgr :: launchdownloader Successfully launched the downloader
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: error - ConnectMgr.cpp:4512 (2) ProcessApi :: WaitForProcess Downloader terminated abnormally
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host vpn.timelink.com.
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: ProfileMgr.cpp:428 (0) ProfileMgr :: getHostInitSettings Profile "" not found. Using default settings
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: warning - PreferenceInfoBase.cpp:494 (0) addNewPreference Trying to create an existing preference.
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: ProfileMgr.cpp:356 (0) getProfileNameFromHost No profile available for host vpn.timelink.com.
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: ProfileMgr.cpp:428 (0) ProfileMgr :: getHostInitSettings Profile "" not found. Using default settings
Oct 28 22:43:32 paul-laptop vpnui: [p:5024  pp:1]: warning - PreferenceInfoBase.cpp:494 (0) addNewPreference Trying to create an existing preference.

Any Ideas?

-Paul

---

### Post by casevh on 2009-10-28
Are you using a 64-bit platform?

The instructions at [HTML]http://ubuntuforums.org/showpost.php?p=8178647&postcount=43[/HTML] should work for Ubuntu x64, 9.04 and 9.10. Additional libraries may need to be installed for Kubuntu (see next mesage).

casevh

---

### Post by pmdserrano on 2009-10-29
I'm on 32 bit.
 
-Paul

---

### Post by casevh on 2009-10-31
Which version of Ubuntu? 

Which version of the AnyConnect client?

Are you using just username/password for authentication or is a certificate required, too?

Can you verify that you have libsqlite3 and libxml2 installed?

casevh

---

