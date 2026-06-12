---
title: "Envy - All drivers incompatible?"
date: 2009-01-06
forum: Multimedia Software
---

### Post by VoXoM on 2009-01-06
So I installed EnvyNG and all the drivers on the list are incompatible, and of course unrecommended.

My graphic card is an ATI, I don't know which exactly, but it's quite old.

Any help would be greatly appreciated.

---

### Post by tuxxy on 2009-01-06
I would help if you had the model.  If its a PCI card try lspci in terminal

---

### Post by Lee_Machine on 2009-01-06
Here is a wiki howto for ATI cards

just choose if you have 8.04 or 8.10

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

good luck

---

### Post by VoXoM on 2009-01-06
lspci
> 00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0d.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

---

### Post by tuxxy on 2009-01-06
You have a ATI Radeon 9200 SE by the looks of it and according to the wiki it should work fine, is there no restricted drivers provided in Ubuntu?

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

---

### Post by VoXoM on 2009-01-06
> **tuxxy said:**
> You have a ATI Radeon 9200 SE by the looks of it and according to the wiki it should work fine, is there no restricted drivers provided in Ubuntu?

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

How can I know if there is a restricted driver or not?

---

### Post by tuxxy on 2009-01-06
> **VoXoM said:**
> How can I know if there is a restricted driver or not?

Open** system > admin > hardware drivers **and activate it here.

---

### Post by Melcar on 2009-01-06
Newer drivers do not support those cards.  You have to stick with the open source driver (Ubuntu loads it by default).

---

### Post by VoXoM on 2009-01-06
> **tuxxy said:**
> Open** system > admin > hardware drivers **and activate it here.

There is nothing. It says "No proprietary drivers are in use on this system".

---

