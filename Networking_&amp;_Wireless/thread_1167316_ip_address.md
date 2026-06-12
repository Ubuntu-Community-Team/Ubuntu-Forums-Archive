---
title: "ip address"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by hero1900 on 2009-05-22
when i check the ip address in terminal i got that i have a 10.0.0.1 but the problem is i am not connected to router or local lan, i am connected directly to INTERNET so i have to take the ip from ISP and that is the one that i have to see by ifconfig. i did install DHCP server (to try some stuff) but i did remove it. so what is this problem??

---

### Post by Iowan on 2009-05-22
What is your router address? I'm curious/confused how you get an IP address via DHCP without a DHCP server... although some setups remember/use their last valid IP address.

---

### Post by helgman on 2009-05-22
If it is the way you describe above and you can surf the web with that address ... congratulations, your ISP uses some weird IP setup ... if you, on the other hand, can't surf the net then your might need to change your setup.

Just for the record - you only have ONE network interface?

You could try to get a new lease from your ISP (if your connected to them), something like ```
dhclient ethX
``` (or whatever your NIC is at). This will let you see the whole discovery/offer process.

And ```
route -n
``` might give you some clue as to where your packages go when they are not destined for the LAN.

Regards,
Helgman

---

