---
title: "What video cards ATI 8.41.7 driver supports ?"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by MaximB on 2007-09-15
The new driver 8.41.7 came out, but I don't know if it will help me much
I have ATI 9800 Pro video card and in the amd site the 8.40.0 driver is still recommended.
it is said that the new driver supports only high end cards and I should keep using the old drivers.

sould I install the new drivers or keep the crappy old ones ?

---

### Post by rbmorse on 2007-09-15
I"m using the new driver on an R580 card (X1950XTX) which is technically not supported, either. but it works very, very well on both Kubuntu Feisty and Ubuntu Gutsy. Followed the instructions in the sticky. 

I've been following the discussions about the new driver on the Phoronix site.  From that traffic, it appears that people with PCI-e cards are having more success than people using AGP cards like your Radeon 9800 Pro, so my advice would be to wait until next month for the 8.42 driver that is supposed to be a unified driver that supports the R300 card family, too. 

But, if you like to play, the installation is not hard, nor is recovery if it doesn't work (boot into recovery mode and then sudo dpkg-reconfigure -xserver-xorg and switch back to the driver you were using before).

---

### Post by w4ett on 2007-09-15
At the moment it looks like SOME X-series cards and above.  See this thread:

[http://ubuntuforums.org/showthread.php?t=549464](http://ubuntuforums.org/showthread.php?t=549464)

---

