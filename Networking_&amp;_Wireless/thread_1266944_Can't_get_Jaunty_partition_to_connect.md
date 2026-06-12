---
title: "Can't get Jaunty partition to connect"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by DougieFresh4U on 2009-09-15
I run a multi boot system and I can get connected on 3 of my partitions. I ran some updates on Jaunty last week and it called for a reboot. Upon booting up Jaunty partition, Internet would not connect using ethernet. So I tried using my wireless, which has worked before and it was a no-go for wireless. Was not even showing any available to connect to. I am at a loss as I keep trying and ehto and wirless will not connect. When I go to 'Edit Connections' and click 'IPv4' tab, I choose 'manual' and enter all the correct info but the 'apply' button is not working and does not work for wireless either.
Any help would be most welcome.

---

### Post by DougieFresh4U on 2009-09-15
I tried restarting network and this is the outcome:
```
dougie@DougiesLeanMachine:~$ sudo /etc/init.d/networking restart
[sudo] password for dougie: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.pan0.pid with pid 3598
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/ce:80:66:d5:78:6e
Sending on   LPF/pan0/ce:80:66:d5:78:6e
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan1 ; No such device.
SIOCSIFADDR: No such device
wlan1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan1: ERROR while getting interface flags: No such device
Failed to bring up wlan1.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/ce:80:66:d5:78:6e
Sending on   LPF/pan0/ce:80:66:d5:78:6e
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[pan0]: waiting for interface wlan1 before doing NFS mounts
                                                                         [ OK ]
dougie@DougiesLeanMachine:~$
```

---

### Post by DougieFresh4U on 2009-09-16
I am still seeking some kind of help.
Thanks

---

