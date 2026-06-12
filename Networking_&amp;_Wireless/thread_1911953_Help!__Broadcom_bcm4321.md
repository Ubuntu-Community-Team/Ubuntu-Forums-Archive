---
title: "Help!  Broadcom bcm4321"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by jpdidthis on 2012-01-19
I recently installed ubuntu 11.10. I tried the original STA drivers that I downloaded and installed. I have a broadcom bcm4321. I recently read in another post some say "bcm4321: some cards do not work in DMA mode (PIO is needed)" Can anyone tell me what this means? Also I have been fighting with this for a couple of days now. My drivers say they are active and working, and I can find my network. I Have connected to, and used this network before and it worked fine. Now when it tries to connect it keeps asking for my password every minute or so. Any ideas on the situation? Thank You

---

### Post by 23senick on 2012-01-19
Try the method on this link: [http://ubuntuforums.org/showthread.php?p=11604412](http://ubuntuforums.org/showthread.php?p=11604412) 

That was different Broadcom wireless but could be same problem?  Ubuntu failing to ignore drivers which don't work?  In which case you need to disable them by blacklisting them.  Good luck

---

### Post by jpdidthis on 2012-01-19
When I try "lshw -C network" the driver=wl0    I'm not sure what that means....

---

### Post by 23senick on 2012-01-19
Looks the same as mine, maybe it isn't the same problem as I had (mine was broadcom 4313). If you go to system/additional drivers, is there a broadcom driver listed, and is it enabled?  Afraid I con only suggest trawling the various forums till you find an answer...

---

### Post by jpdidthis on 2012-01-19
yup, according to the charts made by broadcom I am supposed to use the STA drivers.  They are installed and active.

---

### Post by 23senick on 2012-01-20
Mine were active but I still had the problem until I blacklisted the old drivers (see link mentioned before) but not sure this will help you...sorry

---

