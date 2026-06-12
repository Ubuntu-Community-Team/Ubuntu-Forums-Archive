---
title: "Audio Problem with 9.04"
date: 2009-05-04
forum: Multimedia Software
---

### Post by Anlace on 2009-05-04
Greetings,

The problem is no sound . . . . sort of.

After I boot into KDE I can manually enable sound with System Settings > Multimedia and changing HDA NVidia (ALC1200 Digital) to HDA NVidia (ALC1200 Analog) or visa versa HDA NVidia (ALC1200 Analog) to HDA NVidia (ALC1200 Digital).  Whichever setting is saved as preferred will not work again on reboot but when I manually change the setting in Settings > Multimedia audio then works.

This is onboard high definition audio on a NVidia 780i chipset motherboard using snd-hda-intel as suggested by [http://www.alsa-project.org](http://www.alsa-project.org) for my audio setup.

Some background - This is a clean install of Kubuntu 9.04 64 bit, although I did retain the /home partition without formatting it.  I installed on Friday, May 1 without any apparent problems and the sound worked up until yesterday, May 3.

I followed all of the steps outlined here: Comprehensive Sound Problem Solutions Guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) with the exception of manually compiling and installing the alsa driver.  I have not done an apt-get --purge as suggested because I don't believe it's needed.  I am also concerned that when the purge removes kubuntu-desktop it will mess with my /home partition when it's reinstalled.

Any suggests as to what may be going on?  This one has me stumped.  As always any and all helpful assistance is very much appreciated!

Peace,
Gail

---

### Post by Anlace on 2009-05-04
Well, after fussing with a few things like adding user permissions for pulse-audio now KDE gives me a error message that analog/digital audio cannot be initialized and falls back to the next switching back and forth just like I was doing manually.

I have sound without doing this by hand so I'm ok with this.  Wish I was offering a more comprehensive explanation for how I got this far but . . . .

Seems to be lots of issues with audio and Jaunty.  I'm hanging tight for a bug fix.

---

### Post by gmhawash on 2009-05-13
Have you been able to figure this thing out.  I have the same problem and followed similar steps as you have done.

---

