---
title: "Big Problem Enabling Video Card"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by Pido on 2008-02-04
I followed the top guide on how to install an ATI card on any stable version of Ubuntu but seem to be getting this problem every time, when I enable the driver as per instructions in the article I read at the top of this forum it asks me to restart my computer.

After I restart thinking my video card will work it get to the loading screen where is says "Ubuntu" then when the bar loads all the way a cursor blinks twice and the screen goes completely blank and remains that way, I cannot Ctrl+Alt F1, or anything to give any input on it. So basically I have to reinstall Ubuntu from the CD to get it working again. Now is there anyway I could get my Video Card to work?

I have a Radeon x1300/1550 Video Card, when on windows I update it using the 1550 driver from their website.

---

### Post by Pido on 2008-02-05
Bump for great justice!

---

### Post by pimpemon on 2008-02-05
I just got a Radeon x1650 and had the same problem. I hope that you can get get into the recovery console at the boot menu because you can revert to the xorg driver with this command: 
sudo dpkg-reconfigure xserver-xorg
i found this at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Pido on 2008-02-08
Bump.

---

### Post by greencookie on 2008-02-12
Bump for same problem for my x1300/1500 card. Running Gutsy on Dell Dimension c521

---

