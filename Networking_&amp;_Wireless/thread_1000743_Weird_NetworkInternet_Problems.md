---
title: "Weird Network/Internet Problems"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by shatogtar on 2008-12-03
Hi there I am experiencing some network trouble and cant find any solution for it. I tried but no chance.

My specs:
OS: Ubuntu 8.10
Mainboard: ASUS P5K-E WIFI-AP
Router: D-Link DI-524
Internet: Unity Media 2Play 16000 (16 MBit/s through TV-Cable)

My Problems:
W-Lan Connectivity is always 16%,
The Internet speed is low sometimes, 
sometimes the Websites time out, 
downloading via Bittorrent is very slow,
When I connect my Router with my PC through an additional Lan-Cable Internet stops working 

I did a "ping -c 100 google.com"
and this was the result:
[IMG]http://img367.imageshack.us/img367/6858/screenshot4hk3.png[/IMG]

in the pinging process two abnormalities like this showed up:
[IMG]http://img389.imageshack.us/img389/5686/screenshot1bt0.png[/IMG]

There are IP's where there should be adresses which leads me to the assumption that this could be a DNS problem, couldnt it?

And here the Failure Message I receive when Internet stops working
[IMG]http://img360.imageshack.us/img360/6849/screenshot5vw6.png[/IMG]

I did numerous Speed tests, all with nearly equal results:
Download: 6500 kbit/s   
Upload:   1000 kbit/s
Which is too slow for my 16 Mbit/s Connection although I would be happy if at least this would be running properly.

My Provider says that the 16 Mbit/s are working. Something in my Preferences must be wrong but they can`t help me.

Does anybody know what this could be? I would very much appreciate it. I recently switched to ubuntu, finding myself an idiot for not having changed long ago. Its very comfortable and beautiful. But this little internet problem is beginning to grind my gears ;) 

thx in advance

(PS: I needed approx. 2 hours to register here, upload the pictures etc. due to the loss of internet connection and connectivity problems)

---

### Post by s3gfault on 2008-12-03
Can you explain what you mean by this part:
> When I connect my Router with my PC through an additional Lan-Cable Internet stops working 
Also, have you tried connecting your PC by ethernet to the cable modem directly?

---

### Post by shatogtar on 2008-12-03
> Can you explain what you mean by this part
Im normally using Wireless Lan. But for testing purpose I tried to connect my Computer to my Router with a normal Lan Cable.

Now I just tried to make the connection between Modem and PC, as you said but same problem. Internet stops working.

---

### Post by superprash2003 on 2008-12-03
what is your MTU value?? post your ifconfig output

---

### Post by shatogtar on 2008-12-03
MTU Value: 1500 (set to Auto)
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:6b:bb:aa  
          inet6 addr: fe80::21b:fcff:fe6b:bbaa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:764 (764.0 B)  TX bytes:9857 (9.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149392 (149.3 KB)  TX bytes:149392 (149.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:0f:9d:c4  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe0f:9dc4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:275243859 (275.2 MB)  TX bytes:35418050 (35.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-0F-9D-C4-64-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



any suggestions? This says nothing to me.

---

### Post by shatogtar on 2008-12-03
Ok just read the "How to post a wireless issue"-Thread so here's some more information:

from lspci:
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)

from lsusb:
Bus 004 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

from iwconfig:
wlan0     IEEE 802.11bg  ESSID:"rocket_sauce"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1B:11:A5:35:6A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=16/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by superprash2003 on 2008-12-04
im not sure if this would work.. but you could give it a try.. try changing your mtu values [http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by shatogtar on 2008-12-07
Okay for some days now it worked quite well. Not the 16 Mbit/s I am paying for but at least something around 8 Mbit/s, though I had to reboot sometimes to get access to the W-Lan again.
But now again: internet is very slow and I get kicked out of W-lan all the time.
Any Ideas?

---

### Post by razy60 on 2008-12-07
Can you access the router to see what is going on,
Check the time+date and time zone.(tells you if there is a isp problem and not a pc problem).
Do all the address lines look correct, i.e dns.dhcp,etc(none are full of zeros unless they should be).
Essentially your router is not actually suffering any problems.
The old favorite have you switched the router off left it for a while then switched it back on,(this normally clears any logs, occasionally if a log file gets full it affects the router).

one thing to try manually set mtu in network manager to the same as the mtu in your router don't rely on the auto setting.

Raz

---

### Post by shatogtar on 2008-12-07
Hi there,
I can access the router
Time, Date, Timezone is correct
By adresses you mean this:?
[IMG]http://img247.imageshack.us/img247/6946/screenshot1ma2.png[/IMG]

Changed my MTU Value back to 1500.
So What now?

And why is my Wlan adapter shown in the "lsusb"?
It's an on-board-device.

---

### Post by razy60 on 2008-12-07
do you know if your isp uses Pppoe, also as you have 16mb is connection cable(fibre optics).
i would have expected to see something in the ip box not just 0's
What is in the wireless box.

Raz

---

