---
title: "wget won't download from the blackberry website"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by go_beep_yourself on 2009-03-29
I'm on a slow connection, so downloading large files can be a problem. I need the ability to resume a download later if I can't download it all at one time (Just like you can do with torrents). I'm using my Blackberry phone as a modem and currently in Windows because it some times acts up in Linux. So I want to download with wget -c, but it's giving me these errors and downloading a small file instead of the Blackberry software at this website: [https://www.blackberry.com/Downloads/browseSoftware.do](https://www.blackberry.com/Downloads/browseSoftware.do) Can anyone help me in getting the software to download? I'm trying to get Blackberry Desktop Software 4.7 (with Media Manager). Thanks in advance.

[PHP]C:\>wget -c https://www.blackberry.com/Downloads/contactFormPreload.do?code=A8BA
A56554F96369AB93E4F3BB068C22&dl=249EF3F634E5779CAAE8D14EE93E890D
SYSTEM_WGETRC = c:/progra~1/wget/etc/wgetrc
syswgetrc = D:\GnuWin32/etc/wgetrc
--2009-03-29 16:54:50--  https://www.blackberry.com/Downloads/contactFormPreload
.do?code=A8BAA56554F96369AB93E4F3BB068C22
Resolving www.blackberry.com... 216.9.245.101
Connecting to www.blackberry.com|216.9.245.101|:443... connected.
ERROR: cannot verify www.blackberry.com's certificate, issued by `/C=ZA/ST=Weste
rn Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN
=Thawte Premium Server CA/emailAddress=premium-server@thawte.com':
  Unable to locally verify the issuer's authority.
To connect to www.blackberry.com insecurely, use `--no-check-certificate'.
Unable to establish SSL connection.
'dl' is not recognized as an internal or external command,
operable program or batch file.

C:\>wget -c --no-check-certificate https://www.blackberry.com/Downloads/contactF
ormPreload.do?code=A8BAA56554F96369AB93E4F3BB068C22&dl=249EF3F634E5779CAAE8D14EE
93E890D
SYSTEM_WGETRC = c:/progra~1/wget/etc/wgetrc
syswgetrc = D:\GnuWin32/etc/wgetrc
--2009-03-29 16:54:58--  https://www.blackberry.com/Downloads/contactFormPreload
.do?code=A8BAA56554F96369AB93E4F3BB068C22
Resolving www.blackberry.com... 216.9.245.101
Connecting to www.blackberry.com|216.9.245.101|:443... connected.
WARNING: cannot verify www.blackberry.com's certificate, issued by `/C=ZA/ST=Wes
tern Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/
CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com':
  Unable to locally verify the issuer's authority.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `contactFormPreload.do@code=A8BAA56554F96369AB93E4F3BB068C22'

    [   <=>                                 ] 9,934       9.52K/s   in 1.0s

2009-03-29 16:55:04 (9.52 KB/s) - `contactFormPreload.do@code=A8BAA56554F96369AB
93E4F3BB068C22' saved [9934]

'dl' is not recognized as an internal or external command,
operable program or batch file.

C:\>[/PHP]

---

### Post by timandjulz on 2011-01-13
In case someone else hits this page first... the answer is to put quotes around the URL.

---

