---
title: "Change of monitor"
date: 2005-11-04
forum: Multimedia &amp; Video
---

### Post by steverippl on 2005-11-04
I've just gone from a 15'' to a 19'' monitor and I want to increase the resolution accordingly, but all the options I've found only allow me to go lower. I can't increase the max screen resolution from the setting for the 15'' one. How do I get breezy to "re-install" it's monitor settings...

---

### Post by GTvulse on 2005-11-04
Boot up into ubuntu using single-user mode (a.k.a "recovery mode"). You will be left in a console as root. Type at the prompt:
```
dpkg-reconfigure xserver-xorg
```
and follow the instructions... When you are finished, namely, the xserver has been reconfigured, type
```
exit
```
and allow the bootup process to continue normally. If everything went OK, you should have X running at the maximum resolution for your 19" monitor.

---

### Post by steverippl on 2005-11-04
Many thanks... got a bit messed up trying this for a while but once I ran 

sudo dpkg-reconfigure -phigh xserver-xorg

(taken from xorg.conf file) it all seemed to work again with the higher resolution.  Don't know what I did but thanks for steering me in the right direction!

---

