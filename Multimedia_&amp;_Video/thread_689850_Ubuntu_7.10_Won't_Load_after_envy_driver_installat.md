---
title: "Ubuntu 7.10 Won't Load after envy driver installation."
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by Ryan Karerurenn on 2008-02-06
Alright, I'm a complete newbie when it comes to linux.  In fact, this is the first system I attempted to install linux on.  That being said, I downloaded Envy and had it install the appropriate nvidia driver for my laptop (Geforce 8600M GT) and it prompted a restart.

Ok, fine, I allowed it the privilege of restarting.  It boots up.  Whilst rebooting, some error codes (unable to load this, yadda yadda yadda) are flashed for a split second.

Where the log-in screen would usually be, it shows a blue-ish tinted staticy color.  Slowly, this turns into solid white with a thick black bar protruding vertically offcenter.

Wtf.

Any ideas?  I'm obviously dualbooting, so I can fetch any files needed to help!

And god knows I need it.  Help!

---

### Post by sanddgroper on 2008-02-08
You probably need to boot in safemode into a terminal and go
to /etc/X11 and look for your xorg.conf file.Open it with your linux
editor of choice and under section "device" change "nvidia" to "nv"
and try to reboot.If you are new to linux I will try and walk you through it.

Cheers
Sandy

---

