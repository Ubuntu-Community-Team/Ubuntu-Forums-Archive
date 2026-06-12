---
title: "Best Video Card"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by podollb on 2007-12-28
I was wondering if anyone could recommend a great video card for Ubuntu? I am going to pick-up a dual DVI card, but I wanted to make sure to get one that allows me the best resolution and effects (via great driver support).

---

### Post by CCNA_student on 2007-12-28
NVidia video cards have the best Linux drivers. I personally use the ATI X300 and I like ATI better but the NVidia Linux drivers are way better than the ATI Linux drivers. And there is no specific card I can mention, anything in the 7000 or 8000 series of NVidia cards would be fine. I hope that this helps you.

       Sin Cere,

       CCNA

---

### Post by Mike'sHardLinux on 2007-12-28
You don't have to get the best card to get high resolution or effects. Do you have any kind of budget? Also, do you need an AGP or PCI  express card? Do you do any gaming?

I actually had Ubuntu Feisty (or maybe it was Edgy??) running with Beryl effects on a P4 1.7GHz with onboard Intel graphics and it ran ok.

---

### Post by podollb on 2007-12-28
Well, I guess I don't want to spend over $100 I guess. I don't do any gaming, but I have one of my PC's at home that has a NVidia card and the resolution, clarity, and effects make it a great system to use. My other system doesn't have that and I have 2 DVI flat screens that I can hook up to it, so I figured I'd get a decent card for it. I am pretty sure it is PCI Express but how do I know for sure?

Here is the lspci output:

> 00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)


How do I know which speed PCI Express slot I have?

   PCI Express x1
   PCI Express x16
   PCI Express 2.0

What about 32-bit or 64-bit cards?

---

### Post by Mike'sHardLinux on 2008-01-01
You can get a very nice dual-dvi card for under $100.

I can't tell from your lspci ouput what kind of interfaces it has.  The line about VGA mentions the Q965 integrated graphics contoller, which makes me think you have a motherboard based on an Intel 965 chipset, which I am pretty sure means PCI express. Also, a couple of lines do mention PCI Express.

What do you know about your system? Did you build it? If so, what motherboard did you use? If you bought the computer already built, what is the manufacturer and model number?

If you do in fact have pci express, chances are you have at least one x16 slot. There are very few (if any) [non-server] pci-express boards that don't have an x16 slot. You could always open up your computer and look at the motherboard.

As for the 32-bit versus 64-bit question. I have a feeling you're getting PCI Express mixed up with PCI-X. PCI Express is a serial interface. PCI-X is a parallel interface whose bus width is expressed in bits - 64 bits.

As far as bus width for PCI Express, the x16 is the important number, versus x4 or x1. Those numbers represent how many serial "lanes" are used.

---

### Post by podollb on 2008-01-01
Thanks for the very informative response. And with further investigation, you are right, I have a PCI Express x16.

---

