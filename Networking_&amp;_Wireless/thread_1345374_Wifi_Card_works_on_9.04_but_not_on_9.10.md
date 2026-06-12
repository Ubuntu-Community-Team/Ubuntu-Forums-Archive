---
title: "Wifi Card works on 9.04 but not on 9.10"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by beastrace91 on 2009-12-04
Hey All,

So I am putting Ubuntu on an old Toshiba laptop for a friend of mine and naturally I wanted to put 9.10 on it but for some reason the internal Intel wifi card does not work on the 9.10 live CD but it works fine on the 9.04 live CD.

Here is the lspci output from the laptop: ```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

```

Ideas why it does not work under 9.10?...

Regards,
~Jeff

---

### Post by bkratz on 2009-12-04
> **beastrace91 said:**
> Hey All,

So I am putting Ubuntu on an old Toshiba laptop for a friend of mine and naturally I wanted to put 9.10 on it but for some reason the internal Intel wifi card does not work on the 9.10 live CD but it works fine on the 9.04 live CD.

Here is the lspci output from the laptop: ```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

```

Ideas why it does not work under 9.10?...

Regards,
~Jeff



Although this is referencing the remix version, maybe there is something important here. It looks like he did get it to work with something from another forum.


[http://ubuntuforums.org/showthread.php?t=1304759&highlight=RT2500](http://ubuntuforums.org/showthread.php?t=1304759&highlight=RT2500)




Good Luck

---

### Post by beastrace91 on 2009-12-04
Ahh alrighty thanks for the link. For simplicities sake I think I'm just going to boot jaunty on it due to my roommate would be bear to have to run a command in terminal every time she boots the laptop xD

Thanks,
~Jeff

---

### Post by northd_tech on 2009-12-04
I haven't worked with the RT2500 wireless, but I've seen several other wireless interfaces have big problems from one kernel to another (even when both are ubuntu 9.04, for example).  Then when you get it working in one kernel, it won't work with the other kernel(s), unless you install/compile/configure for them individually too.  KGRUBEditor is a good tool to find if you're doing much of that.

Edit:  You might need to install some header packages and other stuff if you need to build a kernel module to get it working.

Here is the ubuntuWiki for that wireless interface though- it might have something helpful (or search for some more RaLink 2500 threads here).

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

Good luck.

---

