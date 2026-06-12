---
title: "Live CD + router disconnect - Auto eth0 fails to reconnect"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by lotuseclat79 on 2009-03-20
I am using the Intrepid Ibex Ubuntu 8.10 Live CD as my base environment.

The /etc/network/interfaces file contains:
auto lo
iface lo inet loopback

When I disable my wired network connection (optical router) by right-clicking on the network icon on the system menu at the top of my screen, I suspect that there might be a timeout on how long the router tolerates being disabled and this probably results in the router disconnecting from the host OS (Live CD) environment after some time (I have not measured how much), although I suppose I should log into my router and poke around to see if there is such a setting - and if that is the case avoid the problem by resetting the timeout period (if possible).

Right-clicking the network icon to re-enable or establish a new connection does not work.  The router uses DHCP.

I tried sudo /etc/init.d/networking restart
and that also did not work.

I also tried to power-off and power-on my router, but that also did not work intermittently, sometimes it did as I recall.

The only way I have been able to re-establish a connection otherrwise with the router is to reboot my Live CD environment, and if the router has been powered on, I can get a connection back.

My typical procedure is to reboot with the router powered down, and when my Live CD environment is re-established, then to power up the router - which also works (99% of the time).

Is there a way to re-connect the host OS to the router after the connection has been dropped, by using some other commands on the command line without having to reboot?

Thanks,

-- Tom

---

### Post by wmatthews on 2009-03-20
It seems like everyone is having this problem.  When there is more than one computer accessing the internet.  My nic that is connected to my DSL will just die out on me.  If I find a solution I will let you know.  

I think if you unload the module for the card with "rmmod" and then load it again with "modprobe", bring the interface back up with "sudo ifup eth0".

I would do that but I can't figure out for the life of me what module my card is using.

---

### Post by jediknight64 on 2009-03-21
I have an Acer Aspire 5335-2238 with built in Acer Nplify 802.11 b/g/Draft-N WLAN. I purchased this with a Belkin N Wireless Router. I installed Ubuntu 8.10 as a secondary boot option to Windows. Wireless is no problem in Windows, but if I boot in Ubuntu I have no internet. My Network Manager doesn't list "Wireless Network" when I click on it.
  I am new to Linux, and I will not let this thing beat me!

---

### Post by lotuseclat79 on 2009-03-25
Hi folks,

After experimenting with looking through the /etc/rc[n].d files, after the same problem happened again today, I was able to successfully bring up the network connection to my optical router with the following steps:

1) /etc/init.d/networking start<Enter> Note:restart may also work as a parameter here
root@ubuntu:~# /etc/init.d/networking start
 * Configuring network interfaces...   
2) /etc/init.d/NetworkManager restart
root@ubuntu:/etc/init.d# /etc/init.d/NetworkManager restart
 * Stopping NetworkManager...    [OK] 
 * Starting NetworkManager...    [OK]

The Auto eth0 kicked in and a connection to the router was created.

-- Tom

---

