---
title: "driver for intel 815e onbard video card"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by ofir on 2006-06-23
No much to add i search the net for driver to this card and found none,
hope you can help me because i become blind after work with 60mhz](*,)

---

### Post by Fass on 2006-06-23
The driver for i815 is the "i810" driver that comes with Xorg. So, edit your /etc/X11/xorg.conf and make the driver line in the device section read:

```
Section "Device"
    Driver "i810"
```

---

### Post by nilou on 2006-06-23
Hi,
I'm also here searching for a driver for the i815... and the driver must supprot 1280 * 1024.  The current driver does obviosly not support this mode.  If I try, my monitor delivers thin vertical lines equally spaced across the display.  Every thing works fine, but the distortion is very annoying.  I have been searching through a great many places to find nothing but similar discriptions of driver failure.  The only solution I have seen til now, is to lover the colordepth from 24 to 16... but when you do so, the result is only that you cannot invoke the high resolution, and the screen display defaults to 1024*768.  Does anyone know when there will be a driver to test, then I will be happy to volunteer... ;o)
Kind regards
Michael Nilou

---

### Post by ITTechGuy on 2008-01-30
I am having the exact same problem on a machine I received recently.  Can anyone help now that I have resurrected this?  I cannot get it to work right even with the xorg reading as earlier stated. I am using the i815.

---

### Post by Yellow Pasque on 2008-01-30
Let's look at your /etc/X11/xorg.conf file as well as the /var/log/Xorg.0.log file after you try and start with the i810 driver.

---

### Post by Whiffle on 2008-01-30
Actually, in Gutsy the driver is "intel."  Apparently its new and improved.  Previous releases used the i810.

---

