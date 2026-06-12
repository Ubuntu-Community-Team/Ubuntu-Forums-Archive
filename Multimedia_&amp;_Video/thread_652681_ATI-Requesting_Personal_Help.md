---
title: "ATI-Requesting Personal Help"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by Neondog82 on 2007-12-29
Hello, I am looking for some personal help on getting my ATI card to work. It is a Radeon X1300. I have currently tried the top sticky, Envy, and this Gusty Gibbon Tutorial [http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748). Nothing seems to work. All that ever happens is when I start Ubuntu it goes into low graphics mode. Recently I did a clean install and tried the Gusty Gibbon Tutorial. When I restarted my computer it went right into low graphics mode. There I told it which driver to use for my on board video. Then when I finally got it, I checked the restricted driver manager...only to see my ATI card was disabled again. It still kept my on board video messed up, so i just replaced t he Xorg.conf file with a backup I made right after the clean install.  Can someone please help me, I can honestly say I have depleted my resources of using tutorials and other post. I would really like to use my ATI card. BTW I am using x64 Ubuntu 7.10

---

### Post by Neondog82 on 2007-12-30
Bump....Will someone please help me?
Bumping

---

### Post by Neondog82 on 2008-01-02
Bump?

---

### Post by Yellow Pasque on 2008-01-03
Ok.. Let's start by making sure you have the restricted repo enabled. Go to System -> Administration -> Software Sources. Make sure the first 4 items are checked on the first tab.

Now, press Ctrl+Alt+F1, login to the terminal and run:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```
Reboot and pray. If that doesn't work, post your xorg.conf(s) (the current one that aticonfig created as well as the one it auto-backed up)

Option 2 to get out of low-graphics mode is to use the radeonhd driver (see the link in my sig). There;s no 3D accel, but at least the 2D support works.

Option 3: "I've had enough of this ATI stuff" Throw down $20 on [this](http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=327718)

---

### Post by Neondog82 on 2008-01-06
Temüjin, 
     I just wanted to thank you buckets. What you told me to do worked awesome. Sorry I did not reply back sooner, but I did not think anyone was going to answer my post. Therefore I was only checking it weekly. Can you explain why what you said to do worked, and why the tutorial i followed didn't, Envy didn't, and straight ubuntu restricted device manager didn't work? Thanks again.

---

### Post by Yellow Pasque on 2008-01-06
Cool, glad it worked. I'm guessing your xorg.conf was in some sort of state that aticonfig/CCCLE didn't recognize/parse properly and required the -f (force) switch to properly set up your X configuration.

If you really want to compare, look at your current /etc/X11/xorg.conf and the one that aticonfig overwrote (in the same directory, I believe it's named xorg.conf.fglrx-0 or xorg.conf.original-0).

---

