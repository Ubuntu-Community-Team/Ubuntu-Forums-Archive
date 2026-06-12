---
title: "GRUB Prompt After Upgrading to 10.10"
date: 2010-08-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bluefoxox on 2010-08-14
Hey all, I just upgraded from 10.04 to 10.10 Alpha 3.  When I rebooted and selected Ubuntu it went directly to the GRUB Prompt.  It might also be important to let you know I used Wubi 10.04 to install 10.04 as well (but probably not).  Any help is greatly appreciated, in the mean time I will be reporting the bug.  Thanks  :^D

---

### Post by ranch hand on 2010-08-14
Are you saying this is a wubi installation?  If so this is very important.

I ask just to help someone that knows about wubi.  I have trouble using it as I do not have an MS OS installed.

---

### Post by bluefoxox on 2010-08-14
> **ranch hand said:**
> Are you saying this is a wubi installation?  If so this is very important.

I ask just to help someone that knows about wubi.  I have trouble using it as I do not have an MS OS installed.


I originally installed Ubuntu 10.04 using Wubi 10.04, then upgraded to 10.10 Alpha 3 by pressing Alt + F2 then entering update-manager -d and going through the upgrade steps there.  When it was all done, and I attempted to log into Ubuntu it went straight to the Grub Prompt.

---

### Post by bcbc on 2010-08-14
> **bluefoxox said:**
> I originally installed Ubuntu 10.04 using Wubi 10.04, then upgraded to 10.10 Alpha 3 by pressing Alt + F2 then entering update-manager -d and going through the upgrade steps there.  When it was all done, and I attempted to log into Ubuntu it went straight to the Grub Prompt.

try the following from the grub prompt (replacing X and Y with the partition you installed wubi on):
```
configfile (hdX,msdosY)/ubuntu/winboot/wubildr.cfg
```

E.g. if you installed on /dev/sda1, use (hd0,msdos1)

I did a fresh install of wubi from alpha3 and that's what I needed to do to complete the install, as well as all subsequent boots. Couldn't find a fix for that.

---

### Post by bluefoxox on 2010-08-19
I got it installed.  You are not going to believe what it appears to have been.  update-grub2 was not run after install automatically, so after 2 fails I tried running it on a hunch, and it appears I was right.  If that is what the problem was, it is mildly ridiculous.

---

