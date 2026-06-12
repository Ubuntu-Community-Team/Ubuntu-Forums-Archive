---
title: "Downloads, streaming video stalling"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by ycason on 2009-08-24
I am having an issue where every time I go to download a large file or stream a video or any other large transfer the download will start strong, but then stall out very quickly.  I've tested my network in multiple ways and it's only affecting the ubuntu computers.  Please help!

---

### Post by ycason on 2009-08-25
Bump.

Update: I have tested both Ubuntu Computers running through the router and direct connection to the cable modem.  I called the cable company and all diagnostics came back positive.  I have tested this with an up to date Jaunty and Karmic install.  This could be a major killer for me, because I need to be able to download large files for my college course.

---

### Post by superprash2003 on 2009-08-26
doed it work well with say a windows machine?

---

### Post by ycason on 2009-08-26
Yes, I can download just fine when I reboot into windows, but I'd rather not have to do that just to download a file.

---

### Post by halitech on 2009-08-30
cable companies lie like cheap rugs (I know, I worked for 1)

what does a test at [http://speedtest.net](http://speedtest.net) give for results?

---

### Post by ycason on 2009-08-30
[[IMG]http://www.speedtest.net/result/552407182.png[/IMG]](http://www.speedtest.net)

I've run this a few times... I get these speeds sometimes and sometimes it won't complete the test.

---

### Post by ycason on 2009-08-30
ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:21:86:9f:06:eb  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:e3:46:9c  
          inet addr:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fee3:469c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116154122 (116.1 MB)  TX bytes:4069357 (4.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-E3-46-9C-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

