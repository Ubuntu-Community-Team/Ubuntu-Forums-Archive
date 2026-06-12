---
title: "Sapphire card?"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by Sonja on 2008-03-07
How do I know which video card I have? And then how do I make sure I'm using the best drivers for it? Right now it just says I'm using "generic VESA-compliant", so I assume there's a driver specifically for my card that would be better?

```
sonja@sonja:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
03:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c3
03:00.1 Audio device: ATI Technologies Inc Unknown device aa10
04:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
04:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)

```

---

### Post by jrusso2 on 2008-03-07
Its some kind of ATI card but I don't know which one might have to take it out and see what it says on the board

---

### Post by markoloka on 2008-03-07
Do you have any idea how old/new it is? Is it AGP or PCIE?
Try to install new ati driver. Look from those stickys for instructions.

---

### Post by kellemes on 2008-03-07
@Sonja:
You can also look in /var/log/Xorg.0.log for hints..

---

### Post by Sonja on 2008-03-07
I'm trying [http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1) to see if it works, but it's asking me to insert my Ubuntu CD in the cd-rom. weird.

---

### Post by Sonja on 2008-03-07
OK, now my xorg.conf file is missing or empty!

---

### Post by Sonja on 2008-03-07
I looked inside on the card and it does say HD.

---

### Post by Sonja on 2008-03-07
OK I totally reinstalled xorg and that fixed it. Now it seems to be running the HD driver, but when I go in System > Admin > Screens and Graphics, nothing opens at all.

---

