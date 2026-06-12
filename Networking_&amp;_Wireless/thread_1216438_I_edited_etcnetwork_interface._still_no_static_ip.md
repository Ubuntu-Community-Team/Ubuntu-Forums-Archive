---
title: "I edited /etc/network interface. still no static ip"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by inga87 on 2009-07-18
I have a pc with ubuntu 9.4 installed. I have also other pcs connected together in a lan with a modem, using a switch.
Before formatting I used to connect the main computer to the modem, as a gateway. other PCs connected to this in order to share internet connection.

now I formatted few days ago and I had to "retune" everithing as it was before.
I edited my /etc/network/interfaces in this way ```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0


auto eth0

pre-up /sbin/ifconfig eth0 up 

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider
```in order to automatically connect the pc to internet at the boot. I have to set a static ip, so I can use it as a gateway address in the other pcs. unfortunatly it doesn't work. maybe I wrote something wrong. please some one does know something about it?
it doesn't ping nor from itself (as 192.168.0.1) neither from other pc.

---

### Post by Kraut~salat on 2009-07-18
I would not edit the file myself unless I really knew what I was doing. Why don't you use Gnomes NetworkManager applet to set your static IP adress?

Also I don't quite get your last sentences. What doesn't work? You cannot coonect to the internet or you cannot ping anyhing in the internet or you cannot ping your gateway pc from another pc or you cannot get to the internet from another pc thru the gateway?

---

### Post by wojox on 2009-07-18
Read here:

[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

---

### Post by inga87 on 2009-07-18
@Kraut~salat

I tried to use NM but in the end I found that it wasn't useful for me.
I tried to set both the interfaces (eth0 and ppp0) with nm but it let you only choose between them, when I was connected to ppp0 I couldn't use the lan, and vice-versa.
Before formatting I used to manage the auto ppp0 interface with /etc/network/interfaces and the eth0 with nm. but I think it doesn't work anymore ( i can connect manually at the startup with pon dsl provider but , it will never connect on his own... or maybe I made a mistake with the configuration).
the more logical conseguence is to manage both the interfaces with /etc/network/interfaces
 but neither now it does work. it connect on startup on his own and I can actually use internet, but the eth0 interface and the IPs seem not to be read from the file.

when I give the command route I obtain this
```
inga@inga-desktop:~$ route
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.1   *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0

```

and this is ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:13:8f:11:22:ae  
          indirizzo inet6: fe80::213:8fff:fe11:22ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5376 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:4699877 (4.6 MB)  Byte TX:1180495 (1.1 MB)
          Interrupt:23 Indirizzo base:0x2d00 

ppp0      Link encap:Point-to-Point Protocol  
          inet indirizzo:87.2.202.67  P-t-P:192.168.100.1  Maschera:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:5071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5247 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:3 
          Byte RX:4580779 (4.5 MB)  Byte TX:1060837 (1.0 MB)


```

---

### Post by inga87 on 2009-07-19
Problem Soleved
I edited /interfaces commenting all the lines related to "auto dsl-provider"

this probably was related with the fact that I edited /etc/rc.local adding the lines ```
ifconfig eth0 up
pon dsl-provider

```

maybe they made conflict together.
now the network start at the boot and the connection is shared within the PCs.

---

