---
title: "static IP randomly changed by DHCP?"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by dp1228 on 2009-12-12
I just set up ubuntu 9.10 server (64-bit) on an MSI Wind barebones system and am running into a very weird problem with the network configuration.  I edited /etc/network/interfaces to have a static IP...

auto eth0
iface eth0 inet static
 address 192.168.1.100
 netmask, network, broadcast, gateway, etc

After restarting the network adapter, everything seems to work fine for about 12 hours or so.  Then, I lose my SSH and webmin access and log into my router to find out that my linux server now has an IP address of 192.168.1.204 which is in the DHCP pool.

Obviously, I can't have the IP changing randomly on me and I really thought I had this set up correctly.  Any troubleshooting suggestions?  It just really confuses me why the NIC would take a DHCP address when the config file is set up for a static IP.

Well, I just thought of one thing to try.  I will power down the server, release the DHCP lease on my router, then power up the server.  I'll let post back with the results.

---

### Post by Mski35 on 2009-12-12
Make sure there isn't any other network manager controlling the state of the interface.  Tehn make sure you have the followng entries added to /etc/network/interfaces:

auto lo eth0
iface lo inet loopback
iface eth0 inet static
address 192.168.1.100
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx(enter gateway ip here)

Also make sure you add your dns servers to your /etc/resolv.conf file as follows:

nameserver xxx.xxx.xxx.xxx(enter your dns server ip)
nameserver xxx.xxx.xxx.xxx(enter your alt dns server ip)

---

### Post by dp1228 on 2009-12-12
Thanks for the quick reply :-)  I am pretty sure that there is no other network manager on my system.  I installed a pretty minimal system - ubuntu 9.10 server w/SSH as the only extra software at installation time.  I've been using webmin and SSH for managing the system.

Is there a quick way to determine what network managers are on the system?  On a different topic, the conflicts that seem to arise between different network managers on the linux desktop distros has always been frustrating to me.

Unfortunately, I seem to have bigger problems now :-(  Some of my partitions are not mounting and I cannot boot the system.  I think it has to do with ACL.  I'll need to see if I can repair it with the Live CD before getting back to the IP issue.  I'll have to deal with it all later to keep on the good side of my wife though!

---

### Post by dp1228 on 2009-12-14
Pretty sure I have this solved, or at least solved enough.  My server was behind a wireless bridge on my network.  Both the bridge and my router are running dd-wrt v24 sp1.  I think the odd behavior might be because of the router and bridge.

For some reason, it appears the wlan adapter on the bridge was being assigned the IP intended for my server (?).  The server would boot up with the correct IP as indicated by ifconfig and I could log into webmin using the correct IP.  However, the server showed up with an incorrect IP assigned by DHCP when I logged into my router admin page.  Eventually, the server actually would obtain this incorrect IP address.  This happened even after deleting the DHCP lease and power cycling the router, bridge, and server.

I moved the server to one of my router's LAN ports, power cycled everything, and it seems to be working perfectly now.

Just a quick note about the non-mountable drive configuration I had, since it might help another noob like me.  After installing ACL (access control lists) on my server, I edited /etc/fstab incorrectly.  I accidentally set the /var partition privileges as "rwx" which is not valid.  The privileges can only be "rw" in the fstab configuration file.  If you think about it, that really makes sense.  You only read from or write to partitions, not execute them.

---

### Post by lisati on 2009-12-14
As an alternative, I wish to respectfully suggest that you let your router assign IP addresses to specific machines if possible, rather than trying to mess around doing it from your computer's end. That way, if you connect your machine, even temporarily, to another network, you are less likely to run into possible conflicts.

---

### Post by dp1228 on 2009-12-15
Good suggestion lisati.  I had some trouble setting static IPs in the past but just figured out how boneheaded I was being tonight.  I kept hitting "Apply" without hitting "Save".  The solution was as simple as hitting "Save" first!

Anyway, I have now set up a static lease on the router for the server.  I plan on keeping the static setup on the server configuration as well.

Thanks!

---

