---
title: "Jaunty ARM Network Configuration"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by digor on 2009-06-15
So I got me one of them there Sheeva Plugs from Marvell. Everything is running smoothly on my local network, but when I go to access the plug (through ssh for example) from the WAN side of things, aka elsewhere (or in my LAN using the WAN IP), I get timeouts on all my services. I have services setup for ssh, http, and ftp.

I have setup port forwarding on my router, and the attached screenshot is my virtual server configuration. As you can see I have setup the router to forward ssh, http, and ftp traffic requests from the internets to my plug. The plug (fujin) is setup to get a static IP (...254). As I said, using the plugs LAN IP for services works dandy, but when I use my WAN IP instead of my LAN IP, I get timeouts.

What's odd is that when I use external port scanning apps (like [http://www.utorrent.com/testport.php?port=80](http://www.utorrent.com/testport.php?port=80)) it shows the ports as open, but my actual services aren't working when I use an appropriate client to access them.

As far as I know, neither ufw nor iptables is installed, but if they were blocking ports then I shouldn't be able to access the services from the LAN either (which I can).

Any help is appreciated, I'm at a loss here.... Some info below for your perusal.

netstat -pl
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:5000          *:*                     LISTEN      17184/rtorrent
tcp        0      0 localhost:mysql         *:*                     LISTEN      9373/mysqld
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      1179/smbd
tcp        0      0 *:www                   *:*                     LISTEN      9627/apache2
tcp        0      0 *:ftp                   *:*                     LISTEN      31328/vsftpd
tcp        0      0 *:ssh                   *:*                     LISTEN      1162/sshd
tcp        0      0 *:6970                  *:*                     LISTEN      17184/rtorrent
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      1179/smbd
udp        0      0 fujin:netbios-ns        *:*                                 1177/nmbd
udp        0      0 *:netbios-ns            *:*                                 1177/nmbd
udp        0      0 fujin:netbios-dgm       *:*                                 1177/nmbd
udp        0      0 *:netbios-dgm           *:*                                 1177/nmbd
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     21924    9373/mysqld         /var/run/mysqld/mysqld.sock

```/etc/network/interfaces
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
        address 192.168.10.254
        gateway 192.168.10.1
        netmask 255.255.255.0
```ifconfig (for giggles)
```
eth0      Link encap:Ethernet  HWaddr 00:50:43:4c:02:26
          inet addr:192.168.10.254  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:325318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:532
          RX bytes:264397732 (264.3 MB)  TX bytes:230984897 (230.9 MB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1462298 (1.4 MB)  TX bytes:1462298 (1.4 MB)

```

---

### Post by digor on 2009-06-16
So I tried setting up a tomcat server on my Windows box to see if it would work. It works in the LAN, as expected. I then setup a virtual server in the router to point to it, and tried to access it via the WAN IP. It did not work...

So I'm thinking this is a router issue now.

---

