---
title: "Screen corruption on resume i810"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by lucianalbrecht on 2007-02-13
I'm having a problem with resume from ram on my Toshiba Tecra A2.

It suspends and resumes okay, but upon resume the screen is corrupt:

[CENTER][IMG]http://farm1.static.flickr.com/130/388955090_b43fb6ce49_m.jpg[/IMG]
[/CENTER]
 [CENTER][(Larger version)]("http://www.flickr.com/photo_zoom.gne?id=388955090&size=o")
[/CENTER]
 
I have an i855 graphics card, and I'm using the i810 driver. Oddly, the problem happened with early Dapper, but went away on an update, but has returned with Edgy.

Thanks in advance,

Output of lspci:
```
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
01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
```

---

### Post by su99 on 2007-05-04
hi, i met the same issue in 7.04 feisty.

my laptop is dell inspiron 710m, with intel 855 card, and xorg uses i810 driver.

sometimes after suspend/resume, the screen is corrupted. looks similar to your screenshot. some elements become transparent. for example, in the password dialog after resume, there is only the text box for inputing password. the gray window body and titlebar are gone. and after you return to the desktop, the icons on the panels are totally messed up, looks like they are overlapping with each other. and page-scrolling in most apps cause "tearing".

restarting x won't solve this problem. you have to restart the entire system.

i'm so eager to see if anyone knows what could be the reason...

it happens randomly. i haven't figured out any pattern.

---

### Post by oprocopio on 2007-05-16
Same problem too.

Toshiba Tecra A2 with Kubuntu Feisty.

Do someone have a solution?

Thanks.

Orlando

---

### Post by oprocopio on 2007-05-16
I've solved my problem.

just add a "#" before of "Load GLcore" in the xorg.conf file.

Orlando

---

