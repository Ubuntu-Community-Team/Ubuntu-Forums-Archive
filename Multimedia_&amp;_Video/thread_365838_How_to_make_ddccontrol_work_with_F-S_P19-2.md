---
title: "How to make ddccontrol work with F-S P19-2 ?"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by crosis on 2007-02-20
Hi,
I'm an owner of Fujitsu Siemens P19-2 lcd and i don't know how to make it work correctly with ddccontrol (i prefer Tune Display in MS Windows which I use to change brightness during night via presets)

typing sudo ddccontrol -p:
```
ddccontrol version 0.4.2
Copyright 2004-2005 Oleg I. Vdovikin (oleg@cs.msu.su)
Copyright 2004-2006 Nicolas Boichat (nicolas@boichat.ch)
This program comes with ABSOLUTELY NO WARRANTY.
You may redistribute copies of this program under the terms of the GNU General Public License.

Skanowanie w poszukiwaniu znanych monitorów.... **(In english: something like searching for hardware)**
Wykryte monitory: **(ENG: Devices found)**
 - Urz&#261;dzenie: pci:05:00.0-2
   Obsluguj&#261;ce DDC/CI: Tak
   Nazwa monitora: Fujitsu Siemens P19-2
   Typ wej&#347;cia: Cyfrowe **(ENG: DIGITAL input)**
  (Zaznaczony automatycznie)
Czyta EDID i inicjalizuje DDC/CI na magistrali pci:05:00.0-2...
Non-fatal error: Invalid response, magic is 0x23
Non-fatal error: Invalid response, magic is 0x23
Non-fatal error: Invalid response, magic is 0x23
Non-fatal error: Invalid response, magic is 0x23
Non-fatal error: Invalid response, magic is 0x23
Non-fatal error: Invalid response, magic is 0x23
Non-fatal error: Invalid response, magic is 0x1c
Non-fatal error: Invalid response, magic is 0x03

EDID zaczyta&#322;:
        Plug and Play ID: FUS0552 [Fujitsu Siemens P19-2]
        Type wej&#347;cia: Cyfrowe

= Fujitsu Siemens P19-2
```

When I'm trying to run ddccontrol by choosing "Run gddccontrol" added to a tool bar in gnome:

> Error occured during opening monitor device. Monitor can be disconnected, press regresh button on the monitors list

[[img]http://img76.imageshack.us/img76/3854/zrzutekranuustawieniamoxt4.th.png[/img]](http://img76.imageshack.us/my.php?image=zrzutekranuustawieniamoxt4.png)

After refresh:
> No monitors which are using DDC/CI found
Graphic card may require additional kernel modules (i2c-dev i framebuffer)
[[img]http://img441.imageshack.us/img441/8004/zrzutekranuustawieniamoyv2.th.png[/img]](http://img441.imageshack.us/my.php?image=zrzutekranuustawieniamoyv2.png)

But when I type sudo gddccontrol in console the window which appears almost the same like the one above opens, but I can choose there "Manage profiles". When i choose that there's an information:
> Choose the name of group/Wybierz nazw&#281; grupy
I think that there should be some settings to adjust, but there's nothing :(

[[img]http://img76.imageshack.us/img76/7800/zrzutekranuustawieniamopf3.th.png[/img]](http://img76.imageshack.us/my.php?image=zrzutekranuustawieniamopf3.png)

I have my X800GTO's drivers installed, like authors of ddccontrol said, P19-2 should be supported by this application. LCD connected by DVI.

typing modprobe radeonfb and i2c-dev make no change :(

First of all I'm sorry for my english, cuz I'm from poland, and messages which appears on my Ubuntu 6.10 are in polish language so I have just translated them into english, but that's not an ideal and 1:1 translation like on english version of ubuntu/ddccontrol :(
So english texts here are just free translations ;)

---

