---
title: "How do I setup a static IP on eth0?"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by C.A.G. on 2009-11-26
Hi,
I have been searching for an howto on making A static IP address.  I want to enable port fowarding on my router but I have to have a static IP address to do so.  If anyone can point me to A howto that would be great!

I have a Dell Mini 9 running Karmic.  The wireless card is set as eth0.

Thanks in advance guys!

---

### Post by lisati on 2009-11-26
I generally let my routers set the IP addresses on my network. Both (one by Thomson, the other by Netgear) are able to assign a specific static address to a particular machine.
As for doing it from the computer end, I defer to the wisdom of other users who might have actually done it.

---

### Post by mhgsys on 2009-11-26
On the right of the top panel, you see the pic of the 2 computers right?

Right click it , edit connections. 

Go to wireless> auto "name network"/ wlan0 > click edit > IPv4 Settings > method > manual: and fill in a ip adres f.e 192.168.1.10 > netmask=255.255.255.0  
Gateway your gateway / routeradress

Dns servers will be found in the router settings. 
use a , to divide the primary and secondary dns

---

### Post by C.A.G. on 2009-11-26
What should my gateway be?  I think my default wireless is actually eth1, is this a problem?

---

### Post by mhgsys on 2009-11-26
Your gateway should be your router adress.



edit;
 eth0 or eth1 or wlan0 (what's probably the wireless lan)  / whatever you want to configure. it should not be a problem to assign a static ip.

---

### Post by Iowan on 2009-11-26
For port-forwarding to work, you need to have an address that doesn't change... a static lease (as suggested by **lisati**) should work as well as a static address (configured either in Network Manager or */etc/network/interfaces*). What are you using for DHCP server - and do you have access to its configuration?

---

### Post by C.A.G. on 2009-11-28
Thanks guys!  I think I have it figured out.  Thanks for the responses. How do I mark this thread as resolved?

---

### Post by Iowan on 2009-11-28
Look under Thread Tools

---

