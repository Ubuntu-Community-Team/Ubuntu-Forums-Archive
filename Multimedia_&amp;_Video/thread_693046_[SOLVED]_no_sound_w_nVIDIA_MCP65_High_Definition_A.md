---
title: "[SOLVED] no sound w/ nVIDIA MCP65 High Definition Audio"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by Maelgwyn on 2008-02-10
Hi guys,

I have had sound working fine before, but since I've installed Emerald, I have none!

here's lspci and aplay :)

```

nik@taonga:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
nik@taonga:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nik@taonga:~$ 

```Last time the sound died on me, I simply installed Envy & re-installed the drivers. I've tried that again but no luck this time >.<

---

### Post by Maelgwyn on 2008-02-11
here's what I've done since the post

* Un-installed the Envy drivers & then re-installed them
* removed Emerald
* opened System -> Admin -> Restricted Drivers Manager and ticked the box & rebooted (Don't know why this was **un**-ticked!

---

### Post by Maelgwyn on 2008-02-11
Fixed!!

Thanks to the power of Google, I found [this](http://linuxblog.pansapiens.com/?s=nvidia).

So all I needed to do was
```
sudo apt-get install linux-backports-modules-generic
```

and now I have sound! ^_^

---

