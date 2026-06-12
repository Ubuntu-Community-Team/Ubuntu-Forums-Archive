---
title: "Installing nvidia drivers on Feisty 64: What process should I use?"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by MrSparkles on 2007-04-09
I have an on-board nvidia chipset.  I believe the model is GeForce 6150LE (the motherboard is an Asus M2NBP-VM CSM).

The output from lspci -n | grep 0300 is:

```
00:05.0 0300: 10de:0245 (rev a2)
```

The output from lspci | grep VGA is: 

```
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)

```

I've reinstalling Feisty to get a clean start.  

Can anyone recommend the proper drivers and/or process?  I've done lots of searching but there seems to be problems with the nvidia drivers in Feisty.

Any help would be greatly appreciated!

---

### Post by Spr0k3t on 2007-04-09
I used the restricted drivers manager to handle the install.  I had to cobble a known bug with gnome-terminal, but I got everything working.

---

### Post by MrSparkles on 2007-04-09
From what I found, the restricted drivers are hit and miss.  You seem to be one of the lucky/smart ones.

Shortly after posting, I found [this thread]("http://ubuntuforums.org/showthread.php?t=402301").  The process worked perfectly.

I've just made the move from Mandriva to (K)ubuntu and I'm wondering what took me so long.

Viva Ubuntu!

Sparkles

---

### Post by Spr0k3t on 2007-04-09
Yeah, I've heard the stories about restricted drivers manager being a bit of a pain for some.  So far, I've not had one problem yet with it.  The system I built uses nothing but reference parts with the exception of the wireless card.  Also, I used the daily beta build alternate install method from two days ago, I think that may have something to do with it.

Welcome to the world of Ubuntu BTW.

---

