---
title: "connect both eth0 and wlan0 at same time"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by noorez on 2009-08-21
Hi...

I am currently exerimenting with the ubuntu 9.04 ltsp server installed on virtual box 2.2.4 but i'm having some networking problems.

I have setup both my cards to use static ip using the network manager. eth0 is set to 192.168.0.2 and wlan0 is set to 192.168.1.63. eth0 is for the server and wlan0 is for the internet.

For the switch used with the server I dug up my old lynksis router (WRT54GS) and disabled the dhcp server and set it to routing mode.

But..when i have the ethernet wire connected, i cannot connect to any internet site, only the lynksis configuration page and when its disconnected i have internet again. Even though the network manager shows both a wired and wireless connection.

any help with that....

---

### Post by Iowan on 2009-08-21
Network Manager only seems to manage one interface at a time.  You should be able to set up the other one (your choice?) via */etc/netowrk/interfaces*.  There is/are another thread or so about having both interfaces operational.  I'll look for it/them... unless you find it/them first...

---

### Post by noorez on 2009-08-21
I tried that...

before i edited /etc/network/interfaces it only showed the loopback interface. I then added the following entry


iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

I left wlan0 out...

this however still did not give me internet when the ethernet wire (eth0) was connected

---

### Post by noorez on 2009-08-21
i should actually note one thing...

in my first configuration i described i was able to connect to both my wireless router (serving internet) config page via 192.168.1.254 and the lynksis router (serving as the switch) via 192.168.0.1.

it was only other sites such as "www.google.com" did not work while the eth0 connection was active. As soon as i removed the ethernet cable from my laptop i had internet access again.

---

### Post by noorez on 2009-08-21
Problem solved??

First, after doing a bit of research and looking it similar problems people have had, I realized I had forgetten the 'Default Route' issue.

It seems that with network manager, when eth0 became active, the default gateway (192.168.0.1) became the default route even if it offered no internet connection.

I then followed a solution to a similar problem: put eth0 back into the interfaces file but left out the gateway line. strangely this seems to work.......

now, even though the ethernet cable is connected, network manager shows the wireless connction as the default route.....
network manager actually shows the wired connection as unmanaged...

can someone explain why this worked? especially the part of my the gateway line could be left out of the configuration?

---

