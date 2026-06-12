---
title: "How do I share a usb  GPRS/EDGE modem btwn 2 laptops"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by 4partee on 2009-04-07
Wife and I are setting out on a three-month drive-about of the US Southwest.  We each have a laptop but only one GPRS/EDGE enabled cell phone with T-mobile.

We would like to be able to connect one laptop with T-Mobile and be able to access the internet from both laptops.  

I have searched this forum and have not been able to figure out what to do.  

I am at home right now and connected to T-mobile via usb to cell phone:
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.178.221.81  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:74 (74.0 B)  TX bytes:107 (107.0 B)

What do I need to do to allow my wife's laptop to share this connection?

I ran this before making the T-Mobile connection:
root@shuttle2:/home/gelmjw# /etc/dbus-1/event.d/25NetworkManager stop

More info:
root@shuttle2:/home/gelmjw# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.6.6.6        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
root@shuttle2:/home/gelmjw# 

gelmjw@shuttle2:~$ tail /var/log/messages
Apr  7 22:01:52 shuttle2 pppd[6617]: Connect: ppp0 <--> /dev/ttyACM0
Apr  7 22:01:53 shuttle2 pppd[6617]: PAP authentication succeeded
Apr  7 22:01:53 shuttle2 kernel: [  362.074470] PPP BSD Compression module registered
Apr  7 22:01:53 shuttle2 kernel: [  180.961680] PPP Deflate Compression module registered
Apr  7 22:01:53 shuttle2 pppd[6617]: local  IP address 10.178.221.81
Apr  7 22:01:53 shuttle2 pppd[6617]: remote IP address 10.6.6.6
Apr  7 22:01:53 shuttle2 pppd[6617]: primary   DNS address 66.94.9.120
Apr  7 22:01:53 shuttle2 pppd[6617]: secondary DNS address 66.94.25.120
Apr  7 22:17:58 shuttle2 -- MARK --
Apr  7 22:37:58 shuttle2 -- MARK --
gelmjw@shuttle2:~$

---

### Post by 4partee on 2010-09-23
I finally got this to work!

---

