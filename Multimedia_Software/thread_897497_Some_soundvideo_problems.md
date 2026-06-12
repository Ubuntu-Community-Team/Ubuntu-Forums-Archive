---
title: "Some sound/video problems"
date: 2008-08-22
forum: Multimedia Software
---

### Post by Guyon on 2008-08-22
I just installed Ubuntu 3 days ago and so far I'm loving it. The only problem I'm having is with flash videos and sound on various things. I've re-installed flash and restarted but no effect was taken. Here are some of my problems:

Flash videos don't have sound
Flash videos freeze every 3 seconds or so
Sometimes when I load a video on a website, Banshee pauses and won't play anything until I close & re-open it.

I'm running Ubuntu 8.04.

This is my first time ever running Linux so a lot of things won't make sense to me, sorry. I'll do my best to explain things to you. I've read/tried some of the things in the stickies to no avail.

---

### Post by livestockPimp on 2008-08-22
have you got your graphics card drivers installed?

If this is a fresh install and your graphics card is not detecting properly/detecting out of the box this could cause flash freeze ups, ect since you will be using the standard VESA drivers.

---

### Post by Guyon on 2008-08-22
I haven't manually installed any graphics card drivers, is there a way to check if I do? If it helps for you to know, all sound worked in Windows.

---

### Post by livestockPimp on 2008-08-22
what video card do you have?
can you post the output of "lspci"

---

### Post by Guyon on 2008-08-22
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)


That was easy. :)

---

### Post by Minipalmer on 2008-08-22
Hey Guyon, I just solved this problem for my own computer.

Is it just flash videos you're seeing the problem with? (Or hearing :)) I kind of went in a flurry of downloading last night and just got everything I could, including many different installations of the new Flash 10 beta. Whatever I did, it worked.

If you don't want to go look for the Flash 10 beta, but can wait, I think it's coming with the new 8.10 update within the next couple weeks.

---

### Post by Guyon on 2008-08-22
> **Minipalmer said:**
> Hey Guyon, I just solved this problem for my own computer.

Is it just flash videos you're seeing the problem with? (Or hearing :)) I kind of went in a flurry of downloading last night and just got everything I could, including many different installations of the new Flash 10 beta. Whatever I did, it worked.

If you don't want to go look for the Flash 10 beta, but can wait, I think it's coming with the new 8.10 update within the next couple weeks.

Thanks. When I tried installing Flash 10 I got this error:

"cp: cannot stat `/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/guyon/.mozilla/plugins/libflashplayer.so': No such file or directory

Installation complete."


I really don't know how to fix that. :s

---

