---
title: "Sandy Bridge HDMI Sound"
date: 2011-05-01
forum: Multimedia Software
---

### Post by lanux on 2011-05-01
Hi,

I have only video signal over HDMI :(
H67 + i3-2100.

```
user@Mbox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
# lspci

00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: ASRock Incorporation Device 3892
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at fe600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```



thx

---

### Post by dawez on 2011-05-13
Same situation here over a H67 board. Video is fine but cannot get any audio out.

The HDMI output is appearing correctly in the output devices.

---

### Post by lidex on 2011-05-14
Which device are you using, 0,3 or 0,7?
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step%2017](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step%2017)

---

### Post by andylinux on 2012-07-04
I had a similar problem with my Mythbuntu 12.04 install.  Sound over hdmi on my sandy bridge worked fine in Mythtv when I picked the "ALSA:plughw:CARD=PCH,DEV=7" in the MythTV audo setup.  

However when if I used firefox to Chrome to play a youtube I did not get any sound.

This would produce sound,
aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav

Next I just created 
this file
more /etc/asound.conf 
pcm.!default {
    type plug slave.pcm {
        type hw card 0 device 7 
    } 

} 

last I rebooted and sound now works.

---

### Post by wildmanne39 on 2012-07-04
Hi, thanks for sharing but this is an old thread so it has been closed.
Thanks

---

