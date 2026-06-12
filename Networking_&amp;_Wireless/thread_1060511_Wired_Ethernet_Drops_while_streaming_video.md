---
title: "Wired Ethernet Drops while streaming video"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by rahduke on 2009-02-04
Hi all... I'm running 8.10 currently and im having connection issues. My connection drops randomly while streaming video to my wireless htpc and xbox running XBMC. It also fails occasionally when downloading, I've tried a different card replaced my verizon fios router and all the cables. Nothing has worked, searched everywhere for help couldn't find the same problem. 

I'm using the onboard NIC on ASUS P5GC-MX board.

---

### Post by Crafty Kisses on 2009-02-04
What are the results of this command?
```
ifconfig
```

---

### Post by rahduke on 2009-02-04
rahduke@rahduke-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1d:60:2a:12:c1  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe2a:12c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1037349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:925054 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:1000430396 (1.0 GB)  TX bytes:780673578 (780.6 MB)
          Memory:dbfc0000-dc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5624 (5.6 KB)  TX bytes:5624 (5.6 KB)
 

should i have used pastebin?

---

### Post by rahduke on 2009-02-05
bump...

---

### Post by rahduke on 2009-02-06
someone.... anyone?

---

### Post by punx45 on 2009-02-06
i would typically look at the wireless as the suspect before anything else.   are there any factors that may cause intermittent interference?  wireless phones, other devices, etc?   are other people/devices using the wireless at the same time?

if not that, what are some other specs of the machine that you are streaming the video off of?   is it old? slow disks?   these could be factors as well.

finally, the video you are watching could be an issue as well.   if you are watching a high bitrate video, HD, maybe even DVD quality mpeg2, it is possible that it exceeds the available bandwith.

---

### Post by rahduke on 2009-02-07
Thanks for the response Punx, however both the streaming box and xbox are wired through my router there is no wireless connection happening. 

The computer I'm streaming from is relatively new core2duo 2.6 running on an Asus P5GC motherboard w/ 4 gigs of ram and 3 SATA HDs.

I've replaced the router from Verizon Fios, tried multiple NIC cards and replaced the cables. 

My connection seems to drop even more frequently right now, regular browsing and chatting is even knocking it out (4x today). 

I think it's the driver, but i have no idea how to identify, let alone replace the driver... can anyone help?

---

### Post by punx45 on 2009-02-09
are you back to using the on board NIC?   looks like some people were having issues with it using Debian Etch a while back.   

[http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg02140.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg02140.html)

i didnt read most of this, but it looks promising:

[http://www.linuxquestions.org/questions/linux-hardware-18/attansic-ethernet-card-not-detected-584877/](http://www.linuxquestions.org/questions/linux-hardware-18/attansic-ethernet-card-not-detected-584877/)

---

