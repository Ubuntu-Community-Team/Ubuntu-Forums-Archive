---
title: "Slow DNS lookups and/or connections"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by HappySegfault on 2006-01-06
Hi all, 

I've got two Ubuntu Breezy machines on my home NAT network.  One of them I reboot into Windows XP Home SP2.  I've noticed that web surfing is much more responsive when in XP than when in Linux.  Firefox in Ubuntu spends a lot of time "Lookup up www.blah.com..."  

I verified that feeling by writing a batch file for XP and matching shell script that simply wget's about 20 different common web addresses, like http://www.google.com/.  The batch file running in XP finishes running in 15 to 18 seconds, while on either Ubuntu setup, it takes anywhere from 32 seconds to over 1 minute.  

I already turned off ipv6 ('lsmod | grep v6' returns nothing).  Just to make sure, I also tried wget with the '-4' option in Ubuntu.  I checked that both XP and Ubuntu are pointed at the same DNS server (my router, 192.168.2.1, which then hits Charter Pipeline's DNS servers).  

I'm running kernel 2.6.12-10-386, and my network adapter is a PCI Linksys tulip card.  Running /sbin/ifconfig after my wget test shows zero errors.  

I'm not new to Linux, but I'm a bit stumped about where to look to fix this.  It's very irritating to have such slow surfing in Linux, when I know the same machine on the same network connection is much faster booted into XP.  

Thanks in advance for any help!

---

### Post by Lambert on 2006-01-07
A couple things to check.

run this command

```
ethtool eth0
```

you'll see something like this.

```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        [B]Speed: 10Mb/s
        Duplex: Half[/B]
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: no

```

speed and duplex could be set wrong. You could be running 100Mb/s on xp and full duplex but only 10baseT and half duplex on linux.

10Mb/s basically your max possible transfer rate, of course 100 is faster/more.
half duplex data transfers only one way at a time creating a bottleneck. full duplex data transfers both ways on link at same time.

To change read the man page for ethtool. The commands are basically

ethtool -s eth0 speed 100
ethtool -s etho duplex full

---

### Post by dcstar on 2006-01-07
[QUOTE=HappySegfault]Hi all, 

I've got two Ubuntu Breezy machines on my home NAT network.  One of them I reboot into Windows XP Home SP2.  I've noticed that web surfing is much more responsive when in XP than when in Linux.  Firefox in Ubuntu spends a lot of time "Lookup up www.blah.com..."  
.......
I'm not new to Linux, but I'm a bit stumped about where to look to fix this.  It's very irritating to have such slow surfing in Linux, when I know the same machine on the same network connection is much faster booted into XP.  

Thanks in advance for any help![/QUOTE]
In Firefox about: config, try changing network.dns.disableIPv6 to true.

---

### Post by HappySegfault on 2006-01-07
[QUOTE=Lambert]A couple things to check.

run this command

```
ethtool eth0
```

you'll see something like this.
[...]
[/QUOTE]

Unfortunately, ethtool doesn't work with the tulip driver.  I get this: 

```
$ sudo ethtool eth1
Settings for eth1:
No data available

```

However, mii-diag does seem to work:

```
$ sudo mii-diag eth1
Basic registers of MII PHY #32:  1000 784c 0000 0000 03e1 cde1 0000 0000.
 The autonegotiated capability is 01e0.
**The autonegotiated media type is 100baseTx-FD.**
 Basic mode control register 0x1000: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised cde1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.
```

So it looks like I'm running 100baseTx, full-duplex.  

Any other pointers?

---

### Post by HappySegfault on 2006-01-07
> In Firefox about: config, try changing network.dns.disableIPv6 to true.

Yep, that's one of the first things my searching around turned up.  I've already got that set.  

Also, note that the problem appears with wget -4.

---

### Post by mips on 2006-01-07
Turn IPv6 off completely and manually specify your DNS servers.
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by HappySegfault on 2006-01-07
[QUOTE=mips]Turn IPv6 off completely and manually specify your DNS servers.
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)[/QUOTE]

I'd already had done that.  See my post---there's no module with "v6" in it loaded.  I manually set my router as the DNS server, and I also tried setting up my ISP's DNS servers.  That didn't help.  

Thanks for taking a stab at it.  

Anyone else have any ideas?

---

### Post by HappySegfault on 2006-01-08
Well, this morning, my series-of-wgets test in Ubuntu Linux is nice and fast.  

Is it possible that my ISP's load conditions (probably light right now) would affect Linux wget more than Windows XP wget?  Seems hard to imagine.

---

