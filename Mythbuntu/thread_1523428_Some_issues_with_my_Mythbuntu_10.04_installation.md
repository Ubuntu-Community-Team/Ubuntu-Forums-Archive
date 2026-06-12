---
title: "Some issues with my Mythbuntu 10.04 installation"
date: 2010-07-03
forum: Mythbuntu
---

### Post by mpc_mythtv on 2010-07-03
Hi all,

A few day ago, I decided to install Mythbuntu 10.04 on the computer connected to my TV. Things went relatively smoothly, except for the following problems that I hope to solve with your help. I'm totally new to MythTV and to Ubuntu (I've been using Mandriva for eight years, though).

1st problem:

Audio does not work at all (no sound). Here are some details:

mpc@dvr:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

mpc@dvr:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

mpc@dvr:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC662 rev1

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

mpc@dvr:~$ lspci -v
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
        Subsystem: Dell Device 02e1                                                              
        Flags: bus master, fast devsel, latency 0, IRQ 16                                        
        Memory at f7dfc000 (64-bit, non-prefetchable) [size=16K]                                 
        Capabilities: <access denied>                                                            
        Kernel driver in use: HDA Intel                                                          
        Kernel modules: snd-hda-intel

I played with alsamixer (verifying volume levels, muting and unmuting buttons) with no results. I also tried the HDMI audio with the ATI proprietary driver, with no success.

2nd problem:

The remote control of my FusionHDTV7 RT Gold capture card does not work. I read the instructions at [http://www.mythtv.org/wiki/DViCO_FusionHDTV5_RT_Gold#LIRC](http://www.mythtv.org/wiki/DViCO_FusionHDTV5_RT_Gold#LIRC) but I got stuck at the lircd command. Where is this executed?

3rd problem:

I have two installed capture cards: a FusionHDTV7 RT Gold (recognized and configured, works well with MythTV), and a Haupauge HVR-1600 which I'm not able to configure in MythTV. Any idea?

If I find solutions myself, I'll post them here. If someone can help, it would be greatly appreciated.

---

### Post by nickrout on 2010-07-03
> **mpc_mythtv said:**
> Hi all,

A few day ago, I decided to install Mythbuntu 10.04 on the computer connected to my TV. Things went relatively smoothly, except for the following problems that I hope to solve with your help. I'm totally new to MythTV and to Ubuntu (I've been using Mandriva for eight years, though).

1st problem:

Audio does not work at all (no sound). Here are some details:



what audio device have you set in mythtv? try alsa:hdmi

---

### Post by mpc_mythtv on 2010-07-04
> **nickrout said:**
> what audio device have you set in mythtv? try alsa:hdmi

Thanks. That worked. One down, two to go...

---

