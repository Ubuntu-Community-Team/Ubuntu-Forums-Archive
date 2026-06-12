---
title: "OpenVPN connection error."
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by sv650s on 2009-12-26
root@CWLD:/usr/lib/openvpn# openvpn /etc/openvpn/xxxx.ovpn
Sat Dec 26 12:47:40 2009 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Sat Dec 26 12:47:40 2009 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sat Dec 26 12:47:40 2009 Cannot load certificate file xxxx.crt: error:02001002:system library:fopen:No such file or directory: error:20074002:BIO routines:FILE_CTRL:system lib: error:140AD002:SSL routines:SSL_CTX_use_certificate_file:system lib
Sat Dec 26 12:47:40 2009 Exiting
root@CWLD:/usr/lib/openvpn# 

I've some problem connecting to OpenVPN as in above. Does anyone has any idea what does the error mean? Thanks for helping. I'm a newbie starting to use Linux.

Trying to do what I have done in windows with Linux.

---

### Post by mrsteveman1 on 2009-12-29
Probably your config file does not have full paths for the certificate and key files

---

