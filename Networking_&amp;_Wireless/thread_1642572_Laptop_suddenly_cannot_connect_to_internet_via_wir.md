---
title: "Laptop suddenly cannot connect to internet via wireless or wired connection!"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by butISitART on 2010-12-10
Hi all,

My laptop has been working fine with ubuntu 10.04, and earlier today it shut down after running out of battery. I came to use it later and discovered that the wifi icon had disappeared from the panel bar, and it won't connect to the wireless network, or via a wired connection.

I have had a play around with this, tried 

ping -c5 google.com

result was:

ping: unknown host google.com

and ping -c5 4.2.2.1

result: 
connect: Network is unreachable.

I have other computers connecting to this network and know that it is working fine.

I have also restarted the gnome panel in an effort to recover the icon for the wifi, but no luck!

Any help would be much appreciated!!

Thanks

---

### Post by butISitART on 2010-12-11
Sorry for the bump, but the problem is no closer to being fixed after a day of playing around with it!

---

### Post by spiky001 on 2010-12-11
can you try ```
sudo dhclient eth0
``` see if eth0 connects? only if your wired connection is eth0

---

### Post by butISitART on 2010-12-11
Thanks!

Tried that, the response is:

Listening on LPF/eth0/00:21:9b:f3:a6:9f
Sending on LPF/eth0/00:21:9b:f3:a6:9f
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

---

### Post by drdos2006 on 2010-12-11
What do you get when you type :  ifconfig 

regards

---

### Post by butISitART on 2010-12-11
eth0   Link encap:Ethernet HWaddr 00:21:9b:f3:a6:9f
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:16

eth0:avahi Link encap:Ethernet HWaddr 00:21:9b:f3:a6:9f
        inet addr:169.254.10.228 Bcase:169.254.255.255 Mask:255.255.0.0
        UP BROADCASt MULTICAST MTU:1500 Metric:1
        Interrupt:16

lo     Link encap:Local loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr:  ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:28 errors:0 dropped:0 overruns:0 frame:0
       TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:2016 (2.0 KB)  TX bytes:2016 (2.0 KB)


Thanks a lot

---

### Post by drdos2006 on 2010-12-11
I copied this from a previous posting for future use. It may be of some help to you......


You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.


regards

---

### Post by spiky001 on 2010-12-11
Have you tried add to panel "notification area"

---

### Post by butISitART on 2010-12-12
Thanks for your help guys! Through a combination of playing around and trying out some of the things on here something clicked and it's online again.

Thanks again, much appreciated!!

---

