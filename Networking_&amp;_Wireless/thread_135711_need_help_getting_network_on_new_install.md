---
title: "need help getting network on new install"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by David22 on 2006-02-24
I recently installed Ubuntu on a second hard drive in my computer. On my windows hd I am completely connected to my home network via ethernet cable, and can reach the internet. Ubuntu is new to me, and I can't figure out how to get it hooked up like windows. Can anyone help?

it detects a connection labled eth0, but activating it does nothing

---

### Post by andrewsawyer on 2006-02-24
can you go to terminal at type 'ifconfig' and post the output?  If you have activated it, and set it to use the DHCP server (assuming you aren't using a static IP) it should be working fine.

---

### Post by David22 on 2006-02-25
This is what ifconfig gives me:

eth0        Link encap:Ethernet  HWaddr 00:13:8F:3F:54:8A
              inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
              inet6 addr: fe80::213:8fff:fe3f:548a/64 Scope:Link
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:124 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:2 dropped:0 overruns:0 carrier:2
              collisions:0 txqueuelen:1000
              RX bytes:40054 (39.1 KiB)  TX bytes:0 (o.o b)
              Interupt:17 Base address:0xe400

lo            Link encap:Local Loopback
              inet addr:127.0.0.1 Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:232 errors:0 dropped:0 overruns:0 frame:0
              TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:19748 (19.2 KiB)  TX bytes:19748 (19.2 KiB)


What do you have to do to set it up with the DHCP server? Does it require more than changing the tab to 'DHCP' in ethernet connection properties?

---

### Post by andrewsawyer on 2006-02-25
No - that should be it.  Assuming that you have clicked the DHCP button before printing this, it looks to have done its job.  The DHCP server has assigned Ubuntu the IP address 192.168.0.106.

Unless anyone else can see anything I'm missing, I don't see why it shouldn't be working fine right now.

---

### Post by jamesr on 2006-02-25
It looks as if you connected to the DHCP server because you have an address> inet addr:192.168.0.106 Bcast:192.168.0.255 Mask:255.255.255.0


Can you ping the router
ping 192.168.0.xxx could be xxx=1 but you should be able to find that info in the router manual.

if yes 
post the output of

cat /etc/resolv.conf

---

### Post by David22 on 2006-02-26
the readout:

64 bytes from 192.168.0.106: icmp_seq=1 ttl=64 time=0.045 ms

means it pinged it right?

entering cat /etc/resolv.conf returns

search hsdl.az.comcast.net.
nameserver 192.168.0.1

---

### Post by jamesr on 2006-02-26
The Ping looks ok, I personally would leave it running longer, because I seen problems with windows system talking to an embedded PC  that seems to take at least 3 good pings in a row before one can trust the link.

But the /etc/resolv.conf does not right

 > 
search hsdl.az.comcast.net.
nameserver 192.168.0.1

The nameserver should one from your ISP unless you are on a corporate network.

My are 
Nameserver xx.226.10.193
nameserver xx.226.1.93

these from my ISP

As a further check 
ping [www.google.com](www.google.com)

---

### Post by David22 on 2006-02-26
pinging google.com at 216.239.39.99 returns:

PING 216.239.39.99 (216.239.39.99) 56(84) bytes of data.
From 192.168.0.106 icmp_seq=2 Destination Host Unreachable
From 192.168.0.106 icmp_seq=3 Destination Host Unreachable
From 192.168.0.106 icmp_seq=4 Destination Host Unreachable

--- 216.239.39.99 ping statistics ---
5 packets transmitted, 0 recieved, +3 errors, 100% packet loss, time 3999ms
, pipe 3

i appreciate the help jamesr.

---

### Post by jamesr on 2006-02-26
Have you got the information re the nameserver from your ISP, it is often on the ISP home page. and comment out the reference to 192.168.0.1 which your router.

---

