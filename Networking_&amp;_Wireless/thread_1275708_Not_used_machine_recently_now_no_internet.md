---
title: "Not used machine recently now no internet"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by jtreg on 2009-09-26
Hi, I have Ubuntu 8.1 and was using this machine up to 6 weeks ago. I recently returned to the machine and I cannot connect to the network - I can see the network (called MSHOME) and my own machine. I cannot connect to the internet or to other machines. My router has one XP machine connected to it and the XP machine is fine, connected to internet ok.

I have been using the same machine hardware for 6 weeks as XP Professional machine quite happily and I swapped back the drive to use my (originally working Ubuntu) drive. I use dynamic allocation of IP address setting with my BT router.

Not sure why the Ubuntu machine has stopped connecting to other machines and internet... please can you suggest what I can check?

Thanks!

---

### Post by Iowan on 2009-09-26
Start with **ifconfig -a** to see if machine has an IP address.

---

### Post by jtreg on 2009-09-26
yes under
eth0:avahi Link encap:Ethernet .... etc...

inet addr:169.254.6.162

---

### Post by Roasted on 2009-09-26
169.254.X.X IP addresses aren't valid. That's typically what network devices that don't have DHCP capabilities give out.

Example - I image computers with my laptop - to 24 port switch - to computers. If my laptop isn't plugged in (which is the DHCP server), the computers I'm plugged in to grab 169.254.X.X IP addresses which aren't valid for external access.

Can you give us a little more information?

If you run "sudo /etc/init.d/networking restart" does it fix your problem?

If not, are you running network manager? Is network manager set to DHCP for your wired connection? Can you run "nano /etc/network/interfaces" and paste the contents here?

---

### Post by j7%&lt;RmUg on 2009-09-26
169.254 is an APIPA address, APIPA is used when DHCP is unavailable.

---

### Post by Iowan on 2009-09-26
If you have been using the machine for the past 6 weeks as XP machine, then it should be safe to assume that the cable, card, and router port are working, otherwise, that'd be the next things to check.

---

### Post by jtreg on 2009-09-27
I get :

james@valis:~$ sudo /etc/init.d/networking restart
[sudo] password for james: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4063
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1f:d0:08:8b:86
Sending on   LPF/eth0/00:1f:d0:08:8b:86
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1f:d0:08:8b:86
Sending on   LPF/eth0/00:1f:d0:08:8b:86
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

---

