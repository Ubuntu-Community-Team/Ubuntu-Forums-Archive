---
title: "Karmic seems to have a lot of issues with sound."
date: 2010-03-13
forum: Multimedia Software
---

### Post by kaldor on 2010-03-13
Ever since I upgraded to 9.10 at around Christmas, sound has been getting quite annoying. My girlfriend has Karmic as well, and she is having the same issues as me. It's basic stuff that shouldn't happen in a distro that's as mature as Ubuntu!

Examples: No sound in flash sometimes. Need to manually unmuted it from the sound controls frequently. No keys are pressed.

Java web applets can't play sound when there are other events. For example, on software I use for online courses, I cannot use anything but the Java applet; when I run another app that uses sound (Skype etc) there comes an error in the Java applet. No sound works on the entire system then until I close the java applet. As soon I close the java applet, all the sounds that should have been played before all play *at once* in a big jumble. 

Some Wine programs have no sound at all (games). Period. 

Sound has a load of static on my girlfriend's laptop when she runs an NES emulator.



Overall, my biggest annoyance is that it seems only one application with sound can work at a time. If I am running skype, only skype sounds will be heard; pidgin, flash, java etc will sometimes not make noise until other applications are exited. 

Note: I only have this problem in Ubuntu 9.10 and Linux Mint 8 (8 is based on Karmic). Fedora and previous Ubuntu releases worked fine. Any indications this will be fixed for Lucid? I don't want to downgrade, but I may have no choice.

---

### Post by subedistra7 on 2010-03-13
> **kaldor said:**
> Ever since I upgraded to 9.10 at around Christmas, sound has been getting quite annoying. My girlfriend has Karmic as well, and she is having the same issues as me. It's basic stuff that shouldn't happen in a distro that's as mature as Ubuntu!

Examples: No sound in flash sometimes. Need to manually unmuted it from the sound controls frequently. No keys are pressed.

Java web applets can't play sound when there are other events. For example, on software I use for online courses, I cannot use anything but the Java applet; when I run another app that uses sound (Skype etc) there comes an error in the Java applet. No sound works on the entire system then until I close the java applet. As soon I close the java applet, all the sounds that should have been played before all play *at once* in a big jumble. 

Some Wine programs have no sound at all (games). Period. 

Sound has a load of static on my girlfriend's laptop when she runs an NES emulator.



Overall, my biggest annoyance is that it seems only one application with sound can work at a time. If I am running skype, only skype sounds will be heard; pidgin, flash, java etc will sometimes not make noise until other applications are exited. 

Note: I only have this problem in Ubuntu 9.10 and Linux Mint 8 (8 is based on Karmic). Fedora and previous Ubuntu releases worked fine. Any indications this will be fixed for Lucid? I don't want to downgrade, but I may have no choice.

intel audio?

---

### Post by Yellow Pasque on 2010-03-13
A lot of people seem to have the issue with apps using ALSA directly (Java, Flash) not mixing well with the pulseaudio sound system. Try this: [http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)

Also install libsdl1.2debian-pulseaudio (it will remove libsdl-alsa) and maybe that will help with NES emulator.

---

