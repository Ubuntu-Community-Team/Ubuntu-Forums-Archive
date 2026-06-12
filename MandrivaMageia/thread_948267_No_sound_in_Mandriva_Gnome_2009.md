---
title: "No sound in Mandriva Gnome 2009"
date: 2008-10-15
forum: Mandriva/Mageia
---

### Post by sertse on 2008-10-15
Hi, I'm currently using Mandriva GNOME 2009, and its a great OS... only I couldn't get my sound working. 

I tried messing the stuff in system -> sounds, but to no avail. I even tried using alsaconf in desperation but still nothing. 

Normally (as in other OSes) autodetect would work, otherwise putting it to cmedia cmi8738 / cmpci  get it going...

Anyways, can anyone help?

---

### Post by AdamWill on 2008-10-15
well, let's check the current state of affairs. What does:

lspcidrake -v

(run as root, at a console) report?

What does alsamixer show - the right controls for your card? If it just shows a couple of PulseAudio channels, try alsamixer -c0 .

---

### Post by sertse on 2008-10-15
[root@localhost user]# lspcidrake -v
snd_cmipci      : C-Media Electronics Inc|CM8738 [MULTIMEDIA_AUDIO] (vendor:13f6 device:0111)
8139too         : Realtek Semiconductor Co., Ltd.|RTL-8139/8139C/8139C+ [NETWORK_ETHERNET] (vendor:10ec device:8139 subv:1043 subd:8109)
i2c_i801        : Intel Corporation|82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [SERIAL_SMBUS] (vendor:8086 device:266a subv:1043 subd:2640)
ata_piix        : Intel Corporation|82801FB/FW (ICH6/ICH6W) SATA Controller [STORAGE_IDE] (vendor:8086 device:2651 subv:1043 subd:2601)
iTCO_wdt        : Intel Corporation|82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [BRIDGE_ISA] (vendor:8086 device:2640)
unknown         : Intel Corporation|82801 PCI Bridge [BRIDGE_PCI] (vendor:8086 device:244e)
uhci_hcd        : Intel Corporation|82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [SERIAL_USB] (vendor:8086 device:265b subv:1043 subd:2640)
uhci_hcd        : Intel Corporation|82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [SERIAL_USB] (vendor:8086 device:265a subv:1043 subd:2640)
uhci_hcd        : Intel Corporation|82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [SERIAL_USB] (vendor:8086 device:2659 subv:1043 subd:2640)
uhci_hcd        : Intel Corporation|82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [SERIAL_USB] (vendor:8086 device:2658 subv:1043 subd:2640)
shpchp          : Intel Corporation|82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [BRIDGE_PCI] (vendor:8086 device:2660)
snd_hda_intel   : Intel Corporation|82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (vendor:8086 device:2668 subv:1043 subd:818f)
Card:Intel 810 and later: Intel Corporation|82915G/GV/910GL Integrated Graphics Controller [DISPLAY_VGA] (vendor:8086 device:2582 subv:1043 subd:2582)
intel_agp       : Intel Corporation|82915G/P/GV/GL/PL/910GL Memory Controller Hub [BRIDGE_HOST] (vendor:8086 device:2580)
hub             : Linux 2.6.27-desktop586-0.rc8.2mnb uhci_hcd|UHCI Host Controller [Hub|Unused|Full speed (or root) hub] (vendor:1d6b device:0001)
hub             : Linux 2.6.27-desktop586-0.rc8.2mnb uhci_hcd|UHCI Host Controller [Hub|Unused|Full speed (or root) hub] (vendor:1d6b device:0001)
hub             : Linux 2.6.27-desktop586-0.rc8.2mnb uhci_hcd|UHCI Host Controller [Hub|Unused|Full speed (or root) hub] (vendor:1d6b device:0001)
hub             : Linux 2.6.27-desktop586-0.rc8.2mnb uhci_hcd|UHCI Host Controller [Hub|Unused|Full speed (or root) hub] (vendor:1d6b device:0001)
usblp           : Hewlett-Packard|psc 1200 series (vendor:03f0 device:2f11)
hub             : Unknown|USB2.0 Hub [Hub|Unused|Full speed (or root) hub] (vendor:05e3 device:0606)
zc3xx           : Z-Star Microelectronics Corp.|Sansun SN-510 WebCam [hv713d] (vendor:0ac8 device:301b)



Using "alsamixer -c0" it reports the controls for the the cmedia card, yes.

---

### Post by AdamWill on 2008-10-15
OK, so it seems like it's there.

I notice you have another audio device:

snd_hda_intel : Intel Corporation|82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (vendor:8086 device:2668 subv:1043 subd:818f)

I guess that's the onboard. I suspect sound may be being routed there instead. Try starting something playing sound, then run pavucontrol. It should show the playing sound as a 'stream'. You can right click on it and it will give you the option to move it between devices. Move it to the card you want. Does it work now?

If so, you can set one output device to be the default permanently by right-clicking on it on the output devices tab.

---

### Post by sertse on 2008-10-15
Works!

Thanks Adam :)

---

### Post by AdamWill on 2008-10-16
Great! Glad we got it. :) The default device setting should be saved permanently (including across reboots) - poke me if that doesn't seem to be working.

(Yes, it only took Linux 17 years and about fifty three sound servers before we got one that can set the default output device graphically. That's progress for you!)

---

