---
title: "Trouble Connecting to HDTV"
date: 2008-05-03
forum: Mythbuntu
---

### Post by mythpeterp on 2008-05-03
I have just got an 8.04 box up and running and the last remaining problem I am having is in getting it to output video via VGA to my HDTV.

I previously had this exact same setup working with a MythTV install on top of FC4 (via MythDora). I have tried just replacing the xorg.conf file with the one from that install with no results. The weird thing is, the splash screen looks fine, its just when XFCE starts up that I have issues. 

I am running an ATI Radeon 8500 LE, attached to a Philips 55PP9352 via DB15. I have attached the xorg.conf that used to work. Any ideas?

---

### Post by wombo on 2008-05-03
I dont think you should have any problems.

I have my Mythbuntu box running into my big LCD screen (LG 42LC2D) via VGA. The box just treats it as a normal monitor.

I did have to change the input mode on the LCD screen for that port.

---

### Post by mythpeterp on 2008-05-03
Yeah, I tried changing from RGB to CmYK, but that didn't help matters.

---

### Post by tgm4883 on 2008-05-03
Did you install the ati configurator from MCC?

Please post the output of xrandr -q from the terminal

---

### Post by mythpeterp on 2008-05-03
"Can't open display"

I don't think I am using the proprietary drivers, so the ATI configurator is not available to me...

---

### Post by tgm4883 on 2008-05-03
> **mythpeterp said:**
> "Can't open display"

I don't think I am using the proprietary drivers, so the ATI configurator is not available to me...

You can't do that when SSH'd in, you have to run xrandr -q from the machine

---

### Post by mythpeterp on 2008-05-05
Gotcha. This is via VNC, since I can't actually see anything from the machine.

Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1680 x 1200
VGA-0 disconnected 1280x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
DVI-0 disconnected (normal left inverted right x axis y axis)
  1280x768 (0x56)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz


Any help?

---

### Post by superm1 on 2008-05-06
That VNC session: it's live on the X server, not a VNC created X server right?

If that's the case, lets see a /var/log/Xorg.0.log to see what it claims.

---

### Post by mythpeterp on 2008-05-06
Attached

---

