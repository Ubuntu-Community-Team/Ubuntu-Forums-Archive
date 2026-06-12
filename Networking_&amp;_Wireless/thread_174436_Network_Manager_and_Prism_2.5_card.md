---
title: "Network Manager and Prism 2.5 card"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by slightly72 on 2006-05-11
I have an Intersil Corporation Prism 2.5 Wavelan card in my laptop, and am trying to use network manager with it (nm-applet). When launching nm-applet, I get the following message:

> The network device "Intersil Corporation Prism 2.5 Wavelan chipset (eth1)" does not support wireless scanning. It will not be completely functional.

The "orinoco_pci" module is loaded for this card. I've tried gtkwifi and got about the same message. nm-applet connects me when I manually supply the network name, but that kinda defeats the purpose of having it.

Is there any trick to have wireless scanning work for this card (it works in Windows XP -- so it's not a hardware problem)? Would it work if I use ndiswrapper?

Thanks

---

### Post by Dr. Nick on 2006-05-11
Yes you could use ndiswrapper and it should work.
I have a prism2 card and the wlan-ng drivers dont fully implement the standard wireless extensions so some of the features dont work like they do when I use ndiswrapper

If you go with ndiswrapper be sure to unload the orinco drivers as they will be used instead of ndiswrapper

---

### Post by slightly72 on 2006-05-11
Thanks. Two quick questions:

1. Do you know where on Windows I can find the driver for the card? Haven't used Windows systematically for the past 14 years, and I'm kinda lost with its setup. I've also tried to look for a driver on the internet, but could not find anything (Intersil has sold its wireless division to Conexant -- which does not have any drivers for this card). I got the laptop used, and it does not have all the cd's with it.
2. How do I disable the loading of orinoco_pci?

---

### Post by Dr. Nick on 2006-05-11
> **slightly72]Thanks. Two quick questions:

1. Do you know where on Windows I can find the driver for the card? Haven't used Windows systematically for the past 14 years, and I'm kinda lost with its setup. I've also tried to look for a driver on the internet, but could not find anything (Intersil has sold its wireless division to Conexant -- which does not have any drivers for this card). I got the laptop used, and it does not have all the cd's with it.[/quote] 
Does the card currently work in XP? If so then go to control panel- system -hardware -device manager - find the wireles card - right clickk to properties- click driver tab- their should be something to list current driver files.

Its been awhile since Ive used windows for a long period of time aswell  said:**
> 
2. How do I disable the loading of orinoco_pci?

Their is supposedly a way to blacklist a driver from being loaded, never worked for me though. My solution was to move or delete the prism2 file. open a terminal and type 
locate orinoco_pci
it should be under /lib/modules/2.6.15-21-386/kernel/drivers/net/wireless/ or similar. Either just delete it or move it somewhere  else. Just keep in mind that this will have to be done after each kernel upgrade

---

### Post by slightly72 on 2006-05-11
Thanks, I found them. The most bizarre thing happened, though. I've installed ndiswrapper, went through the whole card installation process, rebooted the computer. Haven't removed the drivers, decided to blacklist them. After reboot, there was no wlan0 card, ndiswrapper was loaded, but (drums please) wireless scanning was working. Checked which modules are loaded -- and orinoco and orinoco_pci are loaded, and used by hermes. Both nm_applet and gtkwifi can correctly detect all networks (mine, plus 2 neighbors). It's pretty scary, though, but hope it works.

---

### Post by Dr. Nick on 2006-05-11
heh, who knows lol
Hope it works right for you.

---

### Post by slightly72 on 2006-05-13
Of course, it would have been too fairy-tale-ish to work like that -- after a while the whole networking started to be quite unstable and not quite working. A better solution is posted here:

[http://www.ubuntuforums.org/showthread.php?t=12340&highlight=orinoco+scanning]("http://www.ubuntuforums.org/showthread.php?t=12340&highlight=orinoco+scanning")

Basically, it needs upgrading the drivers for orinoco-based cards and compiling them. It worked quite well, without any problems.

---

