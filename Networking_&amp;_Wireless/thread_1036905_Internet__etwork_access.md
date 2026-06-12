---
title: "Internet / etwork access"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by mgdwcb on 2009-01-11
I began a thread a few days ago but apparently it got corrupted...anyway I am having problems accessing the internet.  I succeeded in getting my IP pinged with no errors. I noticed on the Network options that "Multicast" was disabled. I wonder if that is the problem?

---

### Post by ugm6hr on 2009-01-11
Did the LiveCD ethernet connection work?

When you say that you can ping - ping from where to where?

```
ping -c 3 216.239.59.147
ping -c 3 www.google.co.uk
```

Other details that might be useful (output from):
```
lspci
lshw -class network
```

Also - what kind of modem are you using?

---

### Post by mgdwcb on 2009-01-11
thanks for the reply.

My modem is a Draytek Vigor 2800

LiveCD earthnet connections work on Knoppix and Gentoo.

I pinged my IP addrdess only on the Ping tab of Network Tools.

The output below may be of interest:


05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

  description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth1
       version: 13
       serial: 00:15:f2:d3:30:0d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 52:2f:d7:74:9c:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by ugm6hr on 2009-01-11
I'm afraid you will have to give more details.

Above commands & also:

```
ifconfig
```

Pinging your computer's IP from itself doesn't prove anything.

Could you get online with your modem using Gentoo / Knoppix?

---

### Post by mgdwcb on 2009-01-12
Here's what I get for ifconfig

eth0      Link encap:Ethernet  HWaddr 00:15:f2:d3:14:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:15:f2:d3:30:0d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1166 (1.1 KB)  TX bytes:1038 (1.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45120 (45.1 KB)  TX bytes:45120 (45.1 KB)

My router is a Draytek Vigor 2800

I have several live CDs, including Knoppix 5.1.1 and gentoo which both access the internet just fine.  

Hope this helps.

---

### Post by mgdwcb on 2009-01-12
ok this is strange....I am now online :)

The only thing I can think of is that at logon just now there was a message "routine check of drivers"? And then I was wired to the network.

Though for future reference it would be interesting to know just what happened. 

Thanks for help again.

---

### Post by ugm6hr on 2009-01-12
> **mgdwcb said:**
> Though for future reference it would be interesting to know just what happened. 

No idea, I'm afraid.

---

### Post by mgdwcb on 2009-01-12
Well I spoke too soon.  My connection lasted for about 1 hour, during which time I downloaded ubuntu updates ok.  But when I restarted I had the same "The network connection has been disconected" message, as it did before. My connection is stable on the LiveCDs so I don't think its a problem with connections or the router.

---

### Post by mgdwcb on 2009-01-15
The problem is finally solved. The ubuntu DVD was double-sided, with 32 bit version on one side and 64 bit on the other. I originally installed the 64 bit version but when I installed the 32 bit everything was fine. Internet access now ok.

---

