---
title: "Linuxant HSF Drivers + Sound"
date: 2008-08-29
forum: Multimedia Software
---

### Post by benign on 2008-08-29
I'm having a problem with this, but am making progress. A few weeks ago I tried installed the Linuxant HSF drivers for my  Conexant HSF 56k Data/Fax Modem and the modem worked fine. Upon reboot the sound icon was X'd out and there was no sound at all. I tried uninstalling the drivers and reinstalling ALSA but it didn't fix it, so I ended up reintalling ubuntu.

I'm trying it again now and I've found some ALSA drivers from the Linuxant site ([http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)) that are supposed to have improved support for the HSF drivers.

I installed the ALSA drivers yesterday and then the modem drivers, and everything was working great. Now the fishy part is after I rebooted, I get the little drum-roll sound at the login screen, and my speaker icon IS NOT X'd out; however, no sound works after that. 

Totem's icon/volume control is grayed out. Amarok freezes up when I try to play music.

If I use System -> Preferences -> Sound to test everything, I get no output from the tests for 'Autodetect.' and 'PulseAudio.'

The other tests (ALC888 Analog/Digital, ALSA, OSS) give:

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

```

aplay gives:
```

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
aplay: main:546: audio open error: Device or resource busy

```

and aplay -l gives:

```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Anyone have any ideas of what I can do? I've tried using modprobe to load up a few different sound modules, but nothing works. I hate to uninstall the modem drivers because I've been needing to send a lot of faxes lately.

---

### Post by benign on 2008-08-29
bumpity bump.

I tried reinstalling the alsa sound drivers from the linuxant site and it made the sound and modem work at the same time - until I rebooted. Then it was back to the drumroll sound, but nothing after that.

This is kind of ridiculous. I guess I'll have to install the fax drivers every time I want to send a fax, and then uninstall them after I'm done with them.

Has anyone had any luck getting a conexant modem working in virtualbox under XP?

---

### Post by Crafty Kisses on 2008-08-29
Post the results of this command > lspci

---

### Post by benign on 2008-08-29
Thanks for the response. :)

lspci:

```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem

```

---

