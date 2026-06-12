---
title: "ALSA 'working' still no sound"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by Chachee on 2006-12-23
Well.. apparently enabling everything, and then un-enabling it fixed it.  Is there some log I can check to see what might have changed?

Thanks everyone for your patience.

JT



Hi all,
  Before I get into it - 

Dapper Drake 6.06 LTS currently updated
Sound Blaster Audigy 2 ZS
Creative 5.1 surround sound speakers

  My system was doing find till I decided to set some power saving options and it went to hibernate.  Now I don't get any sounds.  I checked in the Volume Control and everything was muted... unmuted.  No sound.  Restarted. see ALSA loads, hear speakers pop, check and see volume settings are good, still no sound.

  I went through the Comprhensive Sound Guide and have the following output - 

> jeremy@Main:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> jeremy@Main:~$ lspci -v
***cut***
0000:00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at e000 [size=64]
        Capabilities: <available only to root>
***cut***

> ALSA Site - 
Sound Blaster Audigy2 ZS Value  	CA0108  	Details (emu10k1)  	 [ANio] [MIDIio] (1) (3)
No 96khz 24Bit support.

> jeremy@Main:~$ sudo modprobe snd-
***cut***
snd-emu10k1
***cut***

> jeremy@Main:~$ sudo cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
snd-emu10k1

I dual boot so I know all the connections are good since I get sound in Windows.  Also I have loaded amaroK as my music player and have installed the restricted drivers for mp3s and the like.

Again, this was working up to about 2 hours ago.  The only thing I changed in that time was trying to format a USB hard drive with GParted (installed w/ Synaptic) that failed.  And the power saving options, which I've since turned off.

I really need help, this was why I quit fedora to come here.

Thank you,

Jeremy

---

### Post by Chachee on 2006-12-23
Just went through the sound mixer and added all the options to my volume menu.  Turned them all up and unmuted all.  Still nothing.

However, now when I roll over the speaker it says 'HD SPDIF Front'.  I'm using 3 jacks out the back of my sound card for my speakers.  Shouldn't I be using something else for main out?

Still no sound in Ubuntu as of 6 hours ago.  Windows works fine.

JT

---

### Post by tommie74 on 2007-06-17
I´ve had the same problem, no sound after waking from hibernate, and found a solution in launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

The problem seems to be related to a change in the kernel. An updated kernel is available for download:

[http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb)

install using package manager or 

```
dpkg -i /home/***your user name***/Desktop/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb
```

hope this works for you too, as it did for many others,
Thomas.

---

