---
title: "Sound issues, off and on sound (here is info)"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by berlinbrown on 2007-10-20
My sound is hit or miss, sometimes rebooting works, sometimes it doesnt.  If the sound is on, it will stay on forever.  Which I think is strange.  So far, only rebooting resolves the issue.  Hopefully some of these will help.  I have one pci card, audigy and an onboard sound card which should be disabled.

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

bbrown@houston:~$ amixer
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [-12.00dB] [on]
  Front Right: Playback 23 [74%] [-12.00dB] [on]

bbrown@houston:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


bbrown@houston:~$ tail -2 /proc/asound/oss/sndstat
0: Analog Devices AD1986A
1: mixer10

bbrown@houston:~$ cat /proc/asound/cards
 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfbffc000 irq 22
 1 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xe800 irq 23

bbrown@houston:~$ cat /proc/interrupts
21:      46178   IO-APIC-fasteoi   nvidia
 22:       1390   IO-APIC-fasteoi   HDA Intel
 23:          0   IO-APIC-fasteoi   snd_ca0106

---

### Post by Necreia on 2007-10-25
To colaborate--

I have this EXACT same issue, with the exact same audio card (SB0570) and a disabled on-board.  It's a hit or miss-- if there is no sound, I reboot until there IS sound.

This isn't a problem I had with 7.04, only with 7.10.

---

### Post by berlinbrown on 2007-10-28
This was my fault.  I didn't disable the onboard audio and now it is working fine.

---

