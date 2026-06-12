---
title: "Network won´t connect on boot"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by samden on 2008-12-09
This is just a minor annoyance, but it would be nice to fix it. I have this problem with both my Ubuntu machines (specs in signature), whether connected wirelessly or via ethernet.

When I boot Ubuntu, the networking icon in the top panel indicates that the network is connected. However when I try and actually use the internet, it doesn´t work.

When I click on the networking icon, and select my network connection in the dropdown menu, it reconnects to the network. After reconnecting everything works fine.

There are many threads talking about problems with wireless connections not connecting after boot, but this occurs with ethernet also.

---

### Post by Iowan on 2008-12-09
Post results of **ifconfig -a** (before and after reconnect would be interesting).

---

### Post by samden on 2008-12-09
ifconfig -a for the Pentium III connecting via ethernet.

Before:
```
eth0      Link encap:Ethernet  HWaddr 00:x0:18:21:xx:xx  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:724 (724.0 B)  TX bytes:90 (90.0 B)
          Interrupt:12 Base address:0xd400 

```
After:
```
eth0      Link encap:Ethernet  HWaddr 00:x0:18:21:xx:xx  
          inet addr:1xx.1xx.1.2  Bcast:1xx.1xx.1.2xx  Mask:255.255.255.0
          inet6 addr: xx80::2x0:18xx:xx21:ebfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66307 (64.7 KB)  TX bytes:30520 (29.8 KB)
          Interrupt:12 Base address:0xd400 

```
Note all x´s in addresses are where I have edited them before posting.

---

### Post by samden on 2008-12-09
ifconfig -a for Acer laptop, connecting via wireless.
Before:
```
wlan0     Link encap:Ethernet  HWaddr 00:1x:4x:4x:x6:xx  
          inet6 addr: xx80::21x:4xxx:xx43:x616/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:322 (322.0 B)  TX bytes:810 (810.0 B)
          Interrupt:17 Memory:f8000000-f8010000 
```
After:
```
wlan0     Link encap:Ethernet  HWaddr 00:1x:4x:4x:x6:xx  
          inet addr:1xx.1xx.1.3  Bcast:1xx.1xx.1.2xx  Mask:255.255.255.0
          inet6 addr: xx80::21x:4xxx:xx43:xxx6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160344 (156.5 KB)  TX bytes:43376 (42.3 KB)
          Interrupt:17 Memory:f8000000-f8010000 

```

---

### Post by jonobr on 2008-12-09
Hello


Do you have multiple network interface cards on the one machine?
When you mention you have to select your network, how many network options do you have?
Are you using them all?

Im thinking your bootp requests (the request to get an IP address from your DHCP) is not being issued from your eth0.

---

### Post by jonobr on 2008-12-09
btw, I think I cracked your IP address

 inet addr:1xx.1xx.1.3  Bcast:1xx.1xx.1.2xx  Mask:255.255.255.0
=
192.168.1.3 Bcast:192.168.1.255

---

### Post by samden on 2008-12-09
The PIII has ethernet and a dialup modem (which I have never used). The laptop has ethernet, wireless, and a dialup modem (again never used) - when I tested that the ethernet was not plugged in, I was just connecting using the wireless.

I only have the one network option, my home broadband router. That one connection appears in the dropdown menu, I select it, the two little dots appear that go green one by one as it connects, and then I have a working connection - the same procedure whether I am using ethernet or wireless.

---

### Post by samden on 2008-12-09
Well done with the IP address, how did you do that? How sensitive is that info, should I try and edit it out if I am concerned about security, and if so how would I do that so it couldn´t be cracked?

---

### Post by jonobr on 2008-12-09
Hey dont worry about it, thats the default private network assigned by most routers, you can change it but I would not worry about it.

Thats the way 90% of people have  it.

The broadcast is a class C address ( I could see it in the subnet mask (255.255.255.0) )

Shame on me for trying to spook you,
But again, nothing to be worried about, you should be more concerned about your router firewalling and filtering and securiy

---

### Post by samden on 2008-12-15
(bump)

This is getting rather frustrating now as I would like to use fluxbox, but each time I boot I have to log in to Gnome to use the panel icon before I have any internet.

I have tried doing this from the command line (sudo ifdown eth0, sudo ifup eth0) but get the message "interface eth0 not configured" - which is odd because I am getting internet through ethernet and I am fairly sure it is being called eth0.

If anyone has any suggestions I would be very grateful.

---

### Post by samden on 2009-01-21
I have found a workaround so I don't have to boot Gnome then Fluxbox. To access the Gnome network panel icon from Fluxbox, add
```
nm-applet &
```
to ~/.fluxbox/startup - that will show up the network icon in the Fluxbox slit when you reboot fluxbox, allowing it to be used from there. Or you can manually start it by typing nm-applet in a shell.

This doesn't solve the problem of it not connecting automatically on boot, it would be nice to get that working.

---

