---
title: "Strange sound problem with 8.10 installation"
date: 2008-11-16
forum: Multimedia Software
---

### Post by damnbiker on 2008-11-16
Tried this in the Newb forum and the General help with no luck, so I thought that maybe this was the right forum

Currently I'm running a dual boot, Dual screen set up (XP and Intrepid, LCD monitor and HDMI TV)

I have the dual screen working well with the TV at 1920x1080 but cannot get any sound to come through the television. My onboard sound is Realtek ALC888 which shows up as an option under the sound preferences as

HDA VIA VT82xx ALC888 Digital (ALSA).

Testing gets nothing (TV or front channel jack off the motherboard. If I switch to

ALSA - Advanced Linux Sound Architecture

I get sound from headphones in the front channel jack on the motherboard.

Now the strange part, to make matters worse, since I've installed Ubuntu, my sound under XP isn't working either. I had installed XP first, sound working fine through the television, left some empty space on the hard drive and then installed Ubuntu in the free space on a separate partition. I tried reinstalling the drivers in XP but still have had no luck getting the sound working (after several reboots too). So now I have no sound no matter which OS I am running.

The video card is a Sapphire with the RV530 Pro chip, VGA and HDMI outputs. Not sure if that'd make any difference.

After a bit more reading I tried downloading the GUI ALSA mixer and played with that.  No luck there either.

This is not my first crack at this either.  Last time I experienced this I had to start from scratch by deleting all partitions and installing XP all over again to get any sound through the TV.  I'd prefer not to have to go through that again.

Any thoughts?

---

### Post by damnbiker on 2008-11-17
UPDATE:

After playing with the ALSA mixer GUI program I rebooted into XP and have sound again.  Still no joy with Ubuntu.

---

### Post by psyke83 on 2008-11-17
A very common issue with Intrepid is that the PCM mixer gets muted (possibly a bug in ALSA or the GNOME Volume Control applet). The first thing you should do is check that.

Intrepid uses PulseAudio by default, so you should also focus your troubleshooting efforts there. Look at Appendix A of [this]("http://ubuntuforums.org/showthread.php?t=789578") guide and follow the troubleshooting steps.

N.B: Selecting the "ALSA" output in System/Preferences/Sound is a total red-herring. First of all, that's not a "system-wide" preference; it only affects GStreamer applications (Totem, Rhythmbox). Secondly, choosing ALSA output will continue to remap output to PulseAudio automatically due to the way Intrepid's ALSA libraries are configured. Therefore, focus your attention on PulseAudio.

If XP was really affected (i.e. you weren't overlooking something obvious such as a PCM volume slider being muted, or the physical mute button being pressed on your laptop), it could be a BIOS issue.

---

### Post by damnbiker on 2008-11-17
That's a great help, thanks.  Still having problems though.  When I open the pulse audio control application I only have 

ALSA PCM on front:0(ALC888 Analog) via DMA

as an output device.  I don't see a digital option.  It is set up to show all output devices.

Also, for some reason I cannot launch the application from the Applications/Sound & Video/PulseAudio Device Chooser.  I have to load it through the terminal with "pavucontrol"

---

