---
title: "Routing eth0 and wlan0 simultaneously?"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by slickvguy on 2009-03-28
I have a PC with both eth0 and wlan0. Both are setup properly and both work fine. What I would like to do is use both at the SAME time.

eth0 is connected to router A (ISP #1), gateway 10.0.0.1 ip 10.0.0.10
wlan0 is connected to router B (ISP #2), gateway 192.168.2.1 ip 192.168.2.10

How can I download a file using wlan0 and then use eth0 to continue to surf at the same time?

The way I do it now, is when I begin using one or the other interface, that's the one that all future communication takes place via, i.e. I have to choose one default gateway or the other.

I guess what it boils down to is: how can I setup the routing tables so that wlan0 is used for a specific destination address while all other destination addresses route through eth0? 

I've read the man, but it's a bit over my head at this point.

Thank you.

---

### Post by oobe-feisty on 2009-03-28
the answer is not as simple as some might think in short you need to configure both interfaces seperatly using /etc/network/interfaces for one device and a script for another i wouldnt consider using network manager its too buggy also the reason i mention configuring one only in /etc/network/interfaces is because in my experience and from what i have read of others experience is that it either wont work at all or one device looses its routing table and network services need to be restarted somtimes it wont work until you comment one device out. 

ok lets assume you took my advice and have one device configured using /etc/network/interfaces and the other using a script 
you then need to setup some kind of iptables rule using iptables maybe install a frontend for iptables like firestarter. or setup a squid proxy and use it like a proxy in your web browser if you want i can post back with some sample configurations for the interfaces file and sample scripts however i cant help much with iptables or squid

---

### Post by t0mc4t on 2009-03-28
Hello,

Got almost the same problem with me..
The differences is I want to use pppd (broadband) with ath0 (WiFi) in the same time.
If I connect both device, the internet connection (pppd) won't work. But the ath0 connection into internal network is still working.
Any solution in regards of this issue?
Thanks...

---

### Post by oobe-feisty on 2009-03-29
here is some sample configurations for you both bear with me i am not a networking guru this is just what works for me.


i configure eth0 ( my wired lan ) using /etc/network/interfaces like below 
```

auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
up route add default gw 192.168.0.1
```




then i use a small script that connects my wlan0 device to a different subnet 

i save the code below as /usr/local/bin/wlan then sudo chmod +x /usr/local/bin/wlan

```
#!/bin/bash
#/sbin/ifconfig wlan0 down
/sbin/iwconfig wlan0 mode Managed
#/sbin/iwconfig wlan0 key XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX
/sbin/iwconfig wlan0 ap 00:1A:70:DB:10:B7
/sbin/iwconfig wlan0 essid "linksys"
/sbin/iwconfig wlan0 commit
/sbin/ifconfig wlan0 192.168.1.10 up
/sbin/route add default gw 192.168.1.1 dev wlan0
/etc/init.d/networking restart
#/bin/ping -c 5 192.168.1.1
```


this obviously is just an example this is exactly what im using right now but an example in your cases as you will need to modify it to suit your devices and networks


if you choose to go this route ( i have tried many other methods that failed) then you will have to disable or uninstall network manager as it likes to mess with your settings and it will break things you also want to have /etc/resolv.conf configured to use your isp gateway i.e "nameserver 192.168.0.1" or your isp's real nameservers 

on boot both interfaces are connected to each seperate network on different subnets and everything works fine however i do find my wireless drops out somtimes due to buggy linksys drivers using ndiswrapper i have a script that i found on this forum to reconnect the wireless if it drops ( i run it as a cronjob ) connection pasted below.

```
#!/bin/bash
# FILENAME: /usr/bin/wirelesstest
# note the backticks in the next line
if ! `ping -c3 192.168.1.1 >/dev/null 2>&1` ; then
/usr/local/bin/wlan1
fi
#exit 0

```

wlan1 is the same as the sample script i pasted above  except it unloads and reloads ndiswrapper first before configuring wlan0 i have /etc/rc.local call /usr/local/bin/wlan ( the script above ) for the first time on system boot.


EDIT:

this is the result 

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0


as you can see both devices are on 2 subnets and perform quite well as apose to using some gui tool that would only mess things up

---

### Post by parapcros on 2010-03-11
Hi! I have a similar problem. Any help is welcome :)

I have to work with a laptop. I need to use both the wlan and ethernet. I use the wlan to connect to the internet. The ethernet is used to plug a custom FPGA with an embedded server (that's not the problem). The point

wlan gateway: 192.168.0.1
eth0 gateway: 172.16.0.1

I want to use the eth0 ONLY to connect to the FPGA's server, it means, just to pointer the browser to their ip (172.16.0.10). The rest of connections (google.com, for example) should go throw the wlan interface... It's clear the idea?

Thanks in advance


Updated
Without the server's gateway it seems to work...

---

