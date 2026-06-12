---
title: "Expected transfer rate for gigabit ethernet"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by spmurphy on 2010-09-26
Hi,

I have 2 10.04 machines connected through a switch, both with gigabit on board ethernet. Both machines show 1000 Mb/s connections.

When I transfer large files (gig plus up to multi-gig) the maximum I get according to ftp 11472 kB/s.

I did rough computer school math in my head and that seems low but I'll admit I know very little about network transfer rates.

My question is what transfer rates should I expect to get between the 2?

---

### Post by spmurphy on 2010-09-29
Can anyone post their transfer rates for gig ethernet if they have any figures?

That might give me some idea if mine is fubar.

---

### Post by ljw1 on 2010-09-29
There are a heap of variables that go into measuring network speed. Typically the hard drive speed is the limiting factor unless you are running raid or an ssd. For my network I get 40,000KB/s to 100,000KB/s depending on the storage device the files are coming from and going to. Definitely sounds like something is not quite right with your setup.

---

### Post by psusi on 2010-09-29
Sounds like you are only actually connected at 100 mbps.  What are you using to transfer the files?

---

### Post by cj.surrusco on 2010-09-29
> **psusi said:**
> Sounds like you are only actually connected at 100 mbps.  What are you using to transfer the files?

He must be connected with gigabit... He claims transfer rates of 100,000 KB/s, which is 781 megabit.

EDIT: Sorry, I thought you were responding to the post above you instead of the OP.


> **spmurphy said:**
> Hi,

I have 2 10.04 machines connected through a switch, both with gigabit on board ethernet. Both machines show 1000 Mb/s connections.

When I transfer large files (gig plus up to multi-gig) the maximum I get according to ftp 11472 kB/s.

I did rough computer school math in my head and that seems low but I'll admit I know very little about network transfer rates.

My question is what transfer rates should I expect to get between the 2?
That's the same speed that I get with my 100 mbit connections. My best guess is that the switch is only 100 mbit. The speed that the computer reports is only the speed of the Ethernet card, to the best of my understanding.

---

### Post by psusi on 2010-09-30
> **cj.surrusco said:**
> The speed that the computer reports is only the speed of the Ethernet card, to the best of my understanding.

It is supposed to report the actual speed, but there could be a bug, or he could have read the wrong number.

---

### Post by DWsystem on 2010-09-30
What is your HDD RPM?If your HDD is slow,so it is normal.

---

### Post by psusi on 2010-09-30
> **DWsystem said:**
> What is your HDD RPM?If your HDD is slow,so it is normal.

Any hard disk made in the last 10 years can exceed 10 MB/s by a fair margin.

---

### Post by spmurphy on 2010-09-30
Thank you for the replies.

Disk is Intel SSD, switch claims to be gigabit. Magnetic to magnetic solely on the second machine (i.e. without SSD) I was copying multi-gig files at 50MB/s - 70MB/s.

My 1000 Mb/s figure is from the NetworkManager Applet "Connection Information" speed field. It hadn't occured to me that it might only be reporting capability, not connected. It's listed as "Auto eth0", presumably auto-configured/negotiated.

The 11472 kB/s figure is from FTP.

I thought I'd tried direct cabling (i.e. without the switch) but I'll try it again.

---

### Post by psusi on 2010-09-30
What does sudo ethtool eth0 say?

---

### Post by psusi on 2010-09-30
Oh, and check both machines.  Just because one is gigabit doesn't mean the other one is.

---

### Post by msakms on 2010-09-30
I guess eth0 tool isn't installed yet so just type in your terminal:   sudo apt-get install ethtool
and then u can run: ethtool eth0

---

### Post by spmurphy on 2010-09-30
I had ethtool from previous explorations -

SSD machine:
```
# ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Half 1000baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes

```

Machine#2:
```
# ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: yes

```

Those are with the 2 machines connected directly.

If I reconnect them through the switch, Machine#2 changes to:
```
# ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: yes

```

That looks odd; I thought I'd seen the link partner advertised link modes on the 2nd machine, but I could be mistaken.

Connected back to back, one shows 1000, the other shows 100 with ethtool, yet they talk just fine? I don't know enough networking to know if that's OK or not.

When I connect them both to the switch the 2nd one goes to 1000 yet I still only get 11345kB/s with ftp.

On the 2nd machine I tried to use ethtool to set it to 1000 but either I did it wrong or it didn't stick -

```
ethtool -s eth0 speed 1000
```

(I think that was what I used; the command didn't complain but the speed stayed listed as 100 - obviously this was when they were back to back connected.)

---

### Post by endotherm on 2010-09-30
make sure both your cables are Cat5E or better. cat5 (no E) maxes out at 100mb speeds. they are both plugged into the same switch, right?

---

### Post by spmurphy on 2010-09-30
The cable I used to connect them back to back might be cat5.

They're both into the same switch, all cables into the switch are cat 6 utp patch.

---

### Post by psusi on 2010-10-01
Whoa, that is goofy.  When connected to the switch, they can both link at different speeds, but when connected directly to each other, they can't be using different speeds.

I wonder if the first machine has a buggy driver that always reports 1000 even though it is actually only 100.

---

### Post by endotherm on 2010-10-01
does 
```
sudo lshw -C Network
``` show the same driver for both cards, and agree with ethtool?

---

### Post by spmurphy on 2010-10-01
> **endotherm said:**
> does 
```
sudo lshw -C Network
``` show the same driver for both cards, and agree with ethtool?

When they're back to back or through the switch?

I've got a cat 6 crossover now too so I can try them without the other crossover (which might well be cat 5).

---

### Post by psusi on 2010-10-01
Then try the cat 6 crossover.  If they still report different speeds with that, then one of the drivers must be bugged.  If you still only get ~11,000 kb/s transfers then I'd say the bugged one is the one claiming to be running at 1000mbps.

---

### Post by endotherm on 2010-10-01
> **spmurphy said:**
> When they're back to back or through the switch?

I've got a cat 6 crossover now too so I can try them without the other crossover (which might well be cat 5).
lshw output shouldn't change much based on current connection state, so it probably doesn't matter.

---

### Post by spmurphy on 2010-10-01
SSD machine :
```

  *-network
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:07:04.0
       logical name: eth0
       version: 10
       serial: 90:e6:ba:00:b7:62
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.64 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1GB/s
       resources: irq:22 ioport:e800(size=256) memory:f7fffc00-f7fffcff memory:f0e00000-f0e1ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Non-SSD machine:
```

  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:1f:c6:37:2b:9f
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.70 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:28 memory:febfc000-febfffff ioport:e800(size=256) memory:febc0000-febdffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

This is with them connected to the switch.

I'll try the crossover shortly.

---

### Post by spmurphy on 2010-10-01
Hmm. Last night I physically unplugged them both from all power.

```

ftp> get 00001.m2ts
local: 00001.m2ts remote: 00001.m2ts
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for 00001.m2ts (140052480 bytes).
226 Transfer complete.
140052480 bytes received in 2.15 secs (63613.7 kB/s)

```

I'm guessing that fixed it.

I'd heard depriving them of all power would reset crap network adapters but never actually seen it before.

Thank you all very much for your replies, if nothing else I learned some more commands :)

---

### Post by endotherm on 2010-10-01
well that is odd, both cards are using what appear to be gigabit capable drivers, and are set to autonegotiate. I think that may be the problem, though ethtool believes that both are running full dup. autoneg across multiple vendors can be problematic, so the rule generally is that if you can configure it on both ends, do so. 

AHH! this might be the problem:
[http://www.tomshardware.com/forum/117683-28-gigabit-crossover-connection](http://www.tomshardware.com/forum/117683-28-gigabit-crossover-connection)
check down a couple posts. a few guys are claiming that crossover cable automatically downgrades the throughput, though I can't guarantee that that is the case.

---

### Post by psusi on 2010-10-01
I have a realtek nic as well and it also sometimes needs the power pulled to get it to stop acting up.  At least it's working right now.

---

