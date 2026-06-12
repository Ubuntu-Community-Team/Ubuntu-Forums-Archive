---
title: "Network Mangager Help"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by jwsicomputing on 2012-03-22
Hello,

Currently this is my internet setup - Satellite modem which then leads to the ubuntu machine with 2 network cards (one going in from the modem and the other for the WAN network for the rest of my machines) the WAN port then leads to a switch.

Network manager currently assigns an ip address to the machines connected to the switch with DHCP. But the only problem is that i keep on have to reboot every 3 hours because the speed of the connection to the machines gets slower and slower until it stops completely. However when i reboot the machine all is fine again. And to prove it isnt the internet the ubuntu machine is able to access the internet fine at all times.

Any suggestions???

Many Thanks,
James

---

### Post by gordintoronto on 2012-03-22
I can't solve your problem, but you might be able to Google it with the correct terminology.

WAN = Wide area network. From your Ubuntu machine to the rest of the world is the WAN connection.
LAN = Local area network. Everything on your premises is a LAN.

What version of Ubuntu? How much memory? Do you ever open a terminal and run top to see what's happening? If a program has a memory leak, the computer uses the swap file more and more, and everything grinds to a halt.

---

### Post by jonobr on 2012-03-22
HI there

Hope I dont sound like a bit of a geek here, but I just want to add a bit more onto what gordintoronto is saying.
The difference between Wan and Lan is not only on naming convention only but typically implies connection technology associated with that interface.

Its important as if your connecting LAN into something marked as a WAN port , there could be an issue there.



All that being said this sounds as if you may need to take another machine and compare against your ubuntu box or your setup as from what your saying it almost sounds like your using a WAN port for a LAN application.

---

### Post by Cheesehead on 2012-03-22
When it's slow, run the 'top' command to see if any process is hogging CPU or RAM. If so, post the result here.

---

