---
title: "System Sound"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by Olly1234 on 2006-10-10
Hey all, I just installed a SB Live! Soundcard to my computer, and it works great! But when I try to mute the system volume, it doest mute I think this might have something to do with my onboard sound card but cant figure it out Thanks.

---

### Post by Olly1234 on 2006-10-10
Any ideas???? Thanks!!!

---

### Post by wererabbit on 2006-10-10
Hey, 
You need to make sure in your Bios that you've turned off the onboard soundcard that's embedded in your motherboard. Once that's  done you should be able to control your sound properly.
-w-

---

### Post by Olly1234 on 2006-10-10
Thanks, but how is that done?

---

### Post by wererabbit on 2006-10-10
The Bios is the chip in the computer that knows who it is, why it is, what it is, how it is and what time it is.

When you boot up your computer it will show a black screen with white letters reading out onscreen.  On a home-built pc it will usually prompt for the Delete key to be pressed if you want to enter the Bios.  On Dell boxes, it's usually "F2 to enter Setup".  Just make sure you hit it quickly before the prompt goes away.

Now once you are inside the Bios, you'll know because it has usually got a Blue or Grey or Black background with the word "BIOS" up at the top.  There will be a variety of menu settings for your system and under one of the menus (probably PCI Devices or Advanced Settings) you'll see something along the lines of "Onboard Sound = On".  You'll need to change that to "Off" and it will turn off the motherboard's soundcard.

Finally, when you're done, you just go back to the Main Menu of the Bios, and select Save & Exit or Exit and then it may prompt to Save and you'll say Yes.  (If you don't save, then your changes will be lost and you'll have to do this all over again.  This can be good if you really screwed something up in the process and you just want to start over without saving.  Just don't save if you screwed something up! ) :) No pressure.  If you find that you really hosed the system, there is almost always a "Default Settings" option which resets the Bios back to original manufacturer settings.

After you've left the Bios, your system will reboot itself and boot into Ubuntu. 
Then you can trouble shoot from there and see if it made any difference.  :) Good Luck!
-w-

---

