---
title: "Can get no sound when I record my desktop session"
date: 2008-02-14
forum: Multimedia Production
---

### Post by geo909 on 2008-02-14
Hello everybody.

I am trying to record a desktop session but I can get no sound through my mic..
That's because the soundcard is not properly configured, as an error message warns.

I'm using gtk-recordMyDesktop

Here's what's on the Advanced->Sound window:

[CENTER][IMG][[IMG]http://www.imageshack.gr/files/un22u8qxitkkrvvii7l8.png[/IMG]](http://www.imageshack.gr/view.php?file=un22u8qxitkkrvvii7l8.png)[/IMG][/CENTER]


... and here's the warning message:

[CENTER][IMG][[IMG]http://www.imageshack.gr/files/05tsbqsmbxrt9x31l1rc.png[/IMG]](http://www.imageshack.gr/view.php?file=05tsbqsmbxrt9x31l1rc.png)[/IMG][/CENTER]

That actually appears a second or two after I press the record button and the recording stops.
Any ideas, anyone?
Thanks in advance!

---

### Post by Creative2 on 2008-02-15
well before you must configure your sound card ...then you can use recordmydeskotop...it's obvious

so i think you must do 

lspci | grep Audio 
then see in the wiki for your sound card ,

---

### Post by geo909 on 2008-02-15
Thanks for your answer!

> **Creative2 said:**
> well before you must configure your sound card ...then you can use recordmydeskotop...it's obvious


Yes,  I know that. Help to configure my soundcard was actually what I had in mind when I post that thread.

> 
so i think you must do

lspci | grep Audio 

I'll try it (I'm not on my PC right now) and I'll tell what happened..

---

### Post by geo909 on 2008-02-16
```
so i think you must do

lspci | grep Audio
```

No output from this command..

However this is what I get when I give "lspci":
```
jorge@jorge-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 0e)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:05.0 Serial controller: Rockwell International HCF 56k Data/Fax/Voice Modem (rev 01)
01:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
jorge@jorge-desktop:~$ 

```

What should I do to configure my soundcard?

---

### Post by jfmxl on 2008-02-16
I cannot record sound either. For the longest time I got nothing at all. I was trying to work with audacity. I gave that up. Now I'm just trying to get sound-record to do so. It does seem to record, but so faintly and unclearly that it seems like an hallucination.

Any help appreciated. This is extemely frustrating. Google returns many sad tales of people trying to make sound work with ubuntu. So far no solutions.

jfl@ws1:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
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
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
05:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by geo909 on 2008-02-16
So, any ideas on how one could "configure his soundcard"?!

---

