---
title: "problems with DSL connection linked somehow to CiscoVPN"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by martillu on 2012-07-12
I have a Toshiba z830 with ubuntu 12.04 . I could use without problems the DSL connection at home until today: I was connected with the DSL connection via CiscoVPN doing some work. Then I had to leave the laptop unattended and I guess the laptop tried to go to suspend. When I came back there were many messages on a black screen (see attached picture) and was not responding. I had to reset the laptop. Until here I could not imagine that the DSL connection woun't work anymore, but it didn't.
 
Since I have it with dual boot, I tried to connect with Windows and it worked. I tried again with Ubuntu and it didn't although it says I am connected.
 
The weird thing is that _if I then try to connect via VPN it works again!_ It looks like the VPN connection does something extra that allows me to have access to the internet.
 
These problems are the same independently whether I am using firefox, or skype, etc.
Please help! :confused:
 
Additional info: I could easily reproduce the strange behaviour when going to suspend and being connected via CiscoVPN
Additional info: at work I can use the wireless network but I cannot use other wireless connections. I seem to get internet connection only when I am connected to the net where I work (where I was connected via CiscoVPN when I started to have problems). This means that if VPN is not working I basically have no internet conection at all....very bad :-(

---

### Post by martillu on 2012-07-16
Let me add some more info:

**martillu@ubuntu:~$**  cat /etc/resolv.conf
domain km.icrr.u-tokyo.ac.jp
nameserver 10.240.12.134
nameserver 10.240.12.135
**martillu@ubuntu:~$** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         61.127.116.199  0.0.0.0         UG    0      0        0 ppp0
61.127.116.199  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0

**martillu@ubuntu:~$** ifconfig
eth0      Link encap:Ethernet  HWaddr e8:e0:b7:2f:bc:5a  
          inet6 addr: fe80::eae0:b7ff:fe2f:bc5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17620 errors:0 dropped:1 overruns:0 frame:0
          TX packets:13168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19452232 (19.4 MB)  TX bytes:2568218 (2.5 MB)
          Interrupt:20 Memory:c0700000-c0720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36316 (36.3 KB)  TX bytes:36316 (36.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:219.167.252.226  P-t-P:61.127.116.199  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1454  Metric:1
          RX packets:17608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:18993590 (18.9 MB)  TX bytes:2221195 (2.2 MB)

wlan0     Link encap:Ethernet  HWaddr 9c:b7:0d:d9:21:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I think that:
domain km.icrr.u-tokyo.ac.jp

in the resolv.conf is suspicious, since if I am not connected via CiscoVPN I do not know why it should appear  "km.icrr.u-tokyo.ac.jp" (this is where I connect via VPN)

Please, help this is getting more and more annoying!

---

### Post by martillu on 2012-07-17
I posted it in "ask ubuntu" forum and got solved almost immediately. Here the link:

[http://askubuntu.com/questions/164342/internet-connection-not-working-although-it-says-it-is-connected](http://askubuntu.com/questions/164342/internet-connection-not-working-although-it-says-it-is-connected)

---

