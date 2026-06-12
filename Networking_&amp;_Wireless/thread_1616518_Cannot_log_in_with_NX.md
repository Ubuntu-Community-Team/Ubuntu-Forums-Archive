---
title: "Cannot log in with NX"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by venik212 on 2010-11-08
When I try to log in remotely to my Ubuntu 10.10 (54 bit) machine using NX, I get an error about bad server configuration.
The /var/log/messages error says:
*"Nov  8 10:39:18 udi-desktop-64 NXSERVER-3.4.0-14[5359]: ERROR: (exception id 4EAD8A0A) eval {...} called at nxserver.pl line 4452"*
I did not change anything, but after I started getting this error, I updated the client, server and node parts of NX to the latest versions using the .deb packages that Nomachine provides.
Any ideas?

==============================

SOLVED: my .Xauthority file was corrupted.  I deleted it and rebooted, and all is well.

---

### Post by stealthdave on 2012-02-19
The same thing was happening to me in Xubuntu 11.10, and the solution listed here worked.  Took an hour of Googling to find it!  The error message from NX Client was:

```
Server configuration error. Cannot log in.
```

Hopefully this will give this thread some more SEO juice and the next schmuck to have this problem will only have to Google for *half* an hour! ;)

- Dave

---

