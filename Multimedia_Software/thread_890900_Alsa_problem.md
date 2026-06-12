---
title: "Alsa problem"
date: 2008-08-15
forum: Multimedia Software
---

### Post by kylet450 on 2008-08-15
Hi, 

I have a creative labs augigy ls ( ca0106 )
And i can only get the 2 front speakers working.
Can anyone help?

aplay -l

> kyle@G4m3R:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



lspci

> kyle@G4m3R:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
03:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1)


:confused:Can you help please?:confused:

If you need anymore data i can supply.
Front 2 speakers work, others dont.

Thank you

---

### Post by markbuntu on 2008-08-15
Try this:

(Open the etc/pulse/daemon.conf file in an editor as sudo.) In a terminal type:
```

 sudo gedit /etc/pulse/daemon.conf.

```
 An editor will open the file for you.Find the line:
```

default-sample-channels=2

```
change the 2 to 5, for 4.1 surround, 6 for 5.1 surround, 8 for 7.1 surround. Save the file and restart the pulseaudio daemon:
kill
```

killall pulseaudio

```
restart
```

pulseaudio -D

```

---

### Post by kylet450 on 2008-08-16
Thanks for that, but it did not work i still only get the front 2 speakers working, not the back 2

---

### Post by markbuntu on 2008-08-16
You need to enable them (unmute) and turn them on in the sound mixer.

---

