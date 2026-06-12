---
title: "Ethernet preventing wifi internet access"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by njparton on 2010-05-29
I've just installed lucid and I'm configuring all the settings I need.

I have 2 network interfaces on my PC, ethernet (eth0) and wireless (wlan0).

eth0 (192.168.2.2) is connected to a switch and then a NAS device (192.168.2.10) - there is no route to the internet this way.

wlan0 (192.168.1.2) is connected to my wireless router (192.168.1.1) and the internet can be accessed this way.

The problem is when I have both active I can't access the internet at all.  When I disable eth0 evertyhing works fine.   So the question is how to I configure the eth0 connection to make it clear that it's not a route to the internet and/or just to access 192.168.2.x addresses only?

---

### Post by Iowan on 2010-05-29
Does your Network Manager settings for eth0 have an option to "Use this connection only for resources on its network"?

---

### Post by valbarcinal on 2010-05-29
I have the same problem, i can connect with WIRE connection but not with WIRELESS connection. How can i configure to connect with wireless or wifi connection.

---

### Post by docbrown on 2010-05-29
I have a similar issue also, on 10.04 lucid.

eth0 = 10.1.2.2 connected to readynas duo = 10.1.2.3
wlan0 = 10.1.1.9 connected to wireless router = 10.1.1.1

I have attempted to configure a route using the "network connections" gui  
Images of my settings for eth0 "wired" are attached below.
I've only guessed what i need to add in each field in the "route" section, so please forgive my ignorance!

I am able to connect both eth0 and wlan0 simultaneously and can connect to the internet via gateway 10.1.1.1, however cannot connect to the rest of the wireless local network that is in subnet 10.1.1.* . However, once i disconnect eth0, i am able to connect to other computers my local network again. 

I also cannot use the "shared to other computers" method in IPv4 settings as a static ip is required for both the computer and the readynas, so they can be connected directly.

Is it possible to have the readynas accessed by other computers in subnet 10.1.1.* wireless network? Even if the ip address is 10.1.2.3 if the routing is configured correctly? Or is bridge required for this situation?

It seems the way to configure this is through /etc/network/interfaces rather than the gui, but i am a little hesitant in adding anything that would break my current internet connection. So would really appreciate any help on what i should put in there.

Thanks!

---

### Post by njparton on 2010-05-30
I think you're correct about having to edit /etc/network/interfaces but I'm not sure to what degree that file is used anymore?

My NAS runs debian lenny so I'm familiar with the basic settings in that file.  But if it's no longer used (?) then this isn't a trivial fix.

---

