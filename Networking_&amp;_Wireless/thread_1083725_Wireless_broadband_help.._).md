---
title: "Wireless broadband help.. :)?"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by linktogunner on 2009-03-01
I recently installed Ubuntu using 'wubi' which I got from the Ubuntu homepage(Ubuntu.com). I got everything set up and it is great.. but I have just one problem - my broadband wireless interent will not work.  I logged onto my ISPs website and got this.


HOW IT WORKS--------
A wireless modem is mounted to your rooftop and aimed at one of our towers.

A small wire is run from the wireless modem to your PC.

Your PC logs onto our network with a PPPoE username and password.
--------------------


Up in the right hand corner when im on Ubuntu there is an icon with two computer monitors and when I click it the only connection options are "Auto eth0" and "VPN >". I can edit my connection but that doesn't really do any good when you don't know what your doing in the first place. Thanks for your time and any help is greatly appreciated. - Gunner

---

### Post by smani on 2009-03-01
Those instructions seem to refer to the communication between ISP and modem works, not modem - pc.
Anyway, please post the output of```
ifconfig
```

---

### Post by linktogunner on 2009-03-01
> **smani said:**
> Those instructions seem to refer to the communication between ISP and modem works, not modem - pc.
Anyway, please post the output of```
ifconfig
```
```


eth0    Link encap:Ethernet  HWaddr 00:11:11:3e:47:98
        inet6 addr: fe80: :211:11ff:fe3e:4798/64 scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets: 212 errors: 0 dropped: 0 overruns: 0 
        frame: 0
        TX packets: 11: errors: 0 dropped: 0 overruns: 0 
        carrier: 0 
        collisions: 0  txqueuen: 1000
        RX bytes: 13160 (13.1 KB)  TX bytes: 2178 (2.1 KB)

lo      Link encap: Local Loopback
        inet addr: 127.0.0.1 Mak: 255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU: 16436 Metric: 1
        RX packets: 246 errors: 0 dropped: 0 overruns: 0 
        frame: 0
        TX packets: 246 errors: 0 dropped: 0 overruns: 0
        carrier: 0 
        collisions: 0 txqueuelen: 0
        RX bytes: 15408 (15.4 KB)  TX bytes: 15408 (15.4 KB) 
```


there you go.

---

### Post by smani on 2009-03-01
Okay, so there is currently no connection between your modem and you pc (which should be confirmed by the fact that you see a little exclamation mark in the icon you mentioned before). You should check if firstly the network cable works and secondly if your modem has the DCHP server enables (assuming your network only consists of your pc and the modem). Otherwise you could set a fix ip address to your ethernet card.

---

### Post by linktogunner on 2009-03-01
> **smani said:**
> Okay, so there is currently no connection between your modem and you pc (which should be confirmed by the fact that you see a little exclamation mark in the icon you mentioned before). You should check if firstly the network cable works and **secondly if your modem has the DCHP server enables (assuming your network only consists of your pc and the modem). Otherwise you could set a fix ip address to your ethernet card.**

and if you don't mind me askin how would i go about doing those things you mentioned

---

### Post by Ben Crisford on 2009-03-01
I have had similar problems.  However my adapter is inbuilt, and ubuntu says that it is operational.

Although it won't find my network :S.

---

### Post by smani on 2009-03-02
Here are some basic concepts of networking:
[LIST]
[*]Usually a network card needs following information to work correctly:
[LIST]
[*]IP Address: identifies the host in the subnetwork. Consists of 4 numbers between 0 and 255 in IPv4 format, the first three identify the network and thus have to be the same for every host in the network, usually 192.168.1. Therefore all IP addresses of format 192.168.1.X are part of that subnetwork. Computers on different subnetworks need a router that connects the two subnetworks in order to be able to communicate with each other.
[*]Gateway: usually the address of the router (which often is part of the modem) of the subnetwork, usually has address 192.168.1.1.
[*]Subnet mask: usually 255.255.255.0
[*]DNS server: the server that translates domain names into ip addresses, usually the address of the modem (again, usually 192.168.1.1) which acts as a relay to the DNS server of your ISP
[/LIST]
A sample network configuration therefore could be:
[LIST]
[*]IP Address: 192.168.1.2
[*]Subnet mask: 255.255.255.0
[*]Gateway: 192.168.1.1
[*]DNS Server: 192.168.1.1
[/LIST]
[*] DHCP servers are servers that provide this information for you if you leave all settings on autodetect, thus not requiring that the user knows the above information. DHCP servers are usually part of the gateway/modem and enabled by default, but it may have been disabled for some reason, to check you should access the web configuration utility of the modem, usually at [http://192.168.1.1](http://192.168.1.1) - and as you are currently unable to connect you may first have to set the information by hand, hoping that your modem follows the standard convention (i.e. it's address is 192.168.1.1).
[/LIST]
The best way to expand knowledge of the basics on networking is clearly reading some related wikipedia articles, or some times modem manufacturers provide excellent manuals.

---

