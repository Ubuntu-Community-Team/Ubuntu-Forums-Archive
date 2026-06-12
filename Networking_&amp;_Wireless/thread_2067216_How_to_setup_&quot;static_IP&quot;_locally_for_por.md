---
title: "How to setup &quot;static IP&quot; locally for port forwarding"
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by ricomoss on 2012-10-06
I've read through a lot of posts about static IPs but I can't seem to understand them or don't know if they apply to what I'm trying to do.

I have a few machines behind a linksys router.  My ISP is comcast.  One of my machines I use as my Linux "server" - running Kubuntu 12.04.

If I run ifconfig I get:
```
th0      Link encap:Ethernet  HWaddr 00:22:15:88:d0:44  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe88:d044/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15056082 (15.0 MB)  TX bytes:2240890 (2.2 MB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:335156 (335.1 KB)  TX bytes:335156 (335.1 KB)

```

So, I simply configure my router to forward SSH requests to 192.168.1.101 - no trouble.  Now, if I restart my Linux box it will get a different internal IP address and I have to reconfigure my port forwarding to the new IP.  This is quite a hassle.

Is there a simple way around this?

Several of the posts I read made it seem as though they were trying to get their external IPs static, which is not really want I'm wanting to do.  I just need it so that every time my computer restarts it is assigned and internal IP 192.168.1.101.

Can anyone help me figure out how to do this?

---

### Post by ricomoss on 2012-10-06
I was eventually able to find a solution that worked for me.

[Here]("http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/")

---

