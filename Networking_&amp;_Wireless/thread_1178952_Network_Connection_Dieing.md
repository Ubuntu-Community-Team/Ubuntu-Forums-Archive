---
title: "Network Connection Dieing"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by Samusaaron3 on 2009-06-05
For some reason over the last few weeks, my computer (running 8.04) has started being strange. The network connection (wired, integrated network card) dies after the computer runs for a while (a restart works as a temporary fix.)

When the connection isn't working, the computer still recognizes the existence of the network card, it just acts like it is unplugged (I am using a manual network configuration).

What is my problem?

---

### Post by bluestreek on 2009-06-05
Perhaps the card itself is failing?

---

### Post by Samusaaron3 on 2009-06-05
> **bluestreek said:**
> Perhaps the card itself is failing?

Its possible, though hopefully that isn't the problem.

Anyone else have any ideas?

---

### Post by jonobr on 2009-06-05
maybe try looking at [THIS]("http://ubuntuforums.org/showthread.php?t=1138177"),
although I still think you need to do a bit more wqork to localise the issue.

When the network dies, you should try getting an ifconfig and see how its setup.
Also, try pinging around.
Try pinging 127.0.0.1 or ping localhost

then ping you IP address assigned to the nic (as seen in Ifconfig)

Then try pinging any other devices on the same network,
Then try your router interface (usually 192.168.1.1) 
If all thats working,
try nslookup pingplotter.com
this will check if dns is working correctly.

If it is, try pining the address of pingplotter.com directly and then by name.

Some of this should localise where the issue is.

If you think its hw related, have a look in dmesg and see if that shows any interesting messages regarding your connection

---

### Post by Samusaaron3 on 2009-06-05
Thanks for the reply, I'll try some of your suggestions next time the connection stops working.

Just for comparison reasons, here is the output of ifconfig when my connection is working.

```

eth1      Link encap:Ethernet  HWaddr 00:1f:d0:80:9f:f6  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe80:9ff6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:796 errors:0 dropped:3075630078 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:533651 (521.1 KB)  TX bytes:149172 (145.6 KB)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88408 (86.3 KB)  TX bytes:88408 (86.3 KB)

```

---

### Post by jonobr on 2009-06-05
Hello

I would also recommend (looking at your ifconfig) disable IPv6 on your setup unless you are using it (which you are not)

Theres info in the forums on disabling this.

In fact.
This could be cuasing some of your issues also,

---

