---
title: "NIC Loses Link?"
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by hemi0539 on 2012-03-19
Quick question, just got Ubuntu Serer 11.10 running on my pc after testing it with VM ware for the past month.  I use it for my home file server and media server.  its running on a AMD tower pc, bought the motherboard and chip at Fry's in 2009, runs good.  

One issue, i have a on-board NIC (10/100) & and a gigabit PCI NIC.  I want to use the gigabit since its faster to transfer files over my home network and all my pc's have gigabit interfaces as well as the infrastructure.  Today when i installed Ubuntu server, the setup found both interfaces, eth0 & eth1, but was only able to get a DHCP address on the 10/100 built in NIC, i went forward with the install.

Then i was messing around a little with it and plugged in my ethernet cord into the gigabit adapter and i get link, but on the console, as soon as the system loads, the link light goes off, but when i plug into the built in NIC, it works fine.  i tried a different gigbit NIC i had laying around, and different PCI slot, as well as reset my bios (for the hell of it), and still no link after Ubuntu loads.  Ifconfig -a shows both interfaces, but obviously a ip on the built in NIC only.

What would cause this, and how could i fix it?  I wonder if anybody has had this issue.  I searched around for a little and diidnt find any links troubleshoot and/ or fix.

let me know if you need more details, love the OS, works great.

---

