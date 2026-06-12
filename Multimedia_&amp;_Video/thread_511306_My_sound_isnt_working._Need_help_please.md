---
title: "My sound isnt working. Need help please"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by stephen_leet on 2007-07-27
My sound isnt working, what do i do?

---

### Post by stephen_leet on 2007-07-27
Where should I start?

---

### Post by srt4play on 2007-07-27
You should start by giving the details of your system.  What sound card do you have? Laptop or desktop?  Has it always not worked since install or did it suddenly fail?

Can you open a terminal (Applications -> Accessories -> Terminal) and do the command

```
lspci
```

and post the output here.

---

### Post by stephen_leet on 2007-07-27
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0f.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 LE] (rev a2)

---

### Post by stephen_leet on 2007-07-28
Does anyone have any suggestions?

---

### Post by stephen_leet on 2007-07-28
where do I begin? I would really appreciate it if someone could start by leading me in the right direction :D

---

### Post by fredj on 2007-07-29
Open a terminal and type sudo lshw -class sound. Post the output from that here.
Also open the alsa mixer by double clicking on the speaker icon. Go to the Edit->preferences 
menu and add all the possible volume controls and switches for both playback and record.
Make sure that all the controls are umuted and set suitable volume levels for each one.

---

