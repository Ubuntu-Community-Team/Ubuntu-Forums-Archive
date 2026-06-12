---
title: "requesting a network address / network has been disconnected"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by Hawkman on 2009-01-14
Hello, new poster, new to Ubuntu, though I was raised on AT&T Unix shell so I'm looking forward to the experience. A week ago I installed Ubuntu release 8.10 on an old AMD Sempron box with 1G RAM. I'm having a few little problems, the most troublesome of which is connecting to my wireless network. 

My D-Link wireless router *sees* the Ubuntu desktop computer. I know this because from my laptop (Vista) I look at the connections to the router, and it includes "computer-room-desktop," which is the name of the machine with Ubuntu on it. Further, my desktop computer *sees* the network. I just can't get the two to talk. When I click on the network icon, I get "Requesting a network address from Bubba Gump Shrimp Company" which is my network name. I see the animated icon that indicates it's trying to connect. Then it says, "Network has been disconnected." I'm afraid I can't physically connect to the network because my house is not wired for ethernet, and I don't have a 100' ethernet cable. What can I post here that would provide information needed to figure out what is wrong? Thanks in advance. 

-Hawkman

---

### Post by xeidy on 2009-01-15
I have similar problem. I connects fine at startup.. work perfectly for few minutes and then all of a sudden it disconnects and does not connect at all.

I've read the forums I found that one person got it fixed by removing lm-sensors but as i think i don't have it installed. And yet i'm facing this problem on my laptop which has Atheros Wireless. I know for fact that it works fine on ubuntu but after it disconnects i don't know what's the problem. I could still see and scan the networks but not connect to any.

as many other people have suggested that it is problem with the newer version of network manager. Can anyone experienced here help by suggesting something that would help?

Thank.

---

### Post by superprash2003 on 2009-01-15
is dhcp enabled in the wifi router?? you could try connecting via static ip.. if not go to the terminal and post output of 
1)ifconfig
2)iwconfig

---

### Post by xeidy on 2009-01-16
that didn't work at all. :(

---

### Post by superprash2003 on 2009-01-16
ifconfig and iwconfig outputs?

---

### Post by xeidy on 2009-01-17
```
ifconfig


eth0      Link encap:Ethernet  HWaddr 00:1d:ba:84:30:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:d7:e2:23  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fed7:e223/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:657729 (657.7 KB)  TX bytes:109292 (109.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E1-D7-E2-23-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HomeNetwork"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:21:91:E9:9B:27   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=73/100  Signal level:-48 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by xeidy on 2009-01-17
is there anyone who can figure something out?? please !

---

### Post by xeidy on 2009-01-18
bump

---

### Post by Hawkman on 2009-01-29
My problem was solved by ditching the old Linksys WUSB11 v2.4 NAU and getting the cheapest new one I could find locally, a Belkin. Did a fresh install of Ubuntu 8.10, plugged in the new device, and presto, I has internets. 

:popcorn:

---

