---
title: "zotac 9300-itx hdmi audio troubles"
date: 2009-09-26
forum: Multimedia Software
---

### Post by sidewinder27 on 2009-09-26
Apologies for another hdmi audio thread; I've tried all the walkthroughs I can find, but after several hours still can't seem to get anywhere.  I'm hoping that I'm close, and that this will be a simple fix.

**Here's what I've done:**
Fresh install of ubuntu-desktop 9.04 x64
Installed nVidia restricted drivers (180.44) (at this point no hdmi audio)
Ran the ALSA upgrade script
Unmuted all channels in alsamixer
Tried all outputs in gnome-sound-properties to no avail
I added the line 'options snd-hda-intel model=6stack-dig' to /etc/modeprobe.d/alsa-base-conf

After all of this, i cannot seem to get the sound properties panel to produce sound or the command $speaker-test -Dplughw:0,3 -c6
speaker-test appears to be running correctly, and I have plugged in an optical line directly to my speakers (at which point i hear sound from left and right, but not center, sub, backleft backright).  So it seems the digital audio is only going out the opitical/spdif channel but not HDMI.


**Here's some important stuff:**

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$lspci -v
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: PC Partner Limited Device 437b
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Sep 26 2009 for kernel 2.6.28-15-generic (SMP).

ALSA info at: [http://www.alsa-project.org/db/?f=96703fcdcfd875d13a95e8cfd34bd940df552b88]("http://http://www.alsa-project.org/db/?f=96703fcdcfd875d13a95e8cfd34bd940df552b88")

**Thanks in advance for the help :)**

---

### Post by sidewinder27 on 2009-09-27
just tried reformatting, and updating to the nvidia 185. drivers, alsa upgrade.  no luck :(
any thoughts before i switch to windows?

---

### Post by disastraus on 2009-10-10
How did you go?

I was thinking of getting this board and installing ubuntu as a HTPC.  I'm guessing you wouldn't recommend it after your experience?

---

### Post by tmclaugh on 2009-10-10
Going through other threads I have read two things that may work.

One is doing an NDIS wrapper on the XP drivers 

Another is installing XBMC Mythbuntu and unmuting this and that. 

I don't have the exact links but there is a thread running over avsforum.  Unfortunately I don't have the time to try either of these out in the near future.

---

### Post by sidewinder27 on 2009-10-14
I went with windows xp x64.  almost no drivers installed automatically and this is a sp3 version.  with no cd drive, had to copy cd drivers to usb thumb drive to get lan card working.  once that was installed, was able to update everything just fine.

still not having great luck with the audio via hdmi.  even with installation cd drivers, sometimes the audio disappears in windows after not using computer for a while.  rebooting does not fix, have not found a consistent solution.  tonight, starting up vlc magically made the audio reappear.  

super strange problem, haven't had time to debug it yet.

---

### Post by sidewinder27 on 2009-10-14
have tried unmuting everything.  i spent my fair time in and upgrading alsa even with various nvidia drivers.  had no luck on this whatsoever.

did not try doing the NDIS wrapper thing, lost focus after 5 days trying to configure alsa and what not

---

### Post by tmclaugh on 2009-11-09
Can someone point me to a walkthrough for doing the NDIS wrapper option.  The only refrences I can find are for Wireless.

---

### Post by ov3rcl0ck on 2009-11-09
> **tmclaugh said:**
> Can someone point me to a walkthrough for doing the NDIS wrapper option.  The only refrences I can find are for Wireless.
 

Probably because its only for wireless bud. You're gonna have to look into ALSA and OSS.

---

### Post by ov3rcl0ck on 2009-11-09
> **tmclaugh said:**
> Can someone point me to a walkthrough for doing the NDIS wrapper option.  The only refrences I can find are for Wireless.
 

Probably because its only for wireless bud. You're gonna have to look into ALSA and OSS.

BTW, the former post, ignore it.

---

