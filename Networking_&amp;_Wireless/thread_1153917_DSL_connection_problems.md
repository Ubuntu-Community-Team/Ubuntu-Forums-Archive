---
title: "DSL connection problems"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by jdr2000 on 2009-05-09
I'm very new to linux, and am wondering if anyone can help me work through some basic problems.  I am using ubuntu 9.04.

Last night I was able to get an ethernet dsl connection up and running.  I installed some updates, then turned off the computer and went to bed.

When I turned the computer on this morning, I can no longer connect.  I tried doing the same thing I did last night to get it to work (sudo pppoeconf), and it went through the same steps but didn't connect me in the end.

I've tried a few different things, including:

Pinging another computer - result was "Address couldn't be found"
pon dsl-provider - tells me that a plugin is loaded and compiled, but still no connection

Can anyone help me establish a connection?  And once that's done, how can I set it up so that it automatically connects every time the computer is started?

Thanks!

---

### Post by superprash2003 on 2009-05-09
you may not me getting an ip address. post output of** ifconfig** from the terminal

---

### Post by jdr2000 on 2009-05-09
ifconfig -a output:

eth0      Link encap:Ethernet  HWaddr 00:0f:3d:88:28:da  
          inet6 addr: fe80::20f:3dff:fe88:28da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:400345 (400.3 KB)  TX bytes:6828 (6.8 KB)
          Interrupt:9 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 56:bb:d4:b1:39:2b  
          inet6 addr: fe80::54bb:d4ff:feb1:392b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)


As I have been continuing to try to figure out this problem, I used pon then plog to see what was happening.  There is an error message in plog:
Timeout waiting for PADS packets
Unable to complete PPPoE Discovery

Not sure if this gives any more insight to possible problems or not???

---

### Post by superprash2003 on 2009-05-10
your eth0 doesnt have an ip.. type **sudo dhclient eth0** in your terminal

---

### Post by jdr2000 on 2009-05-13
That did it - thank you!

Now is there a way to set it up so that my kids can just turn on the computer and use the internet without someone having to go to the terminal for them first?

---

