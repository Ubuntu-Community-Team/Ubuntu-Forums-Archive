---
title: "wondershaper problem on ubuntu 9.04 - RTNETLINK answers"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by manicmiodrag on 2009-08-28
Hello Ubuntu team slide ):P
 i installed Ubuntu yesterday, so I'm real noob. 

I need Bandwidth Down / Up (kbps) limiter. So I found the address: [http://ubuntu-unleashed.com/2008/05/howto-limit-uploaddownload-speeds-and-optimizeimprove-internet-connection-speed-and-responsiveness-in-ubuntu-linux.html](http://ubuntu-unleashed.com/2008/05/howto-limit-uploaddownload-speeds-and-optimizeimprove-internet-connection-speed-and-responsiveness-in-ubuntu-linux.html) some tools:

1. After read this:

**Howto use Wondershaper:**
Install wondershaper via searching synaptic or [click here to install with 1 click]("apt://wondershaper")
Open a Terminal via Applications->Accessories->Terminal
First figure out how much bandwidth you want to cap it to in kilobits
Of course you should calculate the above settings to what you prefer to shape
**Now once you have the download/upload amounts in kilobits lets shape our traffic:**
wondershaper wlan0 1536 128
Replace wlan0 with your interface, 1536 with your downlink speed, and 128 with your uplink speed.

1.1 i click on link and install wondershaper
2.   then i typed on terminal:
        
```
 ifconfig 
```

eth0   

Link encap:Ethernet  HWaddr 00:15:f2:**:**:**  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:****:cdb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146088 (146.0 KB)  TX bytes:23068 (23.0 KB)
          Interrupt:20 Base address:0x6000 

lo        

Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:208 (208.0 B)  TX bytes:208 (208.0 B)


3. i see my "eth0" and open terminal to write next command:
        ```
 miodrag@miodrag-desktop:~$ wondershaper eth0 256 38 
```    after press enter terminal list whille error:

```

miodrag@miodrag-desktop:~$ wondershaper eth0 256 38
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted
We have an error talking to the kernel

```

did i made a mistake somewhere?

---

### Post by manicmiodrag on 2009-08-28
I found a mistake.
The command "wondershaper wlan0 1536 128" must run as "root", same like others 
man forgot to write :lolflag:
now all works perfect:

```

miodrag@miodrag-desktop:~$ sudo wondershaper eth0 512 52
[sudo] password for miodrag: 
miodrag@miodrag-desktop:~$ 

```**Check the status of wondershaper:**
sudo wondershaper ifacename


terminal and result:

```

miodrag@miodrag-desktop:~$ sudo wondershaper eth0
qdisc cbq 1: root rate 10000Kbit (bounded,isolated) prio no-transmit
 Sent 380992 bytes 2276 pkt (dropped 0, overlimits 1717 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
  borrowed 0 overactions 0 avgidle 781 undertime 0
qdisc sfq 10: parent 1:10 limit 127p quantum 1514b perturb 10sec 
 Sent 103580 bytes 1916 pkt (dropped 0, overlimits 0 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
qdisc sfq 20: parent 1:20 limit 127p quantum 1514b perturb 10sec 
 Sent 277412 bytes 360 pkt (dropped 0, overlimits 0 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
qdisc sfq 30: parent 1:30 limit 127p quantum 1514b perturb 10sec 
 Sent 0 bytes 0 pkt (dropped 0, overlimits 0 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
qdisc ingress ffff: parent ffff:fff1 ---------------- 
 Sent 2626967 bytes 2689 pkt (dropped 304, overlimits 0 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
class cbq 1: root rate 10000Kbit (bounded,isolated) prio no-transmit
 Sent 0 bytes 0 pkt (dropped 0, overlimits 0 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
  borrowed 0 overactions 0 avgidle 781 undertime 0
class cbq 1:1 parent 1: rate 52000bit (bounded,isolated) prio 5
 Sent 380992 bytes 2276 pkt (dropped 0, overlimits 0 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
  borrowed 74 overactions 0 avgidle -67263 undertime -1.62092e+06
class cbq 1:10 parent 1:1 leaf 10: rate 52000bit prio 1
 Sent 103580 bytes 1916 pkt (dropped 0, overlimits 1528 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
  borrowed 0 overactions 1052 avgidle -2303 undertime -1.68385e+06
class cbq 1:20 parent 1:1 leaf 20: rate 46000bit prio 2
 Sent 277412 bytes 360 pkt (dropped 0, overlimits 235 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
  borrowed 74 overactions 38 avgidle -71425 undertime -1.5888e+06
class cbq 1:30 parent 1:1 leaf 30: rate 41000bit prio 2
 Sent 0 bytes 0 pkt (dropped 0, overlimits 0 requeues 0) 
 rate 0bit 0pps backlog 0b 0p requeues 0 
  borrowed 0 overactions 0 avgidle 781 undertime 0
miodrag@miodrag-desktop:~$ 

```



 **Howto disable shaping on specified interface:**
sudo wondershaper clear ifacename

terminal and result:

```

miodrag@miodrag-desktop:~$ sudo wondershaper clear eth0
Wondershaper queues have been cleared.
miodrag@miodrag-desktop:~$ 

```

I like this ubuntu :P

---

