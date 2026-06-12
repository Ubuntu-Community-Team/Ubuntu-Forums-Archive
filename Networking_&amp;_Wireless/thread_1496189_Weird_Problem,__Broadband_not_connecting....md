---
title: "Weird Problem,  Broadband not connecting..."
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by davidbilla on 2010-05-29
Hi,

First off, this is completely weird. I have a desktop and a laptop with ubuntu 9.04 and a laptop with windows vista. 

People from my ISP(BSNL) came and 'configured' my modem on a windows machine(theirs) yesterday. In fact, they had problems configuring it on their system and I showed them that there was no problem in the line by configuring it in my ubuntu laptop. Then they bucked up and configured it in their windows machine successfully.

But, from that moment onwards, I can connect to the internet with my windows vista laptop(the usual way, create a new pppoe conn. and enter user/pass) but not with my ubuntu 9.04 laptop and desktop.

pppoeconf finds my 'eth0' but when it starts 'looking for pppoe access concentrator on eth0' it cannot detect anything and times out. This happens in both of my linux systems. It behaves as if I haven't connected my ethernet cable to the system at all.

Any ideas? Please post your questions if I haven't been clear enough. Thanks.

---

### Post by dineshs on 2010-05-29
What is the model name of your modem? Pl post the output of
```
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by davidbilla on 2010-05-29
Modem model no. DataOne UT-300R2U.

Output of ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:26:22:d4:59:87  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fed4:5987/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30453 (30.4 KB)  TX bytes:29720 (29.7 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 0c:60:76:9b:c6:84  
          inet6 addr: fe80::e60:76ff:fe9b:c684/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12117 (12.1 KB)  TX bytes:12117 (12.1 KB)

pan0      Link encap:Ethernet  HWaddr c2:86:29:da:45:b0  
          inet6 addr: fe80::c086:29ff:feda:45b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:11251 (11.2 KB)

pan0:avahi Link encap:Ethernet  HWaddr c2:86:29:da:45:b0  
          inet addr:169.254.7.235  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```


Output of cat /etc/resolv.conf:
```

nameserver 192.168.1.1
```

---

### Post by arjunak01 on 2010-05-30
if you use bridged mode, use network manager to create a new DSL connection. enter your username and password into the respective fields and click apply, it should work now. plz note that this doesnt not work in ubuntu 9.10
if u use pppoe then use the "Wired connection 1" automatically created by ubuntu.

---

### Post by dineshs on 2010-05-30
Pl try this method to configure your modem in `always on' mode
Open Firefox
Type [COLOR="DarkRed"]192.168.1.1[/COLOR] in Address bar. Click GO
Enter both Username and Password as [COLOR="Blue"]admin[/COLOR]
Click OK
Click advanced setup
Click edit at the right end of the line having 0/35 as VPI/VCI value
Click Next
select PPP over Ethernet and click next
Enter  PPP Username and PPP Password as allotted by BSNL in the respective fields 
Click Next
Click Next again
Click save
Click save/reboot
wait till reboot complete (3 minutes)

Once reboot you can access the site directly(No pppoeconf....)

---

### Post by davidbilla on 2010-06-01
@arjunak01 : Thanks. I've tried that method but it didn't work for me.

@dineshs: Thanks again. It didn't work though. I cannot even reach the nameserver address 192.168.1.1. Firefox says page not found.

It is as if the ethernet cable is not connected to the port at all. And it is the same with both of my ubuntu systems. pppoeconf says 'cannot find access concentrator'. 

Could it have anything to do with the modem configuration at the service provider's end? But it works in vista.

Thanks.

---

### Post by tanixmukherzee on 2010-06-01
@david
i am having the same problem...lukin for solution...
if u can resolve this issue plz post here...

---

### Post by dineshs on 2010-06-01
Pl try this
Configure NM with the option Automatic(DHCP) for both ethernet ports-because if you are setting manual IP it should be outside the DHCP range-Then post the output of
```
ifconfig -a
```
and
```
ping 192.168.1.1 -c5
```

If there is no reply for ping 192.168.1.1 you can try changing cable to eth1 ie the other ethernet port.

---

### Post by neeraj-vaidya on 2010-06-15
I am having this problem too with Lucid 10.04....DavidBilla , any luck in getting this resolved ?

---

### Post by dineshs on 2010-06-15
neeraj,
pl post the output of 
```
ifconfig -a
``` 
```
ping 192.168.1.1 -c5
```
and 
```
ping 4.2.2.1 -c5
```

---

### Post by davidbilla on 2012-05-23
The problem was with the ISP anyway! Solved it after weeks of trying out various things to get it working. Forgot to update it here!

---

### Post by sidart on 2012-09-05
did they tell you what exactly is the problem? It would be a miracle, but just hoping.

I am having a similar issue when I connect through my ubuntu 10.04 server. This started happening all of a sudden. Server tries to reach an access connector that gives me a user not found error during chap authentication.This happens for a couple of hours.  After a couple of hours it retries by changing the access connector, and then connects immediately through the new access connector. The modem is in bridge mode

I have tried forcing the connector using rp_pppoe_ac, but to no avail.
Of course if I use the adsl modem in pppoe mode and remove my ubuntu server, it connects just fine.

BSNL anyway refuses to acknowledge that they might have a problem. So if they have told you what the issues is maybe I can bring it up to them

---

