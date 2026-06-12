---
title: "unable to browse but connected to internet"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by joncolson on 2009-07-27
Running 9.04 on a wired connection.  I have an IP address.  I can ping my DNS server.  But I can't browse the web using Firefox or Opera.

Please help!

I'm running a live CD of Fedora right now, so I know the problem isn't hardware related.

For weeks now, the connection would seem to drop then restablish, then repeat, and finally it just stopped re-establishing itself.  I didn't knowingly change anything.

---

### Post by wojox on 2009-07-27
What does :

```
ifconfig
```

say post it back here.

---

### Post by Newfoundlander on 2009-07-27
Also try the following...

```
ping www.google.com
```

And...

```
ping 74.125.79.99
```

---

### Post by doas777 on 2009-07-27
> **joncolson said:**
> Running 9.04 on a wired connection.  I have an IP address.  I can ping my DNS server.  But I can't browse the web using Firefox or Opera.

Please help!

I'm running a live CD of Fedora right now, so I know the problem isn't hardware related.

For weeks now, the connection would seem to drop then restablish, then repeat, and finally it just stopped re-establishing itself.  I didn't knowingly change anything.

do you have any upstream hardware? flapping wans have been troubling netadmins for decades now.

---

### Post by joncolson on 2009-07-27
Thanks so much for the attention.  

Yes I have a router.  I am able to connect to it using Firefox and through that release/renew the IP lease.  

Here is my ifconfig.
jonathan@deathstar:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:58:95:50  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe58:9550/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1438 (1.4 KB)  TX bytes:6674 (6.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

Sorry i have to reboot back into ubuntu to answer the other questions then back into this live Fedora CD.  I was unable to ping [www.google.com](www.google.com) before.  I believe it said something about unable to resolve host???  Not exactly sure.

---

### Post by LookTJ on 2009-07-27
Are you able to ping your router?

Most common ip telling from the ifconfig details is 192.168.1.1


```
ping 192.168.1.1
```
```
sudo route
```to double check the router's ip.
:)

EDIT: 

What type of card do you have?

```
lspci | grep Ethernet
```

---

### Post by joncolson on 2009-07-28
So weird.  Now for no reason, nothing else changed.  I'm on the Internet.

I still see errors in IFCONFIG.  

I don't understand.

lspci | grep Ethernet
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:58:95:50  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe58:9550/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1368329 (1.3 MB)  TX bytes:277624 (277.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8254 (8.2 KB)  TX bytes:8254 (8.2 KB)

---

### Post by doas777 on 2009-07-28
I'm guessing you have an hardware issue (or a serious router misconfiguration). are you in a position to replace the cabling? also can you confirm this problem with another PC?

---

### Post by DJonsson2008 on 2009-07-29
have you compared the output of 

route

in terminal between your boot CD and your Ubuntu install.

someone also made the brilliant suggesting of booting with 
the live CD that matches your install then comparing the
conf files, beginning resolv.conf between the CD and install
to see what the difference is.

as well one could us a USB stick to store the resolv.conf and do a comparison. wish i would of thought of that.

anyhow i had a similar problem,

lan working, but no internet.

digging around i found the problem was in /etc/resolv.conf

ifconfig
looked ok and was showing the network card was working...

route
showed either no gateway or wrong gateway

ping gateway router was ok.
could open gateway router admin page in browser
but no internet.

the solution was incredibly simple.

adding the following line
with number of gateway router
solved the problem instantly closed
and reopened browser and it worked.

nameserver XXX.XXX.XXX.XXX

i also note in the sample resolv.conf
a line called

search com

not sure what that is but i added it for good luck.
not sure if it helped but i can now see the internet

it also seems you can load multiple nameserver addresses
in resolv.conf, in the even one might be moving from workplace
to workplace that might be handy.

---

### Post by LookTJ on 2009-07-29
Check your router's manufacturer's website to download the newest firmware for your router model.

:)

I really think it's a router firmware issue.

---

