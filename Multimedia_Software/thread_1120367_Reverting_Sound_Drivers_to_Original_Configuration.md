---
title: "Reverting Sound Drivers to Original Configuration"
date: 2009-04-08
forum: Multimedia Software
---

### Post by Anaithnid on 2009-04-08
This is my first time using the forums and I apologize if this is the wrong place.  I know it can a pain for the moderators to sort and shift all this stuff around.  My sound drivers upon install worked perfectly, everything was up and running without any tinkering.  I was trying to do some recording and couldn't find my Mix channel so I noticed the default drivers were not specific to my exact card.  I downloaded the specific driver and installed it... that didn't work and I couldn't get any of it working again.  I did a fresh install of Ubuntu 8.1 and everything is fine again. Is there an option to restore install defaults for sound like there is for fixing your graphics settings by setting your xconfig back to default?  I searched everywhere even purged everything ALSA related on the comp but couldn't get any new or old drivers to work with my card again.

---

### Post by markbuntu on 2009-04-09
Did you do

sudo apt-get purge remove linux-sound-base alsa-base alsa-utils

Because that is about the only way to remove all the alsa files and their configs. Then you just reinstall the same packages

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:

sudo apt-get install gdm ubuntu-desktop

If you are using xubuntu this will also happen to you

sudo apt-get install gdm xubuntu-desktop

Then you need to reboot but it beats having to reinstall just because you messed up your sound.

If you are having problems with your driver or anything else soundwise go here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Anaithnid on 2009-04-09
Thank you for the reply, I tried that method first but it still did not restore the original configuration.  For some reason ALSA never really totally repaired.  I suppose it may have been the way I installed the new drivers, I have read getting HDA intel cards to work right can be rough so I am happy it worked fine from the get go. I shouldn't have messed with it I suppose.

---

