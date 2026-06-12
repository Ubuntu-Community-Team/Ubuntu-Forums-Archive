---
title: "Silicon Integrated Systems"
date: 2008-07-13
forum: Multimedia Software
---

### Post by Jcink on 2008-07-13
i'm trying to help a friend who's using Hardy, but he has a really funky hardware setup:

```
   1.
      To run a command as administrator (user "root"), use "sudo <command>".
   2.
      See "man sudo_root" for details.
   3.
       
   4.
     x@x-desktop:~$ lspci
   5.
      00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
   6.
      00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
   7.
      00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
   8.
      00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
   9.
      00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
  10.
      00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
  11.
      00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
  12.
      00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
  13.
      00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
  14.
      01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)
  15.

```

His problem largely lies with his video card; he says the resolution is real small, can't change it, looks all stretched, etc. I can't seem to find drivers for this kind of card anywhere for Linux, never heard of Silicon Integrated Systems.

Any advice on what to do?

Thanks.

EDIT: I think i found them here: 

[http://www.sis.com/download/download_step1.php](http://www.sis.com/download/download_step1.php)

but they're all RPM files... how do I use that here?

edit: actually I found an executable now, and unzipped it but i have no idea what to do with it. It's just one file "XSiS_SVGA"

---

### Post by xc3RnbFO8P on 2008-07-13
What kind of monitor does your friend got?
Did you check Screen and Graphics?

---

### Post by ajgreeny on 2008-07-13
To run Screen & Graphics, which is now hidden, for some reason, use Alt+F2 and command ```
gksudo displayconfig-gtk
```in the box that appears.  It may help to set drivers etc etc.

---

