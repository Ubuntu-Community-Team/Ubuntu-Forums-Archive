---
title: "No Sound on Gutsy Fresh Install"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by zksailor534 on 2007-11-06
I just completed a fresh install of Gutsy on my computer and for the first time I have no sound (had no problems with 6.04,6.10,or 7.04).

lspci output:
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
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
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
05:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
05:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

output from cat /proc/asound/cards :
 0 [SN25P          ]: ICE1724 - Shuttle SN25P
                      Shuttle SN25P at 0xa000, irq 5


I've tried working through the "Comprehensive Sound Problem Solutions Guide" and it shows that a driver does not exist for my sound card.  This I could understand if I had ever had problems before, but why does it not work all of a sudden?

---

### Post by chaos_abl on 2007-11-13
Hello,

I have the same problem: fresh installation of gutsy but I have no sound. I posted this problem a few days ago in the german ubuntuusers-forum, but until now nobody  could help me.
I posted my sound configuration also there: [http://ubuntuusers.de/paste/17843/](http://ubuntuusers.de/paste/17843/)

Does anyone have a solution?

Greetings from switzerland,
chaos

---

### Post by nedkelly on 2007-12-06
Tested if this works [http://www.mepis.org/docs/en/index.php/VIA_Envy24PT/HT]("http://www.mepis.org/docs/en/index.php/VIA_Envy24PT/HT")

---

### Post by frith01 on 2007-12-17
Upgrading Alsa to 1.0.15 fixed my problem.  (It added another control to the mixer which was muted previously).

This link helped with the upgrade ::

[http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html](http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html)

---

