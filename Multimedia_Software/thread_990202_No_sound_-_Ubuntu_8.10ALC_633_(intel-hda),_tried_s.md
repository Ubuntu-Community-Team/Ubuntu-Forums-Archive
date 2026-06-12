---
title: "No sound - Ubuntu 8.10/ALC 633 (intel-hda), tried script and tried manual recompile"
date: 2008-11-22
forum: Multimedia Software
---

### Post by lopoetve on 2008-11-22
I'm kinda stumped here.  Hardware is an Asus N80 laptop, with the intel-hda audio (ALC 633). 

Aplay -l lists both the analog and digital outputs for the ALC card, but no sound.  Double checked alsamixer for mute, and it's off for everything.  alsaplayer tries to play, but nothing from the speakers.

Initially tried the script located [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) -.  Script install went fine, no errors in the log, on reboot I get a bunch of system beeps during the kernel init, but it loads into gnome anyway just fine.  No sound, nothing muted, etc.  Ok, maybe it's a patch - I fire up the updater (this is a brand new install) and do all 80 patches.  Reboot, and now it doesn't think I have a sound card.  

Progress!  I can now install them fresh :)  Run the installer script again - reboot, and now it thinks I have a card again, but no joy on sound.  Double check the mute, crank volume, no joy.  

Go to alsa-project.org, download the latest manually.  Follow the instructions at [http://ubuntuforums.org/showthread.php?t=972761](http://ubuntuforums.org/showthread.php?t=972761)

No good - again, it thinks I have a card, and now I've got the hardware beeps at boot (in kernel init), but no sound in gnome or through alsaplayer.  Double check windows - Vista is playing sound just fine on my dual boot.  

I dug through the general troubleshooting thread at the top-
module is loading (modprobe works fine).
No errors in dmesg about snd-hda-intel
alsa-player/etc all think they're outputting sound, but nothing is going on.

I'm stumped :(  Anyone have any ideas?

---

### Post by lopoetve on 2008-11-22
got it.  3stack-dig into modprobe.

---

### Post by danielfortin86 on 2008-11-26
Hi,

I'm also having the same problem with my Asus N80. I'm using the alsa installation that came with Kubuntu 8.10 x64 which is slightly behind the current version. I added 

options snd-hda-intel enable=1 index=0 model=3stack-dig

to /etc/modprobe.d/alsa-base and I get sound now out of the computer speakers. However, when I plug speakers or headphones into the output jack I get nothing. It works fine in Windows Vista. Does anyone have any ideas?

Thanks,

D

---

### Post by lopoetve on 2008-12-17
> **danielfortin86 said:**
> Hi,

I'm also having the same problem with my Asus N80. I'm using the alsa installation that came with Kubuntu 8.10 x64 which is slightly behind the current version. I added 

options snd-hda-intel enable=1 index=0 model=3stack-dig

to /etc/modprobe.d/alsa-base and I get sound now out of the computer speakers. However, when I plug speakers or headphones into the output jack I get nothing. It works fine in Windows Vista. Does anyone have any ideas?

Thanks,

D

I'm still working on that one ;)

---

### Post by nusmuk on 2009-01-16
hello,

look like adding : 
options snd-hda-intel model=g50v position_fix=0 

works for my asus N80vn.
(analogue + digital + speaker)

hope that help.

---

