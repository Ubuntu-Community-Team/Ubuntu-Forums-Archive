---
title: "Sound not working -- install driver?"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by PieSquared on 2007-04-08
After attempting to install Nvidia drivers and then reverting back to nv as the driver, I suddenly found that no sound played, including all startup sounds and whatever. I think that maybe when trying to set up the nvidia drivers through "reconfigure xserver-xorg" or something like that, I somehow messed up the drivers to my sound card?

The sound card that I have is SB Live! EMU10k1 by Creative Labs, according to System -> Administration -> Device Manager.

I am running Ubuntu 6.10. The sound works in Windows XP, which is on the same computer, so I know it isn't a problem with any wiring or hardware.

I am still a newbie to Ubuntu, so I don't know how to fix this, and the Internet tutorials I found didn't explain how to check for drivers.... :( Anys suggestions?

---

### Post by PieSquared on 2007-04-08
Should something significant be in /etc/modules? 

The only stuff in there is

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp



Should the driver for the soundcard be there? (By the way, modprobe soundcore returns normal results)

---

### Post by sgx on 2007-04-08
try the  lsmod     command, and look for emu10k (a sign of a Creative Labs product being noticed) or similar in the list, and assuming you made a separate /home partition, and no sign of 'emu10k'
or similar, a reinstall is easy, if no separate partition, you can always copy the .folders in your /home/user folder to a ceedee, and restore them after a new install...and install alsaoss and alsamixergui, and search in the gui for volumes turned down...good luck!

---

### Post by PieSquared on 2007-04-08
It finds the card, and it used to work before. However, I would rather try to fix it instead of reinstalling  Linux completely. Any other suggestions? Maybe somehow use reconfigure xserver-xorg, since that is how I managed to screw it up?

 Thanks for the effort though!

---

### Post by PieSquared on 2007-04-09
I looked at the "[Comprehensive Sound Problems Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")" post, but it didn't help. 

aplay -l outputs a lot of data about the card, so I suppose that means it is being detected. 

I added "snd-emu10k1" to /etc/modules, since that is the driver for my sound card; however, that did not help either. 

I tried following the steps in the "Getting the ALSA drivers from a *fresh* kernel" section, however, that yielded no results. According to that post, the only possible problem is with alsamixer and the volume levels. However, I have enabled everything at maximum volume and have been playing around with that for some time now...

Can someone *please* help me?

---

### Post by PieSquared on 2007-04-09
They were right... :oops: :oops: 

All I had to do was make the "Line LineDrive" thing louder in alsamixer.... Though I have no idea what "LineDrive" or any of that is...

---

