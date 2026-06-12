---
title: "Sound has vanished after a 9.10 update"
date: 2009-12-27
forum: Multimedia Software
---

### Post by bbbaldie on 2009-12-27
Suddenly, no sound.

I read the comprehensive guide. Here are some results of commands:
```

rone@rone-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
rone@rone-ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

I also purged my alsa install and reinstalled, per instructions. I also reinstalled gdm and ubuntu-desktop for good measure.

lspci -v shows this audio device:

```
03:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 17
	I/O ports at de00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci
```

I've never had problems with sound before, through my initial install of 8.04 up until now. IMHO, the fact that alsamixer won't load is significant.

Help, anyone? System/Preferences/Sound Preferences shows that all is normal, unmuted, and should be working.

Oh, and I DID check the connector! I'm an old networker, always check the physical layer first ;-)

Here's more return, from alsactl init:

rone@rone-ubuntu:~$ alsactl init
Unknown hardware: "CMI8738-MC6" "CMedia PCI" "" "0x13f6" "0x0111"
Hardware is initialized using a guess method
/usr/share/alsa/init/default:51: control element not found
/usr/share/alsa/init/default:52: missing closing brace for format
/usr/share/alsa/init/default:52: error parsing CTL attribute
/usr/share/alsa/init/default:52: invalid rule
rone@rone-ubuntu:~$ alsamixer

---

### Post by bbbaldie on 2009-12-27
Remarking this one solved! Here's what got me there:

[http://yoyar.blogspot.com/2008/11/i-recently-setup-ubuntu-server-8.html](http://yoyar.blogspot.com/2008/11/i-recently-setup-ubuntu-server-8.html)

Adding rone (my user) to the audio group fixed it.:guitar:

---

