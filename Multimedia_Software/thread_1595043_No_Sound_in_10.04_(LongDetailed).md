---
title: "No Sound in 10.04 (Long/Detailed)"
date: 2010-10-12
forum: Multimedia Software
---

### Post by musendrophilus on 2010-10-12
Bear with me. I've been futzing with sound since last week. I've tried everything.

I am dual booting 9.04 and 10.04 on the same Alienware laptop. Before the dual install I tried 10.04 as a live CD and saw no sound. I run alsamixer, everything's unmuted and cranked to 100%. I made sure the user is able to use audio under user groups/permissions. Nothing is muted under Sound Preferences. The sound works five minutes before when I'm in 9.04 but when I reboot into 10.04 the sound mysteriously becomes frustratingly unavailable. Under Lucid Lynx I have something about Dummy Output and there's nothing listed under the hardware tab even though the following commands show otherwise.

I've run this script:
[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)
I've tried this remedy:
[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)
I tried this .deb to no avail
[http://people.canonical.com/~diwic/temp/alsa-hda-realtek-ignore-sku-dkms_1.0.23.diwic_all.deb](http://people.canonical.com/~diwic/temp/alsa-hda-realtek-ignore-sku-dkms_1.0.23.diwic_all.deb)
I've purged pulseaudio from my system and rebooted and the box is still mute.

When I do aplay -l under Lucid Lynx I get:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
```
When I do aplay -l under Jaunty Jackalope I get:
```
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
[COLOR=#550055]  Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
```
[/COLOR]I checked lshw
```
sudo lshw -c sound
 *-multimedia
      description: Audio device
      product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition
Audio Controller
      vendor: Intel Corporation
      physical id: 1b
      bus info: pci@0000:00:1b.0
      version: 03
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list
      configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```
I tried the Gnome device manager but it only tells me which is which and under that I get:
Alsa Capture
Sound Card: HDA Intel
Sound Device: Si3054 Modem
Device File: /dev/snd/pcmC0D6c
Alsa Playback
Sound Card: HDA Intel
Sound Device: Si3054 Modem
Device File: /dev/snd/pcmC0D6c

How do I point Lucid Lynx/Alsa/pulseaudio at my RealTek ALC880 and let it know that's  the correct sound device to use not the modem?  What conf file do I tinker with  and what syntax do I use for the task?

---

