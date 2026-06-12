---
title: "Please help! Lost ping and network!"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Skavenger0 on 2008-12-21
Ok this is bizzar.

Everything was working fine yesterday and I havnt changed anything except a apt-get update and installed a couple of emulators.

The computer im on now is WinXP connected via exactly the network through a single router and its fine.

My ubuntu install on a seperate PC is saying its connected to the network and has aquired the DHCP address. It has a wiFi and 2 network cards. Ive tried all three and get exactly the same.

Im running ubuntu 8.10, kernel 2.6.27-10-generic
I have turned off all firewalls.
I have added ALL:ALL to ubuntus allow list. Ive tried googling for hours.

I cannot pull any sites up or get any app to connect to the internet. I also cant ping anything as I get.

Ping: Sendmsg: Operation Not permitted

I am using root access via "sudo su".

I need help?

---

### Post by Skavenger0 on 2008-12-21
Tried ubuntu to auto reconfigure and nothing works. 

Cannot even access the router.

DHCP enabled but according to ubuntu its all fine and has been given an address

IFconfig looks normal however the network card has only sent data and not recieved any.

Could the kernel be responsible for this somehow or could it be an access right.

Ive added myself to the root group and still nothing

---

### Post by Skavenger0 on 2008-12-21
Could it be possible that tcp 192.168.1.2 (me) is not listening?

If so how could i check/fix

---

### Post by Skavenger0 on 2008-12-21
Ive also tried disabling all but on interface.

Im surprised that even the wireless doesnt work.

Im 100% sure this is not a harware issue.

---

### Post by Skavenger0 on 2008-12-21
i did think it had somthing to do with iptables but I think ive managed to bypass or clear them but it still doesnt work.

---

### Post by Iowan on 2008-12-21
What IP address(es) are in use? What does the XP machine have, and what is on the Ubuntu machine (192.168.1.2 is on which interface - and what's on the others)? The router (DHCP server) is on 192.168.1.1?

---

### Post by Skavenger0 on 2009-01-03
I found the fix after re-formatting damn it. It seems to have been a conflict somewhere between GNOME and KDE

---

