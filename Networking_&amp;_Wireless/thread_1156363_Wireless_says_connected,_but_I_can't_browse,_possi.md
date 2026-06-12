---
title: "Wireless says connected, but I can't browse, possible Gateway issue?"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-05-11
Hey guys, I have an older machine I'm trying to get up and running on the internet wirelessly, I have the following Linksys card in this machine:
```
Ralink RT2500
```
That card to my knowledge should work out of the box with Ubuntu and other Linux distributions. For anyone interested here are the results of 
"iwconfig wlan0":
```
wlan0     IEEE 802.11bg  ESSID:"Connection1" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9F:8E:6D:1D   
          Bit Rate=24 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=17/100  Signal level:65/65 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Now in wifi-radar my Gateway was set to "0.0.0.0". So I added a gateway by doing the following:
```
route add default gw 192.168.1.254
```
Once I did that, I then restarted the network by running the following:
```
ifconfig iwlan0 down
sudo /etc/init.d/networking restart
```
Once I restarted the network, still nothing. I still cannot browse. Then I ran the following to see if I'm getting any replies from this ping:
```
ping 192.168.1.254
```
I'm not getting any replies, this is the result of that ping:
```
From 192.168.1.68 icmp_seq=11 Destination Host Unreachable
From 192.168.1.68 icmp_seq=14 Destination Host Unreachable
From 192.168.1.68 icmp_seq=15 Destination Host Unreachable
From 192.168.1.68 icmp_seq=17 Destination Host Unreachable
From 192.168.1.68 icmp_seq=18 Destination Host Unreachable
From 192.168.1.68 icmp_seq=29 Destination Host Unreachable
From 192.168.1.68 icmp_seq=30 Destination Host Unreachable
From 192.168.1.68 icmp_seq=31 Destination Host Unreachable
From 192.168.1.68 icmp_seq=34 Destination Host Unreachable
From 192.168.1.68 icmp_seq=35 Destination Host Unreachable
From 192.168.1.68 icmp_seq=37 Destination Host Unreachable
From 192.168.1.68 icmp_seq=38 Destination Host Unreachable
From 192.168.1.68 icmp_seq=39 Destination Host Unreachable
```
I have another laptop that can connect just fine, although I don't have that with me right now, but I think that's just strange I can't browse but it's saying I'm connected. Let's see if we can get this solved!

---

### Post by panosgr on 2009-05-11
do you have this problem after updating to jaunty?

---

### Post by Crafty Kisses on 2009-05-11
Well the older machine didn't really have an OS, I did put Jaunty on it though.

---

