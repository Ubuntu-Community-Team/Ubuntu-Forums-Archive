---
title: "Belkin F5D6001 working but über slow."
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by -X- on 2006-06-02
I have a wireless PCI card (Belkin F5D6001 rev 3) which seems to be "working", but I'm only able to transfer data at about 1KB per second.

I have a Dapper Beta system with XGL running currently. 
X2 3800+ | 2GB o' RAM | X1800 XL | Asus A8V-E SE | SB Extigy

Any takers? Guesses? Bets? Anyone? What about installing the "final" Dapper?

---

### Post by -X- on 2006-06-05
Am I forced to go down the ndiswrapper route? I did notice this thread, but...

[http://www.ubuntuforums.org/showthread.php?t=144659&highlight=Belkin+F5D6001](http://www.ubuntuforums.org/showthread.php?t=144659&highlight=Belkin+F5D6001)

... It didn't enlighten me too much.

---

### Post by -X- on 2006-06-08
[[IMG]http://img428.imageshack.us/img428/7049/screenshot1oi.th.png[/IMG]](http://img428.imageshack.us/my.php?image=screenshot1oi.png)

I'm not quite feeling the love here. A fresh install of Dapper (final) fixed a couple of my non-wlan-related problems but my wlan problem still persists. What can I say? No WEP is being used, in XP the speed and signal is quite good (hits the 4mbit cap of my internet connection).

Stay tuned for the next episode of...

---

### Post by danielph on 2006-06-23
Hi,

I am curious if you managed to resolve this issue or continues with ndis? I have a 2 machines each with Belkin wireless using ralink chipset. I can only get them talking at 1.3Mbs over a 54Mbs wireless setup. See [http://ubuntuforums.org/showthread.php?t=202256&highlight=slow](http://ubuntuforums.org/showthread.php?t=202256&highlight=slow)

What chipset are you using? If it is ralink maybe this will help 
[http://ubuntuforums.org/showthread.php?t=201539&highlight=slow](http://ubuntuforums.org/showthread.php?t=201539&highlight=slow)

Or maybe it is a IPv6 problem
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Regards

Dan

---

### Post by -X- on 2006-08-01
Thanks for your reply, and sorry for the delayed response :) I'm still not 100% sure about what's causing it, but alot of packets seem to be getting dropped.

ifconfig:
[I]
wlan0     Link encap:Ethernet  HWaddr 00:30:BD:4E:97:EC
          inet addr:80.186.72.235  Bcast:80.186.95.255  Mask:255.255.224.0
          inet6 addr: fe80::230:bdff:fe4e:97ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5577 errors:0 dropped:22902 overruns:0 frame:0
          TX packets:4438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5695535 (5.4 MiB)  TX bytes:507938 (496.0 KiB)
          Interrupt:82 Memory:f8906000-f8906100
[/I]

According to iwconfig the quality of the link is constantly jumping between 1 and 99 quality whenever it is transferring data. If no data is being transmitted/recieved then the quality is reported as 99 (or so), constantly.

---

### Post by crionox on 2006-08-05
I'm also curious about this.  I don't have a belkin card, but mine appears to be doing the same thing.  Just got a new laptop and decided to go ubuntu, and right now i'm just trying to download the updates (and it is choking from the lack of dataflow).

---

### Post by danielph on 2006-08-05
This does not sound like the same issue I am experiencing. I am getting plenty of bandwidth for internet. My internet connection is 2MB which is giving me 240kb/s download max. My wireless card is running at 1.3MBs up and download all the time, so it is not an issue as the card is always faster then the internet connection. My problem is only apparent when I talk over the network to another machine. Here I continue to get 1.3MBs which is slow over a LAN. I would expect 54MBs. My old card was a dlink which gave me 22MBs.

This is with both machines having a full signal, no packet loss or errors. I still havent found a solution for this and tend to transfer large files through a large USB drive.

Regards

Dan

---

