---
title: "projector nec lt20"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by crawall on 2008-01-16
i just installed ubuntu on my dell latitude D505 and trying to use my projector without result. The projector is a NEC lt20.
I tried the Fn+F8 switch but still no display.
What else can I do?

---

### Post by wieman01 on 2008-01-16
What graphics adapter have you got? Do you know the exact model and chipset?

---

### Post by crawall on 2008-01-16
how do i find what graphics adapter i have (the exact model and chipset)?
I'm a newbee with ubuntu

---

### Post by crawall on 2008-01-16
after using the command 'lspci' this is what i did get:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

I hope this give you an idea

---

### Post by wieman01 on 2008-01-16
Does this help?

[http://ubuntuforums.org/showthread.php?t=411674]("http://ubuntuforums.org/showthread.php?t=411674")

---

### Post by crawall on 2008-01-16
in that post they're talking about an I810 but in my conf it's an 'intel'. Is there a difference? or can i use the steps explained in that post?

---

### Post by wieman01 on 2008-01-17
> **crawall said:**
> in that post they're talking about an I810 but in my conf it's an 'intel'. Is there a difference? or can i use the steps explained in that post?
You can try at least. I think it should work with the i855 as well.

Please also take a look at this thread (which I find even better): [http://ubuntuforums.org/showthread.php?t=411674]("http://ubuntuforums.org/showthread.php?t=411674")

You can try it out first and let me know if it has worked for you.

---

### Post by crawall on 2008-01-19
No
I tried but without any result

if you have other suggestions...I'll try them all

---

### Post by wieman01 on 2008-01-19
I have another computer with a Intel 810 and all I had to do is connect the projector and press FN + F4 or something like that. Would that work for you as well? Perhaps that's too obvious an answer though...

---

### Post by crawall on 2008-01-19
no reaction for the projector, other things happend like the level of my battery, opening the cd rom,...:confused:

---

