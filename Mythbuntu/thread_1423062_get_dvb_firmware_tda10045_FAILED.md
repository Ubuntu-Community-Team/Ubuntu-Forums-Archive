---
title: "get_dvb_firmware tda10045 FAILED"
date: 2010-03-06
forum: Mythbuntu
---

### Post by paul-cyt on 2010-03-06
This post is related to: [http://ubuntuforums.org/showthread.php?t=1423032](http://ubuntuforums.org/showthread.php?t=1423032)

Does anyone know how to get (dvb-fe-tda10045.fw) firmware?  ie copy out of the hauppauge installation files?  The offical download script is no longer working.  Seems technotrend have changed the website?


Using Mythbunutu 10.04 64bit:

$ ./get_dvb_firmware tda10045

--2010-03-06 11:59:58--  [http://www.technotrend.de/new/217g/tt_budget_217g.zip](http://www.technotrend.de/new/217g/tt_budget_217g.zip)
Resolving [www.technotrend.de]("http://www.technotrend.de/")...  212.185.20.148
Connecting to [www.technotrend.de|212.185.20.148|:80]("http://www.technotrend.de%7c212.185.20.148%7c/")... connected.
HTTP request sent, awaiting response... 403 Forbidden
2010-03-06 11:59:58 ERROR 403: Forbidden.

wget failed - unable to download firmware at ./get_dvb_firmware line  577.

---

### Post by paul-cyt on 2010-03-06
Seems I've found tda10045 firmware revision 2c
Here is how i did it:

$ apt-get install rpm2cpio

download this:
[ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandriva/2008.1/non-free/release/binary/x86_64/dvb-firmware-frontends-20061120-1plf2007.1.noarch.rpm](ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandriva/2008.1/non-free/release/binary/x86_64/dvb-firmware-frontends-20061120-1plf2007.1.noarch.rpm)

$ rpm2cpio dvb-firmware-frontends-20061120-1plf2007.1.noarch.rpm | cpio -idmv

Now you have lib/firmware
copy this to

/lib/firmware


log now shows:

tda1004x: waiting for firmware upload (dvb-fe-tda10045.fw)...
budget_ci dvb 0000:05:00.0: firmware: requesting dvb-fe-tda10045.fw
tda1004x: firmware upload complete
tda1004x: found firmware revision 2c -- ok

---

