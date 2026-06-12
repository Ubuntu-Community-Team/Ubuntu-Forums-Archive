---
title: "Work network printer setup: newbie help"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by nijinsky on 2006-01-13
Hi All.

I'm a newbie. I have ubuntu on my desktop accessing our wlan. We have a shared network printer attached to our ethernet-lan. I have a winXP laptop next to me accessing the same wlan as my ubuntu and can print to the HB 4050 printer butr I cannot get ubuntu printing. In system-adimn-printing I used these settings (blaged from my XP machine) but I dont know if they are the correct ones to use.

General tab
description laserjet 4050
location "empty"
resolution default

Driver tab
driver laserjet 4050

connection tab
network printer radio button ticked
dropdown menu HPjetdirect
host 130.xxx.xxx.xxx ip of what I think is the correct
port 9100

Can any tell me what settings to copy from my XP box to ubuntu to get printing?

All the best
Bob

---

### Post by hajk on 2006-01-14
You seem to have all the required information already... so what's the problem then applying it?

Click on System --> Administration --> Printing, and double click on the New Printer icon. Choose Network printer and HP JetDirect; then enter the printer address (just the address), the 9100 port is already standard; then in the next screen choose HP and select your HP LasetJet 4050, and accept the suggested driver hpijs. That's it, a LaserJet-4050 icon appears next to the New Printer icon; right-clicking on it and selecting Properties should enable you to set page size etc. Then printing a Test Page should work.

Afterthought: type "sudo route" and check that there is a route to the printer...

---

