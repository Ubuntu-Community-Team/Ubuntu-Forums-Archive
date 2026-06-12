---
title: "No IP adress -Dapper"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by ElderLars on 2006-05-09
I upgraded my working Brezy to Dapper. But when was logged in i couldent reach internet. Network problem that is. I found the guide in this forum and folowed it step by step:

Lars: sudo mii-tool
eth0: negotiated 100baseTx-FD, link ok

Lars: ifconfig eth0
Link encap: Ethernet             HWaddr: Yadyadyada
inet6 addr: blablabla             scope:link
UPBROADCAST RUNNING MULTICAST
...more...

Lars:lspci | grep Eth
0000:00:0b.0 Ethernet controller: Davidcom Semiconductor, inc. 21x4x DEC-Tulip compatible 10/100 Ethernet(rev 40)

Lars:lsmod | grep mii
no anser

Lars: sudo modprobe tulip

after I have tried all this it no differense
I tried with Sodo ifconfig eth0 up.

Do you have any idea?

---

### Post by louis_nichols on 2006-05-09
Did you use System>Administration>Networking to set your connections properties: IP, netmask, gateway, DNS?... That's the first thing you should do.

---

### Post by ElderLars on 2006-05-11
In the folder i got from my ISP they have an help for windows. They say i should mark the Get ip-adress automatic and the get adress to DNS automatic.
And i didnt find any simmilar in Ubuntu.
So i have no exact adress to my DNS.

---

### Post by louis_nichols on 2006-05-11
Oh! This is a typical example of how windows keeps people in the dark about what's going on behind the GUI. :)

What windows calls "obtain IP address automatically", Ubuntu (and pretty much all linux distros) calls "obtain IP address through [DHCP]("http://en.wikipedia.org/wiki/DHCP")". :) So, at the network administration screen, choose the connection to your ISP, click properties and, where it says "configuration", choose dhcp from the drop-down. Then just activate the connection and you should be good to go.

---

### Post by ElderLars on 2006-05-12
I tried that. I marked it, unmarked it. inactivated the Card. activated the card but no differense.

I found in the networking-tool(I use swedish Ubuntu so the names might be wrong) under the tab Units, some information.

Ip-information:
blablabla         Not available
blablabla         Not available
and so on.

"Gui information"(Gränssnitsinformation - swe)
not available 

But under the "gui statistiks" i found something hapens.
Sending bytes:  5,3Kb
Sending pakets: 16
Sending errors: 1     ----not good?

received bytes:  256 +counting
received pakets: 4500 +counting

"lsmod | grep mii" i dont get any anser. Shouldnt i get that?

---

### Post by mips on 2006-05-12
ElderLars,

There are know issues with the Tulip chipsets. Don't dispair as there is a solution somewhere here that I read but can't exactly remember.

Could I suggest you search for 'tulip' in the Networking & Dapper forums as the solution is in a thread here somewhere.

---

