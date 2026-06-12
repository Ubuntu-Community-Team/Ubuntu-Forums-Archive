---
title: "Server 12.04 LTS - Internal PC can ping websites but unable to pull up in browser"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by mortt1 on 2013-05-02
Ubuntu Community,

I'm looking for some suggestions on what can be causing my Ubuntu server to not allow clients to pull up websites. I have tried every possible How-To, Setup, etc. to setup my server as a router/gateway but every time I run into the same problem.

**Here's what I'm using:**

```
Comcast RCA Modem (don't know model and unable to check at the moment) - 25mbps/1.5mbps

OEM Production 2550L2D - Ubuntu Server 12.04 LTS
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856205007](http://www.newegg.com/Product/Product.aspx?Item=N82E16856205007)

MacBook Pro (Summer 2010 edition) - Windows 7
```

**For my server, I use the following setup:**
 
```
eth0 (WAN) - Using DHCP
eth1 (LAN) - Using Static 192.168.1.1, Netmask 255.255.255.0
DNS - Have setup DNS through various methods (bind9, webmin, shorewall)
DHCP - Have setup DHCP through various methods (isc-dhcp-server, webmin)
IP Forward - Have setup IP forwarding through various methods (sysctl.conf, shorewall)
IPtables - Have setup IPtables through various methods (iptables,shorewall,shell scripts)
```

**For my Macbook Pro, I use the following setup:**

```
Windows 7 Home Premium
Network (Pre-DHCP configuration) - Using Static 192.168.1.50, Netmask 255.255.255.0, Gateway 192.168.1.1, DNS 192.168.1.1
Network (Post-DHCP configuration) - Using DHCP
```

**Here's what happens from a networking perspective:**

Server - can ping & traceroute 192.168.1.50, can ping, dig, & traceroute [www.google.com]("http://www.google.com") and can get packages through apt-get/aptitude
Windows 7 - can ping & traceroute 192.168.1.1, can ping & traceroute [www.google.com]("http://www.google.com")

If I then open IE or Chrome and try to navigate to [www.google.com]("http://www.google.com"), it tells me the website is found and sometimes even gives me a white screen like it's going to load but then times out. However, if I try to go to [www.msn.com]("http://www.msn.com"), the name on the tab updates to reflect it's MSN and the text comes through, but doesn't seem to go past that.

When I look at the syslog I see that the packets are making it from the PC to the Server and the request is going out to the Website. I read somewhere that IPv6 can cause slow internet speeds (not sure if that's what's happening but it seems like it) so I entered the following into my sysctl.conf and rebooted

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

Afterwards, doing an ifconfig no longer reflects any reference to IPv6 but still same results on PC. I also read that MTU of 1500 sometimes causes these problems so I tried finding the MTU where I no longer got the message and think it was at 1452 but I was still unable to connect online via PC (sorry, can't remember exact details on this, but it was based off a post I read about checking max MTU).

On one of my many attempts of fixing this by re-installing and starting fresh, I also setup outside access for my brother using SSH and he was able to connect quickly.

I have checked my IPtables configuration for all tables and chains and do not see anything abnormal or different that anyone else who is running a Linux gateway/router. I have also searched to see if anyone else is having problems with the Broadcom 57788 chip and I could not find anything other than Ubuntu's component catalog.

Unfortunately, I don't get much time at home to work on this so if you have any suggestions, please include a couple of following steps so I can try them in one go and come back with results. Since this is a completely new machine and I'm still one step 1 in my mind, I have nothing of value on the machine and I am willing to start over from scratch if anyone feels that is necessary.

Thank you in advance!

P.S. Sorry for the extremely long post but trying to provide everything so maybe we can pinpoint this quickly :)

---

