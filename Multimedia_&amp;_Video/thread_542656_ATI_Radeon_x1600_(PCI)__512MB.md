---
title: "ATI Radeon x1600 (PCI) / 512MB"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by RWC on 2007-09-04
I have the following Video Card Installed in my computer - in the PCI-Express Slot: 
ATI Radeon x1600 / 512MB

The Computer's integrated video card is the Radeon Xpress 200 / 128MB

The monitor is connected to the x1600 Card - which means that the Xpress 200 is not active - correct?

Is the full power of the 512MB  Radeon Card being utilized by Ubuntu?

If not - do I really need the 512MB Card?

If not - how do I get Ubuntu to fully utilize the 512MB Card without fumbling around with the ATI Proprietary Drivers?

---

### Post by frank95com on 2007-09-04
Are you using the vesa drivers for your x1600?
If you are using the proprietary driver Ubuntu can utilize the full power of the graphic card (but ati drivers suck).
If you are using vesa driver you can't have 3-D accelleration enabled.
I don't know if you can use free xorg-ati drivers with the xpress 200.
You should see at freedesktop.org.

---

### Post by kellemes on 2007-09-04
You need the ATI Proprietary Drivers to get the result you want.. together with XGL.
There are some stickies about fglrx + XGL.

---

### Post by RWC on 2007-09-04
> **kellemes said:**
> You need the ATI Proprietary Drivers to get the result you want.. together with XGL.
There are some stickies about fglrx + XGL.

Thanks for the response - I think I'll take out the card and just stick with the Xpress 200.

---

### Post by RWC on 2007-09-05
'Hold the phone!'

I got the ATI Proprietary Drivers to work!  

....I think.

I used the following guide using Method 2: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

The ATI Catalyst Control Center is installed.

---

