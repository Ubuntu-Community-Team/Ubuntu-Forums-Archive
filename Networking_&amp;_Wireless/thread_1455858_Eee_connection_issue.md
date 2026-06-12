---
title: "Eee connection issue"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by beak02 on 2010-04-16
Hi

I'm running an Asus Eee PC with the Ubuntu Netbook Remix 10.04.

I have a problem with connecting to wireless networks.  It connects fine to the unprotected BTOpenzone near where I live, but will not connect to my secured connection (secured by WPA).  I have tried resetting the router and resetting the netbook, but I can't get it to connect.  It finds the network, says it's connecting, but repeatedly asks for the network key (which is entered correctly, I checked, three times!)

Any ideas what's causing the problem?

---

### Post by beak02 on 2010-04-16
Anyone?

---

### Post by bourger on 2010-04-16
All I can say that I have the same issue (same netbook but with Karmic). However I **can** connect to my home WPA network - after a key request... And I can connect to any WEP network (provided that I know the key :)) on the fly. 
Some time ago I had exactly the problem you describe (couldn't connect to any WPA network at all), but what did I do to solve it - can't remember... 
What wireless driver do you use? I'm under ndiswrapper.

---

### Post by beak02 on 2010-04-16
I haven't changed the wireless driver on it since install... not sure exactly which one it's using.  I get a key request, but entering it again doesn't help... it just asks for it again.

Thanks by the way, nice to know someone else has this problem, and it's not just me going mad! :D

---

### Post by crustymonkey on 2010-04-19
I've got an eee pc 900 as well with *exactly* the same issue.  I can't connect to a WPA or WPA2 access point.  I just did a clean install of UNR 10.04 beta 2.  I get the popup asking for the key, which I enter, and then it just tries to connect for a while before dying.

---

### Post by crustymonkey on 2010-04-19
On a related note.  I just plugged in an ethernet cable and I was not able to get a network connection.  I thought this was odd so I popped up a terminal and tried to manually grab an address for eth0 with dhclient3:

```

$ sudo dhclient3 eth0
...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 10.0.0.160 from 10.0.0.1
DHCPREQUEST of 10.0.0.160 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 10.0.0.160 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 10.0.0.160 from 10.0.0.1
DHCPREQUEST of 10.0.0.160 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 10.0.0.160 on eth0 to 255.255.255.255 port 67
...
...

```

The above pattern repeats endlessly instead of actually finishing the DHCP transaction, setting the IP and getting nameserver info.  Now if I manually set up the network from the command-line, everything works fine:

```

$ sudo ifconfig eth0 10.0.0.160 netmask 255.255.255.0
$ sudo route add default gw 10.0.0.1
$ sudoedit /etc/resolv.conf
nameserver 10.0.0.7

```

From there out, everything works just fine.  I wonder if the WPA/WPA2 connection itself isn't being set up, but the actual point of fail is the at the DHCP transaction.

Personally speaking, I'm running DHCP on my FreeBSD firewall.  As far as DHCP server, it is isc-dhcp3-server-3.0.5.  I'd be happy to help figure this out, if it hasn't been already (I'm currently running updates...).  Just let me know what info you would like.

---

### Post by crustymonkey on 2010-04-19
Heheh, sure enough.  After setting up the network connection manually and running updates, everything seems to be working just peachy now :-)

---

