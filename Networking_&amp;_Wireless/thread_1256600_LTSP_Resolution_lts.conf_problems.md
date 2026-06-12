---
title: "LTSP Resolution lts.conf problems"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by tentwelveeight on 2009-09-02
For anyone having problems with different resolutions on different monitors in an LTSP setup the solution I found was to put:
```
XRANDR_DISABLE = True
```
in my lts.conf
This disables xrandr trying to auto detect the monitor and video card settings which solved my problem for me. You can read more about my specific issue here:
[http://hartmansblog.blogspot.com/2009/09/resolution-issues-in-ltsp.html]("http://hartmansblog.blogspot.com/2009/09/resolution-issues-in-ltsp.html")

Cheers! -joe

---

