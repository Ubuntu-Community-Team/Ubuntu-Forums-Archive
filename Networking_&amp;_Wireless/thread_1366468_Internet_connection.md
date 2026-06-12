---
title: "Internet connection"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by melwaltrip on 2009-12-28
I have installed Ubuntu along side Windows XP on a desktop. My Windows internet connection works fine both before and after installing Ubuntu. However, Ubuntu will not connect. The following is some data from the Windows connection: (It is a wired network)

Physical address 00-15-F2-D5-1C-B1
Address type - DHCP
IP  192.168.1.100
Subnet 255.255.255.0
Gateway 192.168.1

Can some one guide me through to get Ubuntu connected.

---

### Post by Charlietje on 2009-12-28
Hey,

go into ubuntu and post the output of:
```
ifconfig
```

---

### Post by 32034 on 2009-12-28
Like mentioned "ifconfig" output would be greatly appreciated :KS

---

### Post by melwaltrip on 2009-12-28
eth0 Link encap:Ethernet HWaddr 00:15:f2:d5:1c:b1
inet6 addr fe80::215:f2ff:fed5:1cb1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST
MTU:1500 Metric:1
RX packets:7 errors:0 dropped:0  over runs:0 frame:0
TX packets:10 errors:0 dropped:0 Over runs:0 carrier:0 
collisions:0 txqueuelen:1000 RX bytes 581 (581.0 B)
TX Bytes 1876 (1.8KB) Interrupt:23 Base address 0xc000

lo Link encap: local loopback
inet addr: 127.0.0.1 Mask:255.0.0.0
inet6 addr::1/128 Scope:host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 Over runs:0 frame:0
TX packets:0 errors:0 dropped:0 over runs :0 Carrier:0
collisions:0 txqueuelen :0 rx bytes:0 (0.0B) tx bytes (0.0B)

---

### Post by 32034 on 2009-12-28
ifup eth0 (brings up your Ethernet card if its down)
dhclient eth0 (fetches a new IP address from the DHCP server)
ifconfig (see if you see an IP address now in the output for eth0)

---

### Post by melwaltrip on 2009-12-28
You lost me completely.......

---

### Post by 32034 on 2009-12-28
Type those into your Terminal; anything in parenthesis explains what the command does

ifup eth0
dhclient eth0
ifconfig

---

### Post by melwaltrip on 2009-12-28
Ok

---

### Post by shairozan on 2009-12-28
As an explanation, it looks like 32034 is wanting you to make sure that Ubuntu has your ethernet card active. I believe it already is, as the IFCONFIG output shows the interface as being UP. 

I'm guessing you're using a Linksys router from the addressing scheme? Can you do the following for me? 

open up a terminal and enter the following code:

```

sudo /etc/init.d/networking restart
```

This will attempt to acquire a new address from your router and make sure your interface is up. You can also perform this in the GUI by clicking on the network connection icon in the top right and selecting AUTO ETH0 as it will attempt the same thing.

---

### Post by melwaltrip on 2009-12-28
If I enter "ifup eth0" I get a msg - failed to open statefile/var/run/network/ifstate: Permission denied.

If I enter dhclient eth0 I get a whole page of error junk with permission denied.

If I enter sudo/etc/init.d/networking restart I get a msg that says "reconfiguring interfaces then another prompt but I still have no ip addrwess in if config and still have no internet connection.

---

### Post by 32034 on 2009-12-28
sudo su -
dhclient eth0

---

### Post by melwaltrip on 2009-12-28
I hope I have not scared you guys off......I am stumped....

---

### Post by melwaltrip on 2009-12-28
If I enter sudo dhclient eth0 I get:

Listening on LPF/eth0/00:15:f2:d5:1c:b1
Sending on   LPF/eth0/00:15:f2:d5:1c:b1
Sending on socket/fallback
DhcpDiscover on eth0 to 255.255.255.255.255 port 67 Interval7
DhcpDiscover on eth0 to 255.255.255.255.255 port 67 Interval18
DhcpDiscover on eth0 to 255.255.255.255.255 port 67 Interval15
DhcpDiscover on eth0 to 255.255.255.255.255 port 67 Interval17
DhcpDiscover on eth0 to 255.255.255.255.255 port 67 Interval5
No DHCP offers received
No wroking leases in persistent databas - sleeping

---

### Post by 32034 on 2009-12-28
I'm not trying to insult you with this, but is everything connected like its supposed to be and things plugged in? It's odd not to find a DHCP server. Sometimes the lock tab on Ethernet cables break off or doesn't keep the end of the cable inside a router jack or Ethernet jack.

---

### Post by melwaltrip on 2009-12-28
I am not insulted at all - I assumed the cabling is OK since the Windows XP operating system (on the same computer) works fine and connects to the internet, however, I will physically check everything just to make sure. I DO appreciate the help you are giving....

---

### Post by 32034 on 2009-12-28
I've called Comcast a few years ago trying to figure out what was wrong with my Internet and realized I unplugged everything, moved my desk and my cable modem wasn't fully screwed into the cable connection.

---

### Post by melwaltrip on 2009-12-28
OK - you were on the right track. The cables were OK but when I re-booted the router it fixed everything. I don't know how it worked with Windows but not Ubuntu but I am up and operating now. Thank you very much.

---

