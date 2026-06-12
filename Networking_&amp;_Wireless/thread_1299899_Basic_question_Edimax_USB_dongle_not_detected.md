---
title: "Basic question: Edimax USB dongle not detected"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by KingNeil on 2009-10-24
I have an Edimax EW-7318USg, and this is a very basic question. When I plug it into Windows, it detects it and takes me through the process of installing drivers.

However, when I plug it into Ubuntu, it does nothing. No USB storage comes up, no network is detected. It's as if the dongle is completely ignored. I am running Ubuntu under VirtualBox, and I do indeed have the dongle set up under USB settings so that VirtualBox can take control of the device instead of Windows.

By the way, I can run this off a live CD too, so if you feel VirtualBox may be the limiting factor, I don't actually need VirtualBox.

So how do I get Ubuntu to detect the damn thing?

---

### Post by KingNeil on 2009-10-24
I put the dongle in another USB port, and typed lsusb into Terminal. The output was:

> 
Bus 002 Device 013: ID 7392:7318  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


The first result looks as if it could be the Edimax 7318 device, which is promising.

I also clicked the network icon on the top bar and it shows the following:

> Wired Network (Elitegroup Computer Systems RTL8111/8168B PCI Express Gigabit Ethernet Controller)

I'm not sure if that refers to my laptop's ethernet port or my Edimax device.

Come on guys. Help a brother out!

---

### Post by KingNeil on 2009-10-25
I'm going to bump this once and then, if no one responds, sob for days.

---

### Post by coffeecat on 2009-10-25
> **KingNeil said:**
> Come on guys. Help a brother out!

I'll see what I can do. :p

One problem seems to be that Edimax has used different chipsets at different times without changing the model number. I thought only Belkin was up to this underhanded trick and I'm disappointed that Edimax does this too. Anyway, my Edimax EW-7318Ug USB dongle works just fine with Ubuntu Jaunty and Karmic, but lsusb gives me:

```
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
```See the different ID number? That's the important bit. (By the way, I'm reliably informed that my stick **doesn't** have the RT2501 chipset, but a much later one, but that's another story. :?) Anyway when I googled "7392:7318" (which is the ID for your version of the stick) I found [this thread]("http://www.backports.ubuntuforums.org/showthread.php?t=1182602"), which links to [this post]("http://ubuntuforums.org/showpost.php?p=7524721&postcount=7") which may or may not be of help. If not, try that google for yourself and you may come up with something better.

> **KingNeil said:**
> if you feel VirtualBox may be the limiting factor

I think it could be, although there's clearly a problem with your wireless chipset in Ubuntu. I may be missing something here, but if you're running Ubuntu as a guest in Windows, why not let Windows take care of the wireless device, and use the virtual ethernet/NAT wotsit in VirtualBox for internet connection in Ubuntu? I've got Ubuntu running in a VirtualBox machine as a guest in MacOS on my Mac Mini, and on my main Ubuntu machine I've got Windows running as a VirtualBox guest. Both machines connect to my router wirelessly, but both virtual machines "think" they have an ethernet connection.

> **KingNeil said:**
> if no one responds, sob for days.

Cheer up! :wink:

**Edit:** apologies - eyesight failing. :( I've got the Edimax EW-7318Ug, whereas you've got the EW-7318USg, so I withdraw my remarks about underhanded tricks from Edimax (but not from Belkin!) - and that'll explain the different chipsets. Whatever, I hope the links are of use.

---

### Post by KingNeil on 2009-10-25
> **coffeecat said:**
> I'll see what I can do. :p
I may be missing something here, but if you're running Ubuntu as a guest in Windows, why not let Windows take care of the wireless device, and use the virtual ethernet/NAT wotsit in VirtualBox for internet connection in Ubuntu? 

Because I'm trying to use the device for cracking Wifi encryption using injections. Of course, under perfectly legal reasons

---

### Post by KingNeil on 2009-10-25
By the way, the instructions in your link are far too complex and variable to follow. I need one basic guide on how this is done, not link after link and question after question.

---

### Post by coffeecat on 2009-10-25
> **KingNeil said:**
> Of course, under perfectly legal reasons

I hope so, but the word cracking is always suspect. I am sure you will not be offended if I remind you of the forum [code of conduct](http://ubuntuforums.org/index.php?page=policy).

---

### Post by KingNeil on 2009-10-25
It's perfectly legal. I'm hacking my own connection for educational purposes.

---

