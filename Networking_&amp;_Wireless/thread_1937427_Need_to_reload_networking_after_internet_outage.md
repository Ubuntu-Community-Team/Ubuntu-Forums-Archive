---
title: "Need to reload networking after internet outage"
date: 2012-03-07
forum: Networking &amp; Wireless
---

### Post by Hulkiedulkie on 2012-03-07
My cable ISP has short outages every few days (2 to 15 minutes usually). Not a big deal really. After such an outage I need to reload networking in order to regain acces to internet. LAN connectivity is still intact. The interface keeps the same ip-adres during and after the outage but there is no connectivity.
 
My PC (ubuntu server 11.10) is connected directly to the modem and gets an external ip-adress through DHCP (always the same ip).
 
Syslog shows no errors.
 
It's not a DNS-problem. I can't even ping/tracerout to the outside world.
 
My /etc/network/interfaces:
 
```

# The loopback network interface
auto lo
iface lo inet loopback
 
# external interface 
# 192.168.100.2 is for logging into the modem
# ip of eth1 is 77.250.1.xxx
auto eth1 eth1:1
iface eth1 inet dhcp
iface eth1:1 inet static
address 192.168.100.2
network 192.168.100.0
netmask 255.255.255.0
broadcast 192.168.100.255
 
# LAN interfaces
auto eth0
iface eth0 inet manual
 
auto wlan0
iface wlan0 inet manual
 
auto br0
iface br0 inet static
address 10.0.0.1
network 10.0.0.0
netmask 255.255.255.0
broadcast 10.0.0.255
bridge-ports eth0 wlan0
```
 
Network-related packages I use:
- linux-igd
- bridge-utils
- hostapd
- isc-dhcp-server
 
Any thoughts?

---

### Post by lensman3 on 2012-03-07
This is what I use.  It pings my DHCP default gateway, but you could use google for that matter.  If there are no return pings then, it shuts down the current ethernet and reloads it.   I load this in the root cron and it runs every minute.  This runs now on a Fedora machine, but should work anywhere.

My crontab line is:
```
* *   * * * /usr/local/bin/keepalive.sh 2>&1 /dev/null
```

```
#!/bin/sh

ETH1=eth0

if [ -f /var/run/dhclient-$ETH1.pid ] ; then

 ping -c4 -l3 zzz.yyy.xxx.w  2>&1 | grep "0 received" > /dev/null && \
  { /sbin/ifdown $ETH1 > /dev/null; sleep 2; /sbin/ifup $ETH1; }
else
  /sbin/ifdown $ETH1;
  sleep 2;
  /sbin/ifup $ETH1;
fi

```

One gotcha with this  code, and I have done it to myself.  If the network goes down and you are not around to fix it, you can spawn a lot of processes that get eventually hang the system.  After a while you can run out of processes to the extent you won't be able to log on to kill the runaway processes.....

I call this script keepalive.sh and it lives in /usr/local/bin.

(This is not my original code, I got it from somewhere too.)

Good luck.

---

### Post by Hulkiedulkie on 2012-03-07
Thanks for your help.
 
Your script is a decent solution but I'd prefer finding the root cause and doing something about that.
 
Is there maybe some sort of internal timeout where if the computer can't reach a certain subnet for a few minutes it will just stop trying? And can I lift/prolong that timeout?

---

### Post by siloko on 2012-03-08
Hi,

This appears the same/similar problem as I am having and as reported here:

[http://ubuntuforums.org/showthread.php?t=1936533](http://ubuntuforums.org/showthread.php?t=1936533)

I have tried a number of things, none works. I have still to swap out the router but I am reasonably confident that is not the problem, although I will try it tonight. I have never had reconnection problems before and I have certainly not had to use a script to ping the gateway . . .

Interested if you find a solution - but for me this is a new issue for 11.10 . . .

Cheers

S

---

