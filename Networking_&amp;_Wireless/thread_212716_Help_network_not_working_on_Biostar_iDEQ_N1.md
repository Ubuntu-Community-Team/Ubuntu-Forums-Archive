---
title: "Help: network not working on Biostar iDEQ N1"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by greglee on 2006-07-10
Greetings,

I have been looking to switch from WinXP to Linux for a few months now, after buying a new Barebone PC; however, no luck so far, so finally no choice but to jump right in here to seek help.

Latest attempt was installing Dapper Drake 6.06.  Most things work right out of the box, but at the moment got stuck on network installation.

My PC setup is:
BioStar iDEQ N1
  AMD64 3000+
  NVIDIA GeFroce 6100 + nFORCE 410

You can find the product here:
  [http://www.biostar.com.tw/products/barebone/ideq/n1/index.php3](http://www.biostar.com.tw/products/barebone/ideq/n1/index.php3)

Previously it was video and audio problems; it is now working on the new Dapper Drake 6.06.

Ethernet direct connection to another WinXP PC, which connects to Internet via ADSL.  Has setup the WinXP PC to bridge the ADSL to the ethernet port; this connection is verified working, when I dual boot to WinXP on the Biostar PC.

ifconfig shows eth0 with the proper settings (I think, based on what I saw on other posting on this forum).  But the message on the System->Administration->Network Tools, eth0, status: inactive.

Pinging the main PC shows host unreachable.

I notice a number of posts in the forum regarding networking problem on nForce4, have tried many things but still no luck.

Anyone knows a solution or suggest things to try, please reply, thanks.

---

### Post by apjone on 2006-07-10
So you want to share the adsl from your XP machine with your linux machine?
Please list the ipconfig settings on your XP machine and your ifconfig settings on your linux machine. also try as root (or with sudo)

/etc/init.d/iptables stop
ifup eth0
ping *ip address of xp machine*

Also check the firewall on your windows machine and whether it uis et up to share the internet connection.

---

### Post by apjone on 2006-07-10
also check 

[http://www.ubuntuforums.org/showthread.php?t=208565&highlight=Realtek+RTL8201BL](http://www.ubuntuforums.org/showthread.php?t=208565&highlight=Realtek+RTL8201BL)

there may be a drive issue with your NIC.

---

### Post by greglee on 2006-07-10
Wow, that was a fast response, thanks man.  Here are the output from ifconfig and ipconfig:

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:EC:E0:42
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:feec:e042/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:233

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

PPP adapter Prolink 8000:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 219.74.237.68
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 219.74.237.68

---

### Post by greglee on 2006-07-11
Alright, the network is working now, for a reason which I simply can't figure out.  When I got back from work today, and fired up the ubuntu machine, the connection problem simple did not recur.  Hope it stays that way.

---

