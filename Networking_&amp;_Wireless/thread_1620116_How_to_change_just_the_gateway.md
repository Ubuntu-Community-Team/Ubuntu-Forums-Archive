---
title: "How to change just the gateway?"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by jmvbxx on 2010-11-12
My work has recently made major changes to their wireless network.  All workstations are Windows 7 Enterprise and the wireless access is with DHCP but the gateway is being input manually (in this case 192.168.20.253 via Properties - Advanced - Default Gateway).  

My problem is that I cannot figure out how to set just the gateway (just for that one connection) in ubuntu without also having to input an IP address and netmask.

Thank you in advance!

---

### Post by uncaspi on 2010-11-12
Open a terminal and issue the following command
sudo /sbin/route add default gw <you gateway ip> eth0
eth0 is the card. If it's a wireless card it could be eth1,wlan0,wifi0 or ra0

---

### Post by jmvbxx on 2010-11-12
@unicaspi .. If I follow your solution don't I then have to reset it back when I come home from work everyday?

---

### Post by uncaspi on 2010-11-13
You can delete the route with sudo /sbin/route del default

If you want the route to load at every boot you must put the commands in /etc/rc.local
without sudo.

---

### Post by jmvbxx on 2010-11-13
This is one of the few times where I've seen the Microsoft solution to be better than the Linux.  In Win7 you can set network settings for each individual wireless connection which allows me to set-and-forget with my computer connecting properly regardless whether I'm at home or at work.

Thank you for your advice.  For now I'll set a small script to run depending on whether I am at home or at work.

---

### Post by grahammechanical on 2010-11-13
You can add a connection so that you can connect to different wireless access points. If both are set to Automatically Connect then whichever one is in range will be logged onto. Right click the icon. Select Edit Connections. Select the Wireless tab and click Add.

regards.

---

