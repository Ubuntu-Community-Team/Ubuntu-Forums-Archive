---
title: "ping: unknown host www.google.com"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by wutz on 2010-12-19
I'm a noob so please be patient with me.

I'm running an ubuntu server and I run various cron jobs which scrape internet sites, so it needs to have access to the internet.  They've been running successfully for several weeks, but yesterday these jobs started failing.  I don't remember doing anything relevant to the server at the time that this problem started

I did some checking and tried to learn how to diagnose the problem, but I haven't been able to figure it out yet.  Here are some details:

I can successfully ping ip addresses, for example, google's ip address 209.85.135.105.  When I try to ping [www.google.com](www.google.com) however, I get this error
```
ping: unknown host www.google.com
```

BUT, randomly I will be able to ping [www.google.com](www.google.com) for short ~2 minute intervals every hour or two, but then it stops working again shortly after that

How can I diagnose this problem?

I've included below some info which might be of use, but I have no idea whether it actually will be or not.  I'm just listing everything that I've run in to while searching for things which might be relevant

root@server:/# ifconfig
```

eth0      Link encap:Ethernet  HWaddr 84:2b:2b:4d:be:be
          inet addr:72.20.57.159  Bcast:72.20.57.191  Mask:255.255.255.192
          inet6 addr: fe80::862b:2bff:fe4d:bebe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7807187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13124294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1136152864 (1.1 GB)  TX bytes:18203853994 (18.2 GB)
          Interrupt:36 Memory:da000000-da012800

eth1      Link encap:Ethernet  HWaddr 84:2b:2b:4d:be:bf
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 Memory:dc000000-dc012800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:568813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:46194373 (46.1 MB)  TX bytes:46194373 (46.1 MB)

```

ubuntu version
```

You are using Ubuntu 10.04 LTS
                - the Lucid Lynx - released in April 2010 and supported until April 2013.

```


/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0

iface eth0 inet static
address 72.20.57.159
netmask 255.255.255.192
gateway 72.20.57.190

```


/etc/resolv.conf
```

search staminus.net
nameserver 72.20.1.2
nameserver 4.2.2.1
nameserver 8.8.8.8

```


/etc/nsswitch.conf
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```


I don't have traceroute installed, I tried but since I can't resolve domains apt-get is failing to download it, but I opened up Network Tools and there was a traceroute tab, so I tried tracerouting to various things

"traceroute" [www.google.com](www.google.com)
```

server.staminus.net 72.29.57.159
10.1.100.1  10.1.100.1
10.1.100.1  10.1.100.1
no reply
72.20.0.29  72.20.0.29
216.3.101.245  216.3.101.245
216.156.0.113  216.156.0.113
207.88.13.109  207.88.13.109
no reply
no reply
no reply
no reply
...

```


"traceroute" 209.85.135.105
```

server.staminus.net 72.29.57.159
10.1.100.1  10.1.100.1
10.1.100.1 10.1.100.1
no reply
72.20.0.29  72.20.0.29
216.3.101.245  216.3.101.245
216.156.0.113  216.156.0.113
207.88.13.109  207.88.13.109
no reply
no reply
no reply
no reply
...

```


"traceroute" 8.8.8.8
```

server.staminus.net 72.20.57.159
10.1.100.1  10.1.100.1
no reply
72.20.0.29  72.20.0.29
216.3.101.245  216.3.101.245
216.156.0.113  216.156.0.113
207.88.13.21  207.88.13.21
205.158.79.242  205.158.79.242
12.123.30.18  12.123.30.18
12.122.3.121  12.122.3.121
12.122.137.169  12.122.137.169
no reply
no reply
no reply
no reply
...

```



UPDATE:

here's an example of what the ping output looks like during one of the rare times during which pinging works

ping [www.google.com](www.google.com)
```
PING www.l.google.com (74.125.19.99) 56(84) bytes of data.
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=1 ttl=55 time=10.4 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=2 ttl=55 time=12.4 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=3 ttl=55 time=13.3 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=4 ttl=55 time=11.5 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=5 ttl=55 time=10.2 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=6 ttl=55 time=10.0 ms
--- www.l.google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 6481ms
rtt min/avg/max/mdev = 10.074/11.349/13.349/1.213 ms

```


here's another traceroute i did of [www.google.com](www.google.com), might have been during the time period in which i was actually able to access it, i'm not sure
```

server.staminus.net 72.20.57.159
10.1.100.1  10.1.100.1
10.1.100.1  10.1.100.1
no reply
. 72.20.0.29
216.3.101.245  216.3.101.245
v1400.rar3.la-ca.us.xo.net  216.156.0.113
ae1d0.cir1.sanjose2-ca.us.xo.net  207.88.13.109
no reply
no reply
no reply
no reply

```

and then i tried 30 seconds later and it failed again

---

### Post by 3Miro on 2010-12-19
This is a problem with the DNS servers in /etc/resolv.conf

The last two entries are clearly wrong, did you put them in there or did NetworkManager do that automatically? Do you have any graphical environment installed or are you using command line only?

---

### Post by wutz on 2010-12-19
> **3Miro said:**
> This is a problem with the DNS servers in /etc/resolv.conf

The last two entries are clearly wrong, did you put them in there or did NetworkManager do that automatically?

Someone from the hosting company put them there when they were attempting for like 5 minutes to troubleshoot this issue.  8.8.8.8 i think is the new google dns thing, I think 4.4.4.4 is as well, maybe that's what the 4.2.2.1 is also?


when the problem first arose, and for I believe the entire previous two-three week life of the server, the /etc/resolv.conf file looked like this

/etc/resolv.conf
```

search staminus.net
nameserver 72.20.1.2

```


but this was changed after the problem popped up so I don't think it could be the cause



> **3Miro said:**
> Do you have any graphical environment installed or are you using command line only?

i'm sshed in on putty and in addition I have it running neatx so I'm connected to a remote desktop on the machine





I just did a search for the ips in the resolv.conf and got this
```
Free Public DNS Server

=> Service provider: Google
Google public dns server IP address:

8.8.8.8
8.8.4.4

=> Service provider: GTEI DNS (now Verizon)
Public Name server IP address:

4.2.2.1
4.2.2.2
4.2.2.3
4.2.2.4
4.2.2.5
4.2.2.6

```

---

### Post by 3Miro on 2010-12-19
It looks like an ISP issue. I can ping all of the addresses. Does rebooting the modem help?

The only other thing that I can think of is to comment:
```
#search staminus.net
```

---

### Post by wutz on 2010-12-19
> **3Miro said:**
> It looks like an ISP issue. I can ping all of the addresses. Does rebooting the modem help?

The only other thing that I can think of is to comment:
```
#search staminus.net
```

What are the ramifications if it's an ISP issue?  Is there nothing I can do, just wait and hope someone else fixes it?

Also I don't think I have access to the modem?  I don't know it's a hosted server, it's somewhere else in the world from where I am.  If it's an ISP issue, is it likely that the hosting company would have heard of the problem from others?

Also my server is hosting a website which has been functioning perfectly throughout this problem, so it's still accessible through the internet

---

### Post by wutz on 2010-12-19
Actually more importantly, are there any tests I can run to verify beyond a shadow of a doubt that it actually is an ISP issue?  I just don't want to get caught sitting around for days waiting for someone else to fix a problem when I'm the one who actually needs to do it, while my cron jobs fail to run

---

### Post by wutz on 2010-12-19
Also, what do I have to do once I've made changes to the /etc/resolv.conf file in order to ensure that the system has implemented them?

"/etc/init.d/networking restart" or something?

---

### Post by wutz on 2010-12-19
It started working again for about 30 seconds so i took the opportunity to download/install the actual traceroute and these are the outputs for the successful traceroutes i got before it stopped working again

(successful) traceroute [www.google.com](www.google.com)
```

traceroute to www.google.com (74.125.19.104), 30 hops max, 60 byte packets
 1  10.1.100.1 (10.1.100.1)  1.107 ms  1.515 ms  1.641 ms
 2  . (72.20.0.29)  113.046 ms  113.121 ms  113.184 ms
 3  216.3.101.245 (216.3.101.245)  34.469 ms  34.478 ms  34.472 ms
 4  vb1400.rar3.la-ca.us.xo.net (216.156.0.113)  1.762 ms  2.253 ms  2.279 ms
 5  ae1d0.cir1.sanjose2-ca.us.xo.net (207.88.13.109)  34.722 ms *  34.707 ms
 6  216.156.84.30.ptr.us.xo.net (216.156.84.30)  9.544 ms  9.552 ms  9.472 ms
 7  209.85.243.160 (209.85.243.160)  9.994 ms  9.970 ms  10.106 ms
 8  * 209.85.251.94 (209.85.251.94)  18.132 ms  18.109 ms
 9  nuq04s01-in-f104.1e100.net (74.125.19.104)  10.080 ms  10.081 ms  10.091 ms

```

(successful) traceroute some other website
```

 1  10.1.100.1 (10.1.100.1)  0.673 ms  1.050 ms  1.243 ms
 2  . (72.20.0.29)  12.253 ms  12.327 ms  12.438 ms
 3  216.3.101.245 (216.3.101.245)  0.646 ms  0.641 ms  0.636 ms
 4  * * *
 5  vb15.rar3.dallas-tx.us.xo.net (207.88.12.45)  35.222 ms  35.153 ms  35.210 ms
 6  ae0d1.cir1.dallas2-tx.us.xo.net (207.88.13.125)  34.281 ms  36.257 ms  34.112 ms
 7  ip65-47-204-110.z204-47-65.customer.algx.net (65.47.204.110)  35.763 ms ip65-47-204-30.z204-47-65.customer.algx.net (65.47.204.30)  35.698 ms ip65-47-204-6.z204-47-65.customer.algx.net (65.47.204.6)  35.753 ms
 8  * * *
 9  po6.dar01.sr01.dal01.networklayer.com (173.192.18.211)  36.505 ms  36.549 ms  36.707 ms
10  po1.fcr01.sr01.dal01.networklayer.com (66.228.118.154)  36.438 ms  36.477 ms  36.250 ms
11  66.228.123.113-static.reverse.softlayer.com (66.228.123.113)  36.031 ms  36.002 ms  36.497 ms

```



it seems like successful traceroutes contain a line like this 
```
 2  . (72.20.0.29
```

while unsuccessful traceroutes don't.  what does that mean?



and then i tried again and got this
```
traceroute www.google.com
www.google.com: Name or service not known
Cannot handle "host" cmdline arg `www.google.com' on position 1 (argc 1)

```

---

### Post by jingaling on 2010-12-19
Here are some tests to prove if the problem is your end or the ISP end:

1) Open terminal and ping 72.30.2.43 - if you get a reply then you know your internet connection is fine in terms of basic connectivity. To stop the ping press ctrl+c.

2) In terminal again ping yahoo.com - this should resolve to the IP address above and you should get replies from the ping. Step one works and step 2 doesn't then this proves that this issue is DNS. You are currently using googles DNS as your servers, i would try changing your DNS routing to full DHCP so you get your DNS setting from your router. To do this right click on your connection icon in the panel and select edit connections. Go to the connection that you are using (wired or wireless) then edit the connection so that it is in full DHCP mode rather than DHCP address only mode. Your internet will then disconnect and reconnect. Check to see if it works now.

3) If it still doesn't work then re-boot your router at home and try again.

4) Once the router has rebooted right click on your connection icon again and select connection information. Then go to terminal and try to ping the address of your default route (this is your router). You should get a reply from this - if you do then this proves that your computer is talking to your router so the issue may well be the ISP.

If you get to this point and all the above has failed then this is definitely an issue with your ISP as you have proved you can connect to your router (via step 4), you have proved it's not DNS by having DHCP and Google DNS setup (by the way I am using google DNS now so we know its not down) and you have re-booted your router.

I have just realised - if you cannot contact the hosted/remote server and you can come onto ubuntuforums from the machinw (you may well be using another machine) then it may well be the case that the remote server is down.

Hope this helps.

Jing

---

### Post by wutz on 2010-12-19
> **jingaling said:**
> Here are some tests to prove if the problem is your end or the ISP end:

1) Open terminal and ping 72.30.2.43 - if you get a reply then you know your internet connection is fine in terms of basic connectivity. To stop the ping press ctrl+c.

2) In terminal again ping yahoo.com - this should resolve to the IP address above and you should get replies from the ping. Step one works and step 2 doesn't then this proves that this issue is DNS. You are currently using googles DNS as your servers, i would try changing your DNS routing to full DHCP so you get your DNS setting from your router. To do this right click on your connection icon in the panel and select edit connections. Go to the connection that you are using (wired or wireless) then edit the connection so that it is in full DHCP mode rather than DHCP address only mode. Your internet will then disconnect and reconnect. Check to see if it works now.

3) If it still doesn't work then re-boot your router at home and try again.

4) Once the router has rebooted right click on your connection icon again and select connection information. Then go to terminal and try to ping the address of your default route (this is your router). You should get a reply from this - if you do then this proves that your computer is talking to your router so the issue may well be the ISP.

If you get to this point and all the above has failed then this is definitely an issue with your ISP as you have proved you can connect to your router (via step 4), you have proved it's not DNS by having DHCP and Google DNS setup (by the way I am using google DNS now so we know its not down) and you have re-booted your router.

I have just realised - if you cannot contact the hosted/remote server and you can come onto ubuntuforums from the machinw (you may well be using another machine) then it may well be the case that the remote server is down.

Hope this helps.

Jing



I'm not sure if all of these instructions apply to my situation since the ubuntu server i'm using is hosted remotely, so I don't think I can reboot the router and that sort of stuff

---

### Post by wutz on 2010-12-19
I'm a noob so please be patient with me.

I'm running a remote ubuntu server and I run various cron jobs which scrape internet sites, so it needs to have access to the internet.  They've been running successfully for several weeks, but yesterday these jobs started failing.  I don't remember doing anything relevant to the server at the time that this problem started

I did some checking and tried to learn how to diagnose the problem, but I haven't been able to figure it out yet.  Here are some details:

I can successfully ping ip addresses, for example, google's ip address 209.85.135.105.  When I try to ping [www.google.com](www.google.com) however, I get this error
```
ping: unknown host www.google.com
```

BUT, randomly I will be able to ping [www.google.com](www.google.com) for short ~2 minute intervals every hour or two, but then it stops working again shortly after that

How can I diagnose this problem?

I've included below some info which might be of use, but I have no idea whether it actually will be or not.  I'm just listing everything that I've run in to while searching for things which might be relevant

root@server:/# ifconfig
```

eth0      Link encap:Ethernet  HWaddr 84:2b:2b:4d:be:be
          inet addr:72.20.57.159  Bcast:72.20.57.191  Mask:255.255.255.192
          inet6 addr: fe80::862b:2bff:fe4d:bebe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7807187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13124294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1136152864 (1.1 GB)  TX bytes:18203853994 (18.2 GB)
          Interrupt:36 Memory:da000000-da012800

eth1      Link encap:Ethernet  HWaddr 84:2b:2b:4d:be:bf
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 Memory:dc000000-dc012800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:568813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:46194373 (46.1 MB)  TX bytes:46194373 (46.1 MB)

```

ubuntu version
```

You are using Ubuntu 10.04 LTS
                - the Lucid Lynx - released in April 2010 and supported until April 2013.

```


/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0

iface eth0 inet static
address 72.20.57.159
netmask 255.255.255.192
gateway 72.20.57.190

```


/etc/resolv.conf
```

search staminus.net
nameserver 72.20.1.2
nameserver 4.2.2.1
nameserver 8.8.8.8

```


/etc/nsswitch.conf
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```


I don't have traceroute installed, I tried but since I can't resolve domains apt-get is failing to download it, but I opened up Network Tools and there was a traceroute tab, so I tried tracerouting to various things

"traceroute" [www.google.com](www.google.com)
```

server.staminus.net 72.29.57.159
10.1.100.1  10.1.100.1
10.1.100.1  10.1.100.1
no reply
72.20.0.29  72.20.0.29
216.3.101.245  216.3.101.245
216.156.0.113  216.156.0.113
207.88.13.109  207.88.13.109
no reply
no reply
no reply
no reply
...

```


"traceroute" 209.85.135.105
```

server.staminus.net 72.29.57.159
10.1.100.1  10.1.100.1
10.1.100.1 10.1.100.1
no reply
72.20.0.29  72.20.0.29
216.3.101.245  216.3.101.245
216.156.0.113  216.156.0.113
207.88.13.109  207.88.13.109
no reply
no reply
no reply
no reply
...

```


"traceroute" 8.8.8.8
```

server.staminus.net 72.20.57.159
10.1.100.1  10.1.100.1
no reply
72.20.0.29  72.20.0.29
216.3.101.245  216.3.101.245
216.156.0.113  216.156.0.113
207.88.13.21  207.88.13.21
205.158.79.242  205.158.79.242
12.123.30.18  12.123.30.18
12.122.3.121  12.122.3.121
12.122.137.169  12.122.137.169
no reply
no reply
no reply
no reply
...

```



UPDATE:

here's an example of what the ping output looks like during one of the rare times during which pinging works

ping [www.google.com](www.google.com)
```
PING www.l.google.com (74.125.19.99) 56(84) bytes of data.
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=1 ttl=55 time=10.4 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=2 ttl=55 time=12.4 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=3 ttl=55 time=13.3 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=4 ttl=55 time=11.5 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=5 ttl=55 time=10.2 ms
64 bytes from nuq04s01-in-f99.1e100.net (74.125.19.99): icmp_seq=6 ttl=55 time=10.0 ms
--- www.l.google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 6481ms
rtt min/avg/max/mdev = 10.074/11.349/13.349/1.213 ms

```


here's another traceroute i did of [www.google.com](www.google.com), might have been during the time period in which i was actually able to access it, i'm not sure
```

server.staminus.net 72.20.57.159
10.1.100.1  10.1.100.1
10.1.100.1  10.1.100.1
no reply
. 72.20.0.29
216.3.101.245  216.3.101.245
v1400.rar3.la-ca.us.xo.net  216.156.0.113
ae1d0.cir1.sanjose2-ca.us.xo.net  207.88.13.109
no reply
no reply
no reply
no reply

```

and then i tried 30 seconds later and it failed again



It started working again for about 30 seconds so i took the opportunity to download/install the actual traceroute and these are the outputs for the successful traceroutes i got before it stopped working again

(successful) traceroute [www.google.com](www.google.com)
```

traceroute to www.google.com (74.125.19.104), 30 hops max, 60 byte packets
 1  10.1.100.1 (10.1.100.1)  1.107 ms  1.515 ms  1.641 ms
 2  . (72.20.0.29)  113.046 ms  113.121 ms  113.184 ms
 3  216.3.101.245 (216.3.101.245)  34.469 ms  34.478 ms  34.472 ms
 4  vb1400.rar3.la-ca.us.xo.net (216.156.0.113)  1.762 ms  2.253 ms  2.279 ms
 5  ae1d0.cir1.sanjose2-ca.us.xo.net (207.88.13.109)  34.722 ms *  34.707 ms
 6  216.156.84.30.ptr.us.xo.net (216.156.84.30)  9.544 ms  9.552 ms  9.472 ms
 7  209.85.243.160 (209.85.243.160)  9.994 ms  9.970 ms  10.106 ms
 8  * 209.85.251.94 (209.85.251.94)  18.132 ms  18.109 ms
 9  nuq04s01-in-f104.1e100.net (74.125.19.104)  10.080 ms  10.081 ms  10.091 ms

```

(successful) traceroute some other website
```

 1  10.1.100.1 (10.1.100.1)  0.673 ms  1.050 ms  1.243 ms
 2  . (72.20.0.29)  12.253 ms  12.327 ms  12.438 ms
 3  216.3.101.245 (216.3.101.245)  0.646 ms  0.641 ms  0.636 ms
 4  * * *
 5  vb15.rar3.dallas-tx.us.xo.net (207.88.12.45)  35.222 ms  35.153 ms  35.210 ms
 6  ae0d1.cir1.dallas2-tx.us.xo.net (207.88.13.125)  34.281 ms  36.257 ms  34.112 ms
 7  ip65-47-204-110.z204-47-65.customer.algx.net (65.47.204.110)  35.763 ms ip65-47-204-30.z204-47-65.customer.algx.net (65.47.204.30)  35.698 ms ip65-47-204-6.z204-47-65.customer.algx.net (65.47.204.6)  35.753 ms
 8  * * *
 9  po6.dar01.sr01.dal01.networklayer.com (173.192.18.211)  36.505 ms  36.549 ms  36.707 ms
10  po1.fcr01.sr01.dal01.networklayer.com (66.228.118.154)  36.438 ms  36.477 ms  36.250 ms
11  66.228.123.113-static.reverse.softlayer.com (66.228.123.113)  36.031 ms  36.002 ms  36.497 ms

```



it seems like successful traceroutes contain a line like this 
```
 2  . (72.20.0.29
```

while unsuccessful traceroutes don't.  what does that mean?



and then i tried again and got this
```
traceroute www.google.com
www.google.com: Name or service not known
Cannot handle "host" cmdline arg `www.google.com' on position 1 (argc 1)

```


How can I tell for sure whether this is a problem with my server, or an external problem that I need the hosting company to fix, or their ISP or something?

---

### Post by wutz on 2010-12-19
When I run "nslookup www.google.com" i get this
```
;; connection timed out; no servers could be reached
```

---

### Post by wutz on 2010-12-19
When I run "nslookup www.google.com" i get this
```
;; connection timed out; no servers could be reached
```

---

### Post by howefield on 2010-12-19
Threads merged, please don't post duplicate threads.

---

### Post by wutz on 2010-12-19
UPDATE: i turned off apache2 and the problem corrected itself

why would apache2 be messing up dns lookups when it's turned on?

---

