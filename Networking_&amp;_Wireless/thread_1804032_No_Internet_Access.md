---
title: "No Internet Access"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by looorentz on 2011-07-14
Hey guys,

I am having problems connecting to the internet (posting this on my other pc). Here is a dump of IFCONFIG and my /etc/network/interface file.

```

IFCONFIG

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:fb:d0:cd  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fefb:d0cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5176 (5.1 KB)  TX bytes:8339 (8.3 KB)
          Interrupt:47 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3296 (3.2 KB)  TX bytes:3296 (3.2 KB)


INTERFACE file

auto lo
iface lo inet loopback

```

Any help is greatly appreciated!

Thank you,

looorentz

---

### Post by Hashan Rathnayaka on 2011-07-14
bump

---

### Post by grahammechanical on 2011-07-14
You need to explain what you mean by

> problems connecting to the internet

According to ifconfig you are connected to a modem/router by ethernet cable. Do you notice that you have an inet addr that would be the IP address of the router and it is shown to be UP and RUNNING.

Is it wireless that you want to connect with but cannot? I am assuming that you are using 11.04 because you do not tell us. It makes a difference to the directions that you will be given.

Click on the Network Manager icon. It is the two arrows going in opposite directions. Do you see a list of available wireless networks? Is there a tick mark against the line Enable Wireless? Clicking on the lines Enable Networking and Enable wireless will act like an on/off switch.

Is you machine a laptop? Do you have another OS installed? Can you access web sites? All this is relevant information that will helps us to help you.

Regards.

---

### Post by looorentz on 2011-07-14
Sorry for being vague. The problem that I have is that I cannot access the internet. I can connect to the internet, but it seems that all my traffic is being routed incorrectly or something. 

The ting is, everything was working fine until I used Firestarter. This suddenly stopped my vpn from working. So I turned it back off and it was still not working. So I restarted and just tried to view a web page or update the software center, I cannot.

Again, I am connected fine, however I cannot access any web pages, including my router and modem pages.

I am running ubuntu 11.04 on both my pc's.

Also, wireless connects the same as wired. But still cannot view any web pages. 

Just to clarify, I am trying to get the ethernet to work, it says it us up and running, but I cannot access anything.

Are there any other outputs you would like to see to help me with this? 

Thank you

looorentz

---

### Post by looorentz on 2011-07-14
Well, I've been using ubuntu about 4 days now, and I managed to solve this! Haha.. if all else fails:

```
sudo rm -r /lib/modules/2.6.38-8-generic-pae/kernel/drivers/net
```

Then restart - worked wonders.

---

