---
title: "connected to network, but no internet"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by rose34 on 2009-06-07
Hi Everyone,

I am having some trouble with my Ubuntu 9.04 installation. I had my computer at university, where it worked fine on a wireless network. However, I have now brought it home and am having trouble getting onto the internet with it. It says it has connected to the network, but no web pages will load, no downloads will work... it has worked briefly for a couple of minutes, but then stopped. 

I have an idea there might be an IP address issue with other windows computers on the network, but I've tried setting all the addresses manually and that doesn't seem to work. Can anyone suggest what I might try next?

I know it's not the wireless adapter, as that was working fine at uni and nothing's changed there. The router I'm using is a Netgear DG834G v4, the ISP is AOL unfortunately, but none of the windows computers on the network need the AOL software to connect, so I assume it should be fine on ubuntu as well?

Cheers,
Joe

---

### Post by Bucky Ball on 2009-06-07
Should be. Is the router also DHCP server? If so, make sure you are not setting an IP on the machine while the router is trying to serve you one. You need to go to System->Admin->Network, unlock and check properties for your wireless and make sure you have the Configuration = Automatic Configuration (DHCP). 

Anyhow, just make sure there is nothing in there and 'Enable Roaming' is unchecked.

---

### Post by Iowan on 2009-06-07
I haven't found "Enable Roaming" on 9.04. 
After you put the settings back to DHCP, try pinging the router and/or one of the other computers by IP address and by name.

---

### Post by rose34 on 2009-06-07
The setting is Automatic DCHP, I have tried pinging the router while connected to the network and get the following reply:

> joe@joe-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=1 Destination Host Unreachable
From 192.168.0.3 icmp_seq=2 Destination Host Unreachable
From 192.168.0.3 icmp_seq=3 Destination Host Unreachable
From 192.168.0.3 icmp_seq=5 Destination Host Unreachable
From 192.168.0.3 icmp_seq=6 Destination Host Unreachable


I'm not really sure what this means, any ideas?

Thanks a lot,
Joe

---

### Post by Iowan on 2009-06-07
Interesting... What are results of **route -n**?
BTW, did you restart networking and/or Netowrk Manager after changing settings?

---

### Post by Bucky Ball on 2009-06-07
Are your network name (ESSID) and WEP key the same on your computer as they are in your router? You need to make sure they match.

This can be found in System->Admin->Network and check your wireless properties. Check your router config to make sure you get the details correct. If you have none set, set them. The router (AP - Access Point) needs a name and a security code. Some routers have a factory-set WEP key on the bottom of the unit, most you can choose your own.

---

### Post by superprash2003 on 2009-06-08
also post output of **ifconfig** from  the terminal

---

