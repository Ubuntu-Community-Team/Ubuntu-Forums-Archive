---
title: "Advanced Network Configuration"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by Maki on 2009-07-22
Hello I have problems to configure my local network over ubuntu, It works in windows but i can't do the same in ubuntu.

I have 2 ethernet adaptors one of them conected to a router and therefore internet, no problem there.
The second adaptor (gigabit) goes to a windows xp file server (gigabit too), the problem begin when I try to configure the gigabit adapter in ubuntu and get the files of windows.

Configuration in windows (actually working)

PC 1 (which im trying to configure over ubuntu)

Gigabit Adaptor: 
IP 192.168.101.101
Subnet Mask 255.255.255.0


PC 2 (Windows XP File Server)

Gigabit Adaptor: 
IP 192.168.101.100
Subnet Mask 255.255.255.0

Both pcs adapter #1 goes to router, it has IP Range 192.168.100.X

The reason of this setup is to get the file transfer via gigabit (much faster) and internet via router (only capable 100 MB/s)

It's possible to make this in ubuntu?

Thank you.

---

### Post by superprash2003 on 2009-07-22
yes , it is.. just assign these static ip's individually and first ensure that you can ping those ips

---

### Post by Maki on 2009-07-22
superprash2003 thanks for your answer. This is the problem, when I configure the gigabit adapter with static ip. I configure static ip the conection to the router, no problem here. But then I configure gigabit static ip conection the network manager just doesn't connect. No ping at all.

Thank you.

---

### Post by superprash2003 on 2009-07-23
post output of ifconfig , for the gigabit , assign 192.168.1.100 as gateway for the 192.168.1.101 machine

---

### Post by Iowan on 2009-07-23
> **Maki said:**
> ...
HPC 1 (which im trying to configure over ubuntu)

Gigabit Adaptor: 
IP 192.168.[COLOR="Red"]101[/COLOR].101
Subnet Mask 255.255.255.0


PC 2 (Windows XP File Server)

Gigabit Adaptor: 
IP 192.168.[COLOR="Red"]101[/COLOR].100
Subnet Mask 255.255.255.0

Both pcs adapter #1 goes to router, it has IP Range 192.168.[COLOR="Red"]100[/COLOR].X
...I'm probably missing the real problem, and seeing only typos...
Router is in different subnet than machines.

---

### Post by Maki on 2009-07-25
Hello guys.

I reinstalled ubuntu and therefore samba. Now the sistem is working in the same way that windows do.  It's seems my previous ubuntu was broken. 

Thanks for all.

---

