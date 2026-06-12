---
title: "Configuring XOrg  Help!!"
date: 2008-08-17
forum: Multimedia Software
---

### Post by lynwode on 2008-08-17
Hi,
After having a torrid time with a faile Hardy upgrade I have had to start from scratch. All is running well apart from my screen resolution. I can only get a max of 800x640 (in Feisty I had 1440x900 or there abouts. 
I have tried running  dpkg-reconfigure xserver-xorg several times but there is no options regarding the video settings. I remember when I set up Feisty there were quite a few pages of settings to configure. 

I have manually edited xorg.conf and added some settings for the screen and monitor (as there were none at all)but these only slightly improved matters to 1024x768.

I am running AMD46 2.6Ghz @GB RAM and an ancient Diamond Stealth video card.

I'm guessing I don't have something installed. 
Anyone got anyideas.

---

### Post by ajgreeny on 2008-08-17
If there are no restricted drivers available for your card, see what you can do in ```
gksudo displayconfig-gtk
```which opens the Screens and Display configuration window.  That may give you a clue also to the driver you are currently using, and perhaps need to update or install an alternative.

If that gets you nowhere, as a last resort try booting in recovery mode and choosing xfix when the menu appears.  That should go through the detection routine like a clean install, and may give you the proper resolution you need

---

