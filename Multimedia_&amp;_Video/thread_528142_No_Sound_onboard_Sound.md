---
title: "No Sound onboard Sound"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by Nero182 on 2007-08-17
Hey I aint getting any on board sound going I played a DVD and the Video is fine tho their is no Sound.

I am using my unboard sound cause X-Fi Cards dont work on Linux. I think the onboard sound is a Nivida Chipset.

Thanks

---

### Post by wolfen69 on 2007-08-17
in terminal:
```
lspci
```
to see what soundcard

---

### Post by Nero182 on 2007-08-17
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Multimedia audio controller: Creative Labs SB X-Fi
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)



Seems to be showing my X-Fi Card...Which I didnt think it worked? Any Ideas?

---

### Post by wolfen69 on 2007-08-17
is the onboard sound enabled in BIOS?

---

### Post by Nero182 on 2007-08-17
Hmmm Good Point Let Me Reboot Mate :)

---

### Post by Nero182 on 2007-08-17
Yeh It seems to be ok...I had sound working before when it was on a different partion...but this time around I used [http://wubi-installer.org/]("Wubi") To Install Linux if it makes a difference?

---

### Post by wolfen69 on 2007-08-17
i have never used wubi, so it may be a factor.

---

### Post by Nero182 on 2007-08-17
Hmm Is thier anyway to uninstall vista and keep the files on the hard drive lyk my music and things. And then install Ubuntu onto It and then I can acess the files?

---

### Post by Nero182 on 2007-08-17
Any Ideas Guys?

---

### Post by frith01 on 2007-12-17
I upgraded Alsa to 1.0.15 and it fixed my problem. 

Info on how to  here ::

[http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html](http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html)

---

