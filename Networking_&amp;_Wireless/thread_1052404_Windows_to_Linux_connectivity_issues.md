---
title: "Windows to Linux connectivity issues"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by ally_uk on 2009-01-27
Hello Guys I am having some issues getting Linux and Windows to talk to each other.

Currently I am running XP Home on one Machine and I have a ubuntu setup. Previously when I was using DHCP on the Linux Machine I could connect from Windows to Linux using SSH via Putty. 

I have configured a static I.P on the Linux box by editing etc/network/interfaces and since I have done this I am unable to ping the Linux box or access it via Windows.

Those are the Windows Settings

IP Address - 192.168.1.66
Subnet Mask - 255.255.255.0
D/F GW - 192.168.1.254
DNS - 192.168.1.254


Linux I.P Settings

Iface eth0 inet static

address 192.168.1.64
netmask 255.255.255.0
Broadcast 192.168.1.255
gateway 192.168.1.254

As I said previously DCHP on the Linux machines worked fine and I could access the Linux box from Putty via windows. Since I have tried to configure a Static I.P things have started to go wrong.

Windows Firewall is disabled any troubleshooting steps?

Thank you guys

---

### Post by Iowan on 2009-01-27
Static IP's with Network Manager *can* be problematic. [Here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is a method of setting up static address via Network Manager, and a [workaround]("http://ubuntuforums.org/showthread.php?t=974382").
Finally, a [proposal]("http://ubuntuforums.org/showthread.php?p=6623406#post6623406")  proposal to remove NM and re-install the old manager.

---

### Post by ally_uk on 2009-01-28
This has been resolved God knows what I did I erased the /etc/network interfaces file and configured the settings via the gui and it worked. Very strange indeed.

Both machines can ping each other, I have edited the hosts file on both machines so I can now ping by hostname and connect by hostname.

And I have setup my first Samba config and it's all working :) 

I'm pretty tired today though stayed up way to late last night lol

---

