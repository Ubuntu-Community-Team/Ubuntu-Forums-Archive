---
title: "Galaxy Nexus and libmtp"
date: 2012-01-02
forum: Multimedia Software
---

### Post by akwatve on 2012-01-02
Hi

I recently got Galaxy Nexus.

My laptop could not detect it. So I install gmtp which is supposed be able to read/write stuff.

However, apparently the default libmtp (libmtp8 ) has a bug so I installed the latest version (libmtp.so.9.0.1). A lot of people have reported success after this change. However, in my case, gmtp still crashes with an ugly segmentation fault :

> Device 0 (VID=04e8 and PID=685c) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Android device detected, assigning default bug flags
Error 1: Get Storage information failed.
Error 2: PTP Layer error 02fe: get_handles_recursively(): could not get object handles.
Error 2: (Look this up in ptp.h for an explanation.)
Segmentation fault


Here is the status of my libmtp library files :
> 
lrwxrwxrwx 1 root root   15 2012-01-02 21:15 /usr/lib/libmtp.so.8 -> libmtp.so.9.0.1
-rw-r--r-- 1 root root 1.1M 2011-12-23 00:20 /usr/lib/libmtp.a
-rwxr-xr-x 1 root root  921 2011-12-23 00:20 /usr/lib/libmtp.la
-rwxr-xr-x 1 root root 713K 2011-12-23 00:20 /usr/lib/libmtp.so
-rwxr-xr-x 1 root root 713K 2011-12-23 00:20 /usr/lib/libmtp.so.9
-rwxr-xr-x 1 root root 713K 2011-12-23 00:20 /usr/lib/libmtp.so.9.0.1
-rw-r--r-- 1 root root 288K 2010-09-07 04:18 /usr/lib/libmtp.so.8.3.3


Amarok and vlc are the reason I have that little libmtp.so.8 link. If I formally uninstall libmtp8, then ubuntu also removes amarok and vlc

Any help on how to get gmtp working will be greatly appreciated.
Thanks,

---

### Post by akwatve on 2012-04-15
Update :

I tried manually installing my libmtp as per the suggestion  [here]("http://www.humans-enabled.com/2011/12/how-to-fix-samsung-galaxy-nexus-mtp.html") but it did not work.

---

### Post by OliverW on 2012-06-15
This is still an issue, but doesn't seem to be limited to ubuntu (have a look on google) or 64-bits.

---

