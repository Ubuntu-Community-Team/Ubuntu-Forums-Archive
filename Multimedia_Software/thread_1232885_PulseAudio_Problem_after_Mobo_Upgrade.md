---
title: "PulseAudio Problem after Mobo Upgrade"
date: 2009-08-06
forum: Multimedia Software
---

### Post by ScottNZ on 2009-08-06
Hi All,

I'm trying to make my way through the guides and posts here, but I could use some direction. I'm running Jaunty w/2.6.28-14 kernel. I upgraded from an Asus P5KR motherboard to a P5Q Deluxe. Everything was incredibly smooth except for my sound. 

I hear only static when PulseAudio is selected for playback under Sound Preferences and at login. If I select HDA Intel AD198x Analog (OSS) for playback, <Test> is normal. Selecting PulseAudio Sound Server produces static on <Test>. Playback=AutoDetect produces static.

I booted from the LiveCD and got the usual login sound so it must be configuration, but I don't know where to start.

Any suggestions greatly appreciated!
Cheers,
Scott.

---

### Post by markbuntu on 2009-08-06
You should probably reinstall alsa so it can autodetect you new hardware properly


(1) Remove the ALSA packages

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall the same packages

sudo apt-get install linux-sound-base alsa-base alsa-utils

Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:

sudo apt-get install gdm ubuntu-desktop

If you are using xubuntu this will also happen to you

sudo apt-get install gdm xubuntu-desktop

reboot.

---

### Post by ScottNZ on 2009-08-06
Markbuntu--thanks very much. Last night I followed the "[HOWTO: PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578")" tutorial, and that seems to have resolved my issues. I'll try your ALSA instructions if I discover any more problems.

I'm trying to understand the relationship between PA and ALSA; does PA use ALSA or are they independent of one another? More reading this weekend... 

Cheers,
Scott

---

### Post by ScottNZ on 2009-08-06
BTW, I have to mention how absolutely AWESOME it is to upgrade my mobo and have the existing installation of Ubuntu boot with only a minor sound issue.

Windows would have started convulsing with reboots, requiring a full re-installation and twenty minutes on the phone with the MS Client Services to explain my actions and ask permission to re-activate my existing license.

Scott.

---

### Post by markbuntu on 2009-08-07
PA only uses the ALSA hardware drivers.

---

