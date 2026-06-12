---
title: "Problem with Tp Link TL-WN727N usb Adaptor"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by r3load on 2010-12-14
hi,

i am new here, 2 days before i bought a usb wireless adapter Tp Link TL-WN727N for connecting my desktop system with wireless router.

but i am facing problem in it, i am using 10.4 ubuntu, when i plugged my device it shows that it connect to the router, i got full 100% signal strength as well, but i am unable to use internet neither i am able to connect my router through its ip, i have no idea how to get rid of this problem.

need help from the experts here. 

regards,

Mazin Jawaid.

---

### Post by gordintoronto on 2010-12-14
Is it a DHCP connection? Might be a DNS problem, can you post output of:
cat /etc/resolv.conf

---

### Post by r3load on 2010-12-15
> **gordintoronto said:**
> Is it a DHCP connection? Might be a DNS problem, can you post output of:
cat /etc/resolv.conf


is it a terminal command ? how can i use it, i do not have any idea, kindly tell me .

---

### Post by r3load on 2010-12-15
[SIZE=4][B]ok folks i have made it, here is the most simple solution for the problem

just to the terminal write the following command

[COLOR=DarkRed]sudo gedit /etc/modprobe.d/blacklist.conf
[/COLOR]
terminal will ask for the password after this command provide ur password 

then a txt file will be open.. scroll down the file go to in the end write

[COLOR=DarkRed]blacklist rt2800usb[/COLOR]

and saved it.

Reboot your System, plug in your wireless adapter, click on the network indicator on top right near by clock, your wireless connected should be visible now, click on it, provide the network key if u have and enjoy. :)

i have tried it on 9.10, and 10.4. Cheers ... :D

Regards.

Mazin Jawaid[/B][/SIZE]

---

### Post by r3load on 2010-12-16
Solved ...!

---

