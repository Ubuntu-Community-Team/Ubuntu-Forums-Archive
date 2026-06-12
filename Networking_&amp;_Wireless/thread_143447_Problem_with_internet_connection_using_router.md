---
title: "Problem with internet connection using router"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by muscaa on 2006-03-12
Hi i just installed ubuntu linux. I'm using D-link DFE-528TX ethernet PCI adapter and Aztech DSL600EW ADSL wifi combo router. I have only enabled a few MAC address to assess the wifi in the router setting. I managed to assess the router from firefox with the [http://192.168.1.1](http://192.168.1.1) but failed to connect to internet. Can anybody help? Thanks in advance. :) 

PS: is 00:11:95:61:5C:B9 my linux MAC address (pls refer to below)? 

sudo ifconfig

eth0    Link encap:Ethernet  HWaddr 00:11:95:61:5C:B9 
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe61:5cb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1630 (1.5 KiB)  TX bytes:1779 (1.7 KiB)
          Interrupt:10 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19001 (18.5 KiB)  TX bytes:19001 (18.5 KiB)

sudo dhclient eth0 up

Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
up: ERROR while getting interface flags: No such device
up: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device

---

### Post by bscbrit on 2006-03-12
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Try following this link to identify where exactly your problems lie.

Yes that is your MAC address - but it isn't a Linux address, or a windows address.  The value is associated with your specific network interface card and it doesn't matter what software tries to read it, they will all get the same value. :D

---

### Post by muscaa on 2006-03-14
hi bscbrit,
thanks for your advice, I followed the instruction in [http://ubuntuforums.org/showthread.php?t=141728](http://ubuntuforums.org/showthread.php?t=141728) 
I disabled IPv6 and rebooted my ubuntu linux and the internet worked fine! :D
Feeling great with ubuntu now.\\:D/

---

### Post by mips on 2006-03-14
I honestly think Ubuntu should come with IPv6 disabled by default but then again thats just my opinion ;)

---

### Post by hyperair on 2007-10-21
For anyone interested, Routerteech ([http://www.routertech.org )'s](http://www.routertech.org )'s) firmware solves all the problems without disabling IPv6 on Ubuntu. It was the faulty firmware that caused the problems in the first place.

---

### Post by kevdog on 2007-10-21
> I honestly think Ubuntu should come with IPv6 disabled by default but then again thats just my opinion 

I'll second that.  Cant tell you how many times Ive seen this be the problem.

---

### Post by hyperair on 2007-10-21
Like I said, the IPv6 problem comes from outdated and/or sub-par firmware. By upgrading the firmware, or using a suitable 3rd-party firmware, e.g. Routertech's, the problem is solved.

---

### Post by c1t1z3n on 2007-10-21
IPv6 does fix the web connection, but I still can't get synaptic / apt-get to work properly... any ideas?

---

### Post by hyperair on 2007-10-22
When you apt-get everything resolves to 1.0.0.0 right? In that case, you should take a look at this page: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

If you don't wish to use the OpenDNS servers, you could look around for your ISP's DNS server addresses and use them in place of the ones listed at the page. The instruction to be followed is the same.

If you feel a little adventurous, you can go upgrade your router's firmware (or use Routertech's), and that should actually solve the problem.

---

### Post by jasontan6 on 2007-11-04
Muscaa, the starter of this thread said that he was using the Aztech DSL600EW router.

I am also using the exact same router. Installed Gutsy 2 days ago and the DNS problem was driving me nuts. Found a firmware upgrade for the router, installed it, problem solved.

Link to download firmware from Aztech here [http://www.aztech.com/retail_malaysia/support.html](http://www.aztech.com/retail_malaysia/support.html)

---

### Post by hyperair on 2007-11-04
That's the same router I'm using. I now use the Routertech v2.3 firmware and it works really well =P

---

### Post by jasontan6 on 2007-11-04
> **hyperair said:**
> That's the same router I'm using. I now use the Routertech v2.3 firmware and it works really well =P

Could you name me a few features the Routertech firmware offers which are superior to the Aztech firmware? I may consider using Routertech.

---

