---
title: "Wireless pauses but does not show on Network Manager"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by glantela on 2009-08-08
Hi Everyone,

I'm using a Dell Studio laptop with broadcom 4322 wireless controller.  I get this weird pause every 5-10 minutes that lasts about 30 seconds.  It doesnt show any drop in connection on the network manager though.  

It seems to happen more often when i am watching a video on youtube and such.  I was looking at this post: [http://ubuntuforums.org/showthread.php?t=1146367]("http://ubuntuforums.org/showthread.php?t=1146367")
which is similar but not quite the same.  I tried installing Wicd and i couldnt connect at all, same deal with the backports.

Anyone else having this problem? Its quite annoying...

Thanks

---

### Post by glantela on 2009-08-13
Can anyone help me on this?

---

### Post by glantela on 2009-08-13
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:213  Noise level:160
          Rx invalid nwid:0  invalid crypt:367  invalid misc:0

pan0      no wireless extensions.

is it something to do with "not associated"?


Network:

04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

Router:

D-Link DIR-665

---

### Post by superprash2003 on 2009-08-14
well that output means that your not connected to any network.. is this when the wifi doesnt work?? if so , please post same output when your wifi works.. also post output of ifconfig

---

### Post by glantela on 2009-08-14
Nah, that's what it says when i am connected... Although i have been changing some settings on the router and it seems to be working better.  I changed it to select a channel automatically, instead of having it on channel 6 only...  seems a little odd though, as it still says not associated.

---

### Post by glantela on 2009-08-14
It's happening again, so looks like that wasnt the fix.  Arg!

---

### Post by glantela on 2009-08-14
When i ping the router, this is what happens at the pauses....

64 bytes from 192.168.0.1: icmp_seq=134 ttl=64 time=6.31 ms
64 bytes from 192.168.0.1: icmp_seq=165 ttl=64 time=5003 ms
64 bytes from 192.168.0.1: icmp_seq=166 ttl=64 time=3995 ms
64 bytes from 192.168.0.1: icmp_seq=167 ttl=64 time=2987 ms
64 bytes from 192.168.0.1: icmp_seq=168 ttl=64 time=1979 ms
64 bytes from 192.168.0.1: icmp_seq=169 ttl=64 time=971 ms
64 bytes from 192.168.0.1: icmp_seq=170 ttl=64 time=0.611 ms
64 bytes from 192.168.0.1: icmp_seq=171 ttl=64 time=0.919 ms
64 bytes from 192.168.0.1: icmp_seq=172 ttl=64 time=5.77 ms

---

### Post by glantela on 2009-08-18
I just realized you asked for ifconfig, here it is:

eth0      Link encap:Ethernet  HWaddr 00:22:19:f1:a7:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:24:2c:5b:1e:0c  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe5b:1e0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:418
          TX packets:28 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2646 (2.6 KB)  TX bytes:5110 (5.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by DodgeV83 on 2009-08-19
I've had the same problems ever since I got my Dell m1330.  Every new release I install the latest Ubuntu and still experienced the same issues (drop outs for 30 seconds every once in a while).

Unfortunately, I have tried many solutions to no avail.  I don't want to go back to Windows again...for the 4th time...but I rely on my internet connection, so no choice.

---

### Post by DodgeV83 on 2009-08-19
> **glantela said:**
> 

Router:

D-Link DIR-665

I see you're using a D-Link router.  I believe this is the culprit as I am using the D-Link Systems DGL-4500, which is the "gaming" version of yours.

This, coupled with the fact that I have 0 networking problems while on the wireless network at work, indicates an issue with the router...

But what?!

Edit:  I also experience the same problem, though with less frequency, while connected to the router via Ethernet.

---

### Post by glantela on 2009-08-20
i've never actually plugged my laptop into the router, I'll give it a go and see what happens...

Edit: Ethernet works fine!

---

### Post by DodgeV83 on 2009-08-21
> **glantela said:**
> i've never actually plugged my laptop into the router, I'll give it a go and see what happens...

Edit: Ethernet works fine!

In the past I tried using KDE to solve this problem, didn't work.  This time I thought I'd try something different.

Installing WICD and removing the gnome network management worked for me!  I haven't had a single drop out all day yesterday or all day today at least :)

Note:  In the "external programs" tab in WICD, I had to change dhcp to "dhclient" in order to fix an issue where suspend mode would prevent me from connecting again.

Give it a try!

apt-get install wicd

---

### Post by dimsim on 2009-08-30
> **glantela said:**
> Hi Everyone,
 
I'm using a Dell Studio laptop with broadcom 4322 wireless controller. I get this weird pause every 5-10 minutes that lasts about 30 seconds. It doesnt show any drop in connection on the network manager though. 
 
It seems to happen more often when i am watching a video on youtube and such. I was looking at this post: [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)
which is similar but not quite the same. I tried installing Wicd and i couldnt connect at all, same deal with the backports.
 
Anyone else having this problem? Its quite annoying...
 
Thanks
 
This may be of interest to you, I had a similar problem with the 4322G in an HP Mini Note 2140 also under XP. This card would not maintain a reliable connection on any channel initially until updating to the latest HP supplied driver, even then it would drop off randomly and give wild ping times and poor throughput. Changing to another channel (I used 11) on both of my AP's (WRT54GS DD-WRT and Procurve AP530) made a huge difference but I still had the wild ping times and poor throughout so I sent the unit back as in the real world we dont have the luxury of being able to change other ppls AP channel!
 
Following the return of the first netbook I took a chance and got the new HP 5101 which had the 4333AG (i have no idea what the differences are between the two cards). Unfortunately the broadcom card still has some issues but thankfully they are only related to throughput and not connection stability. The throughput using channel 6 was around 1.25MB/sec which doubled to around 2.5MB/sec when using channel 11. I'll keep this one as throughput it not a major consideration for me with this machine and hope that the issues with these cards are discovered and fixed in due course. 
 
So I'm interested in your findings, IMHO this must be an issue with the broadcom 4322 WLAN card and channel 6 (which seems weird) as throughout and connection stabilty appear to be issues regardless of which OS or AP type or which chipset the AP uses.
 
Hope this helps.

---

