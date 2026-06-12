---
title: "ubuntu 11.10 sane server -&gt; xsane win32 frontend"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by parix on 2012-02-07
The documentation howto
[https://help.ubuntu.com/community/ScanningHowTo#Set_.28x.29inetd](https://help.ubuntu.com/community/ScanningHowTo#Set_.28x.29inetd)
 is almost right, but (x)inetd needs to be configured, even if my version is > 10.04

I found that inetd was installed as default but the file[FONT=Courier New][SIZE=2]**/etc/inetd.conf**[/SIZE][/FONT] was missing and I've needed to create it and put in it the line:
[FONT=Courier New][SIZE=2]**saned stream tcp nowait root /usr/sbin/saned saned**[/SIZE][/FONT]
(where to know the path of your saned you can just use "which saned" in a terminal window, in case it is not /usr/sbin/saned).

---

