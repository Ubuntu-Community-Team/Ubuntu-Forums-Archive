---
title: "Network monitor for Ubuntu/Windows"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by RedPandaFox on 2009-09-04
Ok, so for the 4th month in a row I have been blamed for exceeding out download limit at home, noone seems to believe im not using all the download. 

I need a program that will moitor the network trafic on all computers on the network, and tell me what computer is taking up all the downloads.

I know its not me taking the limit up as for the first 4 days of the month I left my computer disconnected from the internet and all of a sudden people start leaving me notes on my desk blaming me for 4gb gone missing already. 
I have feeling it is someone leaching the wireless, but every time I change the security, it keeps happening.

I know there are programs out there that do what I need, but most i know of you have to pay for. Is there anything out there that will monitor Linux, XP and W7 traffic and report who is using what?

---

### Post by callan79 on 2009-09-04
> **RedPandaFox said:**
> Ok, so for the 4th month in a row I have been blamed for exceeding out download limit at home, noone seems to believe im not using all the download. 

I need a program that will moitor the network trafic on all computers on the network, and tell me what computer is taking up all the downloads.



Hi RedPandaFox,

I was about to write and tell you to install vnstat, but someone's already written about it at [http://ubuntuforums.org/showthread.php?t=1089331](http://ubuntuforums.org/showthread.php?t=1089331)

Either way, vnstat only works on your machine.

For a windows machine, try NetStat Live from [www.analogx.com](http://www.analogx.com)

If you wanted to proper monitoring you really need one of two options :

1. Transparent Proxy - sits in between your Internet and your Network. It logs everythng and can generate reports. Probably needs a dedicated computer.

2. A managed network switch - this sits on your network and counts data. It won't tell you WHAT is being done, but it will tell you how much data each computer has done. The problem - it counts ALL network traffic, so if you transfer a file from one computer to another, it'll count.

So a proxy is the best, but if you just want to count how much YOU are doing, vnstat may work fine.

Cheers
CD

---

### Post by Grenage on 2009-09-04
If you have a spare machine anywhere, install something like pfsense on it, connect it to your router, then use that as your firewall.  You can list traffic volume by IP etc.

---

### Post by RedPandaFox on 2009-09-04
Well it seems that running something between the router and everyone is the way to go, so what, I hook the modem to the system, then to the wifi router?

I have enough spare parts to throw something together, problem being, the modem and router are on the kitchen bench, I dont think that will go down to well having something big there.

I got a program when I bought the router, it was Cisco Network Magic, and its just the thing I want, you install it to on a computer, it gathers info from the router, then monthly it emails you a report on who did what. Only problem is, it tells you every site every user visited...

Not everyone is to wrapped about someone having access to every website you visit... Also you have to pay for the network magic software

---

### Post by Grenage on 2009-09-04
It's possible you ran get the information via SNMP polling, but I've never used it for that purpose.  Can the router be moved?

---

### Post by RedPandaFox on 2009-09-04
Router is in the only spot to get reception to everyone, 3 computers in the house and 2 in the flat 20m away, no way it can be moved

---

### Post by Grenage on 2009-09-04
I'd tell them it1s not you, and if they still refute it, they can accept the machine by the router or shut up.

Not that the machine has to be by the router, a cable simply has to connect them.

---

