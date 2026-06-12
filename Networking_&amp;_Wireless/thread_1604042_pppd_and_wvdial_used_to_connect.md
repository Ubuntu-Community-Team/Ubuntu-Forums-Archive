---
title: "pppd and wvdial used to connect"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by sportsdude81 on 2010-10-23
I have a couple of questions for anybody willing to answer them.  I have a GSM modem with a t-mobile SIM card that I am currently trying to use to connect to the Internet.  I am using Lucid amd64 machine.  I have been running wvdial with a baud rate of 115200 with much success getting the output below:

```
sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","telargo.t-mobile.com"
AT+CGDCONT=1,"IP","telargo.t-mobile.com"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Oct 23 10:40:09 2010
--> Pid of pppd: 2520
--> Using interface ppp0
--> local  IP address 10.132.xxxxx
--> remote IP address 192.168.xxxxx
--> primary   DNS address 172.17.xxxxx
--> secondary DNS address 172.17.xxxxx
```

then if I run ifconfig I can see that ppp0 now has an IP address like below:

```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.132.xxxx  P-t-P:192.168.xxxx  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 B)  TX bytes:2617 (2.6 KB)
```

this is where I'm lost.  I'm figuring I have to set a route in the IP tables so that ppp0 routes to eth0 or another IP I can make up, but not familiar with IP tables or if there is a better/easier solution.

here is my IP route table as of now:

```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.xxxxx   *               255.255.255.255 UH    0      0        0 ppp0
10.0.xxx        *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         10.0.1.1        0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by sportsdude81 on 2010-10-23
Figured it out. so if anybody is curious change the default in the routing table with commands below: (run as root)

```
route del default
```

```
route add default netmask 0.0.0.0 gw xxx.xxx.xx.x dev ppp0
```

fill in the xxxx's with what ever your remote IP address is from wvdial.

---

### Post by harry1868 on 2012-05-13
I know this thread is old , but i really want to know what is the advantage of doing this .
Can we share internet connect of wvdial via ethernet 0?

Also is it possible to create adhoc network and share internet using evdo?

---

### Post by sportsdude81 on 2012-06-17
> **harry1868 said:**
> I know this thread is old , but i really want to know what is the advantage of doing this .
Can we share internet connect of wvdial via ethernet 0?

Also is it possible to create adhoc network and share internet using evdo?

I needed to do it to setup a test kit of an evdo modem and it was easier to develop if it was my default connection.

---

