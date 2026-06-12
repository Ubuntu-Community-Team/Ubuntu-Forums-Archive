---
title: "I810: No Valid Modes Found"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by Harin on 2007-04-14
I've been having a lot of trouble getting my install (of edgy) to work, but every step of the way I've found out that the problem is actually something else. Right after the loading screen, my screen goes all scrambled. Right now the problem appears to be in the i810 drivers. 

lspci returns this: 

Host Bridge: Intel corporation 82810 GMCH (rev 03)
VGA compatible controller: Intel corporation 82810 CGC

The drivers I currently configured (through recovery mode) using the dpkg-reconfigure xserver-xorg command were the i810 drivers. But they still don't work. It honestly looks like a refresh rate problem, but I changed the refresh rate in xorg to match the monitor's specific specs. I'm really tired and frustrated, any help will be so very very appreciated. Is there a way I can get it to autodetect the appropriate video card drivers? 

If I try to run the start x command from recovery mode I get these errors:

(ee) I810(0): No Valid Modes found
(ee) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by heimo on 2007-04-14
Could you give us model of your monitor and relevant parts from xorg.conf (monitor, device, screen sections)?

---

