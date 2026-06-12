---
title: "Vista ICS to Ubuntu weird problem"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by SevenC on 2009-04-05
Hey all. This is the first time I post in here eventho I keep reading and coming for answers every now and then. I'm wondering if I you could help me with this issue I have.. I've spent a lot of time searching and trying to fix it with no luck and I feel like giving up.

I've been trying to share my internet connection with my laptop through my Vista PC. This is my setup:

 These 3 devices connected on a Linksys Switch:

[B]-Laptop: Dual boot Ubuntu 8.10 / Windows XP
-PC: Windows Vista
-Speedstream 5200 ADSL modem[/B]

I configured my Vista connection to the ISP to use the ICS.

So this is what i have right now:
[U]-PC (Vista) can connect to internet without a problem.
-Laptop using Win XP is able to connect to internet.
-Laptop using Ubuntu is not able to connect to internet.[/U]

I have the same config on win Xp and Ubuntu but I'm having problems with the DNS when using Ubuntu.

here is the configuration that I use for both:
ip address: via DHCP
gateway: 192.168.0.1  (My PC with ICS)

So while in Ubuntu I try to establish the connection:

sudo dhclient eth0

```
Listening on LPF/eth0/08:00:44:cc:ac:46
Sending on   LPF/eth0/08:00:44:cc:ac:46
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.99 on eht0 to 255.255.255.255. port 67
DHCPACK to 192.168.0.99 from 192.168.0.1
bound to 192.168.0.99  - - renewal in 226 seconds.
```


ifconfig eth0

```

eth0    Link encap:Ethernet  HWaddr 08:00:44:cc:ac:46
        inet addr: 192.168.0.99 BCast:192.168.0.255 Mask:255.255.255.0
        inet6 addr: fec0::7:a00:46ff:febb:ac40/64 Scope:Site
        inet6 addr: 2002:bd99:e8cc:7:a00:46ff:febb:ac40/64 Scope:Global
        inet6 addr: fe80::a00:46ff:febb:ac40/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:1663 error:0 dropped:0 overruns:0 frame:0
        TX packets:1836 error:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:303211 (303.2 KB)  TX bytes:292124 (292.1 KB)
        Interrupt:11 Base address:0x9c00
```


Here comes the weird thing, I can ping both ways from my laptop to PC, I can even ping external ips from my laptop!! but I cant navigate to the sites, or use any other internet app.
For example, I can

ping google.com -c 1

```
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_sqe=1  ttl=246 time=137 ms
```

also i can
nslookup google.com

```
Server:   192.168.0.1
Address:  192.168.0.1#53

Non-authoritative answer:
Name: google.com
Address: 74.125.67.100
Name: google.com
Address: 74.125.45.100
Name: google.com
Address: 209.85.171.100
```


But if I try to open firefox and navigate to [www.google.com](www.google.com)
it doesnt show anything, the status bar shows this:

[B]Looking up [www.google.com](www.google.com)      (shows quickly then change)
Connected to [www.google.com.mx](www.google.com.mx)  (shows quickly then change)
Waiting for [www.google.com.mx](www.google.com.mx)...   (stays here)[/B]

and it stays there..... now if you see it changed from google.com to google.com.mx  (I live in México)

but I'm not able to see any site or use any internet app.

this is what i have on  /etc/resolv.conf

cat /etc/resolv.conf

```
domain mshome.net
search mshome.net
nameserver 192.168.0.1
```

I already tried appending my ISP DNS servers in here with no luck. What i did was add the next line into **/etc/dhcp3/dhclient.conf**

```
prepend domain-name-servers 200.33.148.217, 200.33.148.209;
```

and restart the connection   sudo dhclient eth0
when its established my /etc/resolv.conf looks like this:

cat /etc/resolv.conf

```
domain mshome.net
search mshome.net
nameserver 200.33.148.217
nameserver 200.33.148.209
nameserver 192.168.0.1
```

but if I try again on firefox it will stay the same...

Waiting for [www.google.com.mx](www.google.com.mx)...


I tried setting the DNS server to the OpenDNS server ips (208.67.222.222, 208.67.220.220) and then I can navigate to SOME sites like [www.google.com](www.google.com) but not for other sites that I need to.

Also I have tried configuring it using NetworkManager with no luck. As I said I have no problems while using the same setup on the same laptop but using Win XP, as you can imagine I'd like to use linux not Win Xp. :(


I'm really frustrated over the fact that I've spent so much time on this, and I cant still figure it out, any help would be really appreciated.

Thanks guys!!

---

### Post by superprash2003 on 2009-04-05
what happens when you try to open [http://74.125.67.100](http://74.125.67.100)
  try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by SevenC on 2009-04-05
> **superprash2003 said:**
> what happens when you try to open [http://74.125.67.100](http://74.125.67.100)
  try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)


When I try to open  [http://74.125.67.100](http://74.125.67.100)  I get the same... **Waiting for 74.125.67.100** in firefox status bar. :(

I disabled IPv6 too, and tried again with no luck. 

I'm getting this when I  

**ip a**

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link 192.168.0.99/24 brd 192.168.0.255 scope global eth0
3: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN link/ether ca:0b:33:d4:ed:0f brd ff:ff:ff:ff:ff:ff
```


I'm wondering if it has something to do with Firefox, but the thing is that I can't use any other internet app.

---

### Post by superprash2003 on 2009-04-06
disable any firewall you have.. just temporarily to see where the problem is, either ubuntu or windows firewall

---

### Post by SevenC on 2009-04-07
> **superprash2003 said:**
> disable any firewall you have.. just temporarily to see where the problem is, either ubuntu or windows firewall

Thanks for the help superprash! I already disabled both firewalls (ubuntu and windows), still having the same problem.

Today in the afternoon I ran ubuntu ultimate live dvd to check whats going on using wireshark, and I found some packets having this:

```
checksum: 0xaa4b [incorrect, should be 0x4e79 (maybe caused by "TCP checksum offload"?)] Bad Checksum: True
```

I'll get the logs tomorrow.

I tried disabling the TCP Checksum offload (and the other options relative to the checksum offload) in Windows Vista (my pc) with no luck... I'm guessing I need to do it on my laptop card not the PC, but I have no idea how to do it in linux. 

I'm googling it tomorrow, hopefully I can find something.

---

