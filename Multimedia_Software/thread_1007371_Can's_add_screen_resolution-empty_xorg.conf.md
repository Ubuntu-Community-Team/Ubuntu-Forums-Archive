---
title: "Can's add screen resolution-empty xorg.conf"
date: 2008-12-10
forum: Multimedia Software
---

### Post by cfwells1 on 2008-12-10
I installed 8.1 on a IBM i1300 laptop.  I cannot get 1024x768 resolution to appear in the screen resolution window, I tried sudo xrandr -s 1024x768"  I get a message that states that resolution is not available. The max res I can get is 800x600
I know the display supports 1024x768(in windows anyway).  That is it native res.  I cannot edit the xorg.conf file beacause it is empty.  Unless I can get the higher resolution Ubuntu is worthless to me. In the displays window my monitor shows as "unknown".   Any ideas?

---

### Post by zika on 2008-12-10
Did You get driver for Your card? System->Administration->Hardware drivers

---

### Post by cfwells1 on 2008-12-10
I shows no  drivers.  It says no proprietary drviers are installed.  I have searched around and apparently generic vga drivers a suitable.

---

### Post by zika on 2008-12-10
If that was my machine and if I did not have valuable data on it I would have tried:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` but I am not sure enough to recommend it to You.

---

### Post by cfwells1 on 2008-12-10
I have already done that.  The xorg.config is essentially still empty.  The device section has "configured video device"
the monitor section has "configured monitor
the screen section has  "default screen" 
so essentially the xorg file is still empty.

---

### Post by cfwells1 on 2008-12-10
I think it has to be the monitor configuration.  In the displays section in shows an unknown monitor.  The proper trident video drivers are installed.

---

### Post by cfwells1 on 2008-12-10
I tried pasting a known good xorg.cong file into the blank xorg.conf file but it will not let me save the file.  I also tried to add modelines but to no avail.  I really need help on this one

---

### Post by zika on 2008-12-11
> **cfwells1 said:**
> I tried pasting a known good xorg.cong file into the blank xorg.conf file but it will not let me save the file.  I also tried to add modelines but to no avail.  I really need help on this one

sorry if You've tried but, did You try that editing command with "sudo" or "sudo su" in front, in order to run it as a root ((s)uper(u)ser)?

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by cfwells1 on 2008-12-11
I was able to copy and save the xorgconfif file.  Did not work.  Just tried suse 11 live cd.  It has a switch for 1024x768 on the opening splash screen.  Have not installed it yet.  I hate to give up on Ubuntu.  Any other ideas

---

