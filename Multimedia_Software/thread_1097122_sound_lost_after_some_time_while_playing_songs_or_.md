---
title: "sound lost after some time while playing songs or movie  (get only static noise)"
date: 2009-03-15
forum: Multimedia Software
---

### Post by illusion123 on 2009-03-15
Hi, 

I am facing strange problem with my ubuntu 8.10. While playing movie or songs, I lose main voice/sound after 10-15 mins of playing. I can still hear background music and a lot of static noise, just I cannot hear the character's voice in the movie. I don't have any surround sound speakers. If I reboot the system, I get the voice back, but it goes bad again after 10-15 mins. This is very frustrating. I have tried different mp3s, movies and different players including rhythembox, movieplayer, vlc player but end up with the same problem every time.

I am using on-board audio card on the system I have assembled. Here are the config details:

Motherboard: ECS GF7100PVT-M3 with 8 channel Audio
Processor: Inteal: E7300
Speakers: stereo speakers.

I have tried setting the system->preferences->sound to Auto-detect as well as ALSA. But I run into the same issue each time. 

lspci
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation Device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)

lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c025 Logitech, Inc. MX500 Optical Mouse
Bus 001 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cat /proc/asound/cards 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfebf8000 irq 22

cat /proc/asound/modules 
 0 snd_hda_intel


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

Any help is appreciated. 

Thanks,

[LIST=1]
[/LIST]

---

### Post by illusion123 on 2009-03-19
bump

---

### Post by nelskurian on 2009-03-19
just go through the below guide..May its helping..
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

