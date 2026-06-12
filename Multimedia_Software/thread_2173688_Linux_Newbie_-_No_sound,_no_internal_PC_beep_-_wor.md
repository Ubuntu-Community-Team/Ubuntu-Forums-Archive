---
title: "Linux Newbie - No sound, no internal PC beep - worked before"
date: 2013-09-10
forum: Multimedia Software
---

### Post by the_dude2 on 2013-09-10
Hi everyone,

I'm very new to Ubuntu and Linux and am willing to learn.  I installed Ubuntu 13.04 32 bit on my old Lenovo T60 laptop fairly recently.  It worked fine until suddenly when I woke the computer from standby one day it wouldn't play any sound.  There is no PC beep when I turn the computer on or off anymore either.  I can't even get the sound to work when I boot into Windows XP.

 I checked all the volume controls, searched the forums, ran some terminal mixer app (I forget the command), but still nothing.  The volume is turned up on everything I can find.  Anybody have any ideas?  

Thanks in advance!

---

### Post by zombienerd1 on 2013-09-11
If the sound is not working in Linux, Windows, or even the system power-on beep, you most likely have a failure in the audio hardware (either the audio chip or speakers).  This is not a problem with Linux itself if the problem is in Windows as well.

Have you tried headphones?  If they work, it is most likely your speaker is dead or has come disconnected.

If headphones do not work, check your BIOS settings to disable the audio card, save bios settings, reboot, shut down/restart, re-enter BIOS, then re-enable, save, reboot, shut down and restart.
 
If your computer has a hardware volume knob (some Thinkpads had a volume wheel near the headphone port), try moving it from low to high as well; if it is software based with keyboard controls (Fn+F1-12/up/down) try using those while the system is booting before it hands volume control over to the OS, your hardware could be muted by the card itself.

Best of luck.

---

### Post by the_dude2 on 2013-09-12
Oh wow, I was SURE I had tried the dedicated volume buttons already!  They turned out to be the key, and now do I feel dumb.  I just got this old computer from a friend and don't know all the ins and outs yet.  The computers I have used in the past have had physical volume buttons tied to the OS volume control, so when I pushed the buttons once or twice with no result, I figured they didn't do anything.  Apparently they're tied to the speakers only.

Well thanks for the help!  If it weren't for your suggestions I probably wouldn't have started pushing buttons.

---

