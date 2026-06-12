---
title: "HP Omnibook 510 unable to connect to wlan"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by invert on 2009-07-18
I have a really old HP Omnibook 510 which I recently installed Ubuntu on. But I can't connect to my wlan! I am absolutely sure my wlan router and all are fine because all the other computers can use it. 

  OK, here's what I do. I click the network icon thing on the top right. Then I type all the details. Then I click connect. The icon for connecting appears but the balls are grey. It never connects. It is really old so I suspected it may be because the wlan card needed updating. But I can't find an update for Ubuntu for it.

  I did find an update for [Windows]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=77989&prodNameId=77991&swEnvOID=228&swLang=8&mode=2&taskId=135&swItem=ob-12205-1") though. I'm not sure if it even IS the problem. But I'm pretty open to suggestions:D

Thanks in advance!

---

### Post by invert on 2009-07-18
[SIZE=2]Ok, I just learnt that I DO need to get a driver. So my card is called "Actiontec PRISM 2.5 Integrated (USB) 802.11b Wireless LAN". Which kinda sucks because it doesn't include a product number. I guess it's just really old...
[/SIZE][SIZE=2]
  Anyway, I found NDISwrapper! But no driver exe so I couldn't do anything. I tried unzip-ing the windows version of the driver (just for luck) but it didn't work. I found out that my network controlled was "Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)" if that helps...

  On the website mentioned above, there was another file - w2k6klan.exe . So I Googled to find it, but as usual I couldn't unzip. Still on the website, I found that this same update was for both my Actiontec AND[/SIZE][FONT=Arial][SIZE=2] a "[/SIZE][/FONT][FONT=Arial][FONT=Arial][SIZE=2]3Com 10/100 Mini PCI Ethernet Adapter". I'm not absolutely sure what that means, but it may help. Again, it had no product number (like XY1234 or something like that. I'm not sure what it's called but I'm gonna call it a product number). So it's pretty hard to find. There are drivers for 3Com but all of them have a product number.

  Please help!
[/SIZE][/FONT][/FONT]

---

### Post by invert on 2009-07-18
I kinda found a workaround... I dug up an old Broadcom 4306 PCI wlan card thingy... And there is a driver for it! So I'm just going to use that till this gets resolved...

Cheers!

---

