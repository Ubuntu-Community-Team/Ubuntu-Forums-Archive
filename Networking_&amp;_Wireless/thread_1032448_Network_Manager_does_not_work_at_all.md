---
title: "Network Manager does not work at all?"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by firsttimeuser on 2009-01-06
Hi, i have had this problem for a while I have never been able to figure out what is wrong with my "network manager applet". 

I have one ethernet and one wireless on my laptop, and here is the problem

It appears that Network manager has never been able to detect any kind of wireless router, it just shows nothing, every time I have to manually setup the /etc/network/interface file, put the following into the file, 
"
iface eth1 inet dhcp
wireless-mode Managed
wireless-essid nameoftheconnection
"
and do a "ifup eth1" then can I use the wireless connection.

Also for ethernet interface, the situation is same, i have to fire up 
"
sudo ifconfig eth0 a.b.c.d netmask 255.255.255.0
sudo route add default gw a.b.c.1 eth0
"

and then I will be able to use the network.

And no matter what I do, i see nothing in the "network manager" applet, as you can see in the attached pic, am I supposed to see something in the connection window?

And 10 minutes ago i installed pptp-linux and network-manager-pptp, in hoping I can use PPTP to connect to a microsoft VPN server, and after i restarted the network service, i see nothing in the "Network manager" applet, although I was told i should see a new "VPN Connections " as an option.

:confused::confused::confused:

---

