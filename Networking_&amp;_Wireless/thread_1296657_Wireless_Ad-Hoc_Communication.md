---
title: "Wireless Ad-Hoc Communication"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by treeofdeath on 2009-10-20
I have successfully setup an adhoc connection between two laptops (both Dells with factory ubuntu upgraded to 9.04 but using fully supported wireless cards) but it doesn't appear to be working completely. While the network manager applet looks like it is genuinely going through the paces and then succesfully gives the "connection established" notification, I cant browse shared folders or communicate between the two computers.
The main reason I have the adhoc connection is to be able to chat between the two laptops, and though I setup Pidgin using the Bonjour protocol, nothing interesting happens. The computers just sit there, apparently connected but doing nothing.
Is this a firestarter/iptables problem? I've added policy exceptions and even stopped the firewall, but nothing seems to be working. What am I missing?

---

### Post by treeofdeath on 2009-10-21
bump

anyone have any ideas?

---

### Post by redmk2 on 2009-10-22
> **treeofdeath said:**
> I have successfully setup an adhoc connection between two laptops (both Dells with factory ubuntu upgraded to 9.04 but using fully supported wireless cards) but it doesn't appear to be working completely. While the network manager applet looks like it is genuinely going through the paces and then succesfully gives the "connection established" notification, I cant browse shared folders or communicate between the two computers.
The main reason I have the adhoc connection is to be able to chat between the two laptops, and though I setup Pidgin using the Bonjour protocol, nothing interesting happens. The computers just sit there, apparently connected but doing nothing.
Is this a firestarter/iptables problem? I've added policy exceptions and even stopped the firewall, but nothing seems to be working. What am I missing?

Can you connect to anything on the internet?  Are the 2 computers connected through a switch (router combo)?  What are the IP addresses for these 2 computers?

Tell us what IP addresses your laptops are using.  You can see the IP addresses with this command in the terminal.```
ifconfig -a
```

On my desktop it looks like this.```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:76:cd:54:e0  
          [COLOR="Red"]inet addr[/COLOR]:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fecd:54e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4467 errors:0 dropped:0 overruns:1 frame:0
          TX packets:4247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4508505 (4.2 MB)  TX bytes:480658 (469.3 KB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41200 (40.2 KB)  TX bytes:41200 (40.2 KB)


```

The IPv4 address is noted in red.

---

