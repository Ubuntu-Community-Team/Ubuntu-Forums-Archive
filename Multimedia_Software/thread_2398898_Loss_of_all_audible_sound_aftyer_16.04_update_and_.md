---
title: "Loss of all audible sound aftyer 16.04 update and upgrade to 18.04 did not fix"
date: 2018-08-18
forum: Multimedia Software
---

### Post by tunesdoode on 2018-08-18
Aug 19 15:05:58 cirrus pulseaudio[1469]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 19 15:05:58 cirrus pulseaudio[1469]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.



Aug 19 15:06:21 cirrus pulseaudio[1724]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Aug 19 15:06:22 cirrus pulseaudio[1724]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.

Aug 19 15:06:22 cirrus pulseaudio[1730]: [pulseaudio] pid.c: Daemon already running.

Aug 19 15:06:27 cirrus indicator-sound[1826]: volume-control-pulse.vala:744: Unable to connect to dbus server at 'unix:path=/run/user/1000/pulse/dbus-socket': Could not connect: No such file or directory





*************************************************
Originally I did a clean install of ubuntustudio 16.04LTS 32 bit on this machine and all was well with the sound/audio functioning.
It was playing a random playlist on repeat 24/7 as room background music. Following an auto-update the sound quit going to speakers/headphones but any program playing audio showed as it working fine in the VU meters. It was just feeding a dummy output and hence no log errors.
A check of alsamixer in a terminal window to see if muting was a problem ; it wasn't but all adjustments were missing except for PCM and BEEP.
alsamixer always opens with default sound card selected F6 allows change but both show the same PCM & BEEP only when F5 is selected.

Unable to find a fix I did an OS upgrade to ubuntustudio 18.04LTS in the hopes it would correct a missing file or config but it did not. Whatever occured in that 16.04 update seems to have been deemed as nothing wrong with system and upgrade to 18.04 did not correct whatever was missing. I boot the machine into Windows XP and/or a different flavor of linux on a thumb USB drive and audio works normally but ubuntustudio does not. Sadly it also occurred on a second ubuntustudio machine I have but have not upgraded to 18 yet.

Any help would be appreciated.

workstation                      
    description: Desktop Computer
    product: T5016
    vendor: EMACHINES
    serial: XIA59 800 02268
    width: 32 bits           3GB RAM    1ea 300GB HD 1ea 500GB HD

root@workstation:/home/userID# uname -a
Linux workstation 4.15.0-32-lowlatency #35-Ubuntu SMP PREEMPT Fri Aug 10 19:00:03 UTC 2018 i686 i686 i686 GNU/Linux
root@workstation:/# cat /proc/version
Linux version 4.15.0-32-lowlatency (buildd@lgw01-amd64-037) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #35-Ubuntu SMP PREEMPT Fri Aug 10 19:00:03 UTC 2018

root@workstation:/# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic


AUDIO related info:
alsamixer in terminal windows shows
 Card: HDA Intel   Chip: Realtek ALC880  and only PCM and BEEP at full volume no master ar any other function to chk if muted?
on open alsamixer always opens with default sound card selected F6 allows change but both show the same PCM & BEEP only when F5 is selected.





root@workstation:/home/userID# aplay -l
**** List of PLAYBACK Hardware Devices ****

root@workstation:/# arecord -l
**** List of CAPTURE Hardware Devices ****

root@workstation:/# arecord -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
equal
surround21:CARD=Intel
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Intel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
 



root@workstation:/home/userID# aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
equal
surround21:CARD=Intel
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Intel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
root@workstation:/home/userID# 

lshw  (audio devices )

        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:24 memory:b01c0000-b01c3fff

---

### Post by tunesdoode on 2018-08-23
Unable after two days of google suggestions and forums tips to solve the problem; Tried installing a fresh clean install of Mint 19 32 bit and it had similar results no sound although aplay -l did indicate a device detected; however Mint did not work to play sounds either. audio config tab showed dummy out put still. It appears that the debian based linux flavors for 32 bit machine does not detect and configure the intel ALC880 onboard card. It works OK with windows OS on dual boot so hardware is OK. I tried a Mackie FX8 USB audio mixer sound card and it worked immediately automatically; also a Texas Instruments ezDSP USB sound device was also immediately automatically correctly detected and configure. Both the TI & Mackie devices worked well. I have wasted enough time on this matter. and THANK YOU VERY MUCH FOR ALL YOUR SUGGESTIONS. 

I have been a linux convert for many years but the latest updated releases that seem to screw up printer configurations and sound operations make it difficult to suggest linux as a good choice for others. It is indeed surprising that a version advertised as an audio/video production custom version like ubuntustudio would give a user this kind of bad experience.

---

### Post by nik.charles on 2018-08-25
Interesting that you get response in aplay -L but not aplay -l that only

Have you disabled fast start and turned off hibernation on windows?

It is possible that shutdown from windows can put sound card into a hibernation power state

---

