---
title: "Several simple questions, all of them having do with video cards."
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by theyain on 2007-06-09
Hi, I am trying to help my friend play Tremulous, but when ever we start it, it loads, but none of the 3d models are there.  I think that it is caused by not having any drivers (not sure if we do or don't have the drivers or if they are enabled) Also  Is there any way to see what kind of Video card my friend has in 6.10 Ubuntu?  And I think that his 3d drivers aren't loaded, because I tried to load the screen savers, but i couldn't see them.  How do I enable them (the drivers)?  I think thats it.

---

### Post by moeFinley on 2007-06-09
What card has he got?  ATI, NVidia, Intel etc.

Type 'lspci' in the terminal for a list of all your hardware.

---

### Post by wererabbit on 2007-06-09
Go to the System menu, to Preferences, to Hardware Information.  Your hardware should be listed there.

---

### Post by theyain on 2007-06-10
But you see, I would of one that.  But he doesn't have 'Hardware Information' in his menu.  Thats why I was asking.

---

### Post by moeFinley on 2007-06-10
Well type 'lspci' into the terminal?

Or if you want the gui and you just can't find it in the menus type 'hal-device-manager' for the normal harware information.

---

