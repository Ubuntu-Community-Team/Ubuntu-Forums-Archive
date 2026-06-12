---
title: "NIC appears in `sudo lspci` but not dmesg, `sudo ifconfig -a`"
date: 2005-02-07
forum: Networking &amp; Wireless
---

### Post by lt_kije on 2005-02-07
Hello world-

I've just found an old PCI NIC of mine laying in a closet and thought to pop it into my desktop running Ubuntu 4.10. The card appears in the output of lspci:
```

$ sudo lspci -vvv
0000:00:09.0 Ethernet controller: Honeywell IAC: Unknown device 8139 (rev 50)
        Subsystem: Realtek Semiconductor Co., Ltd.: Unknown device 8139
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 32, Cache Line Size: 0x40 (256 bytes)
        Region 0: I/O ports at d000 [disabled]
        Region 1: Memory at ee107000 (32-bit, non-prefetchable) [disabled] [size=256]
        Region 2: Memory at <ignored> (32-bit, non-prefetchable) [disabled]
        Region 3: Memory at <ignored> (32-bit, non-prefetchable) [disabled]
        Region 4: Memory at <ignored> (32-bit, non-prefetchable) [disabled]
        Region 5: Memory at <ignored> (32-bit, non-prefetchable) [disabled]
        Capabilities: [10] #41 [0000]
        Capabilities: [d0] #00 [0000]

```

The card doesn't appear in the output of `sudo ifconfig -a` or `dmesg` though, which, combined with the "disabled" entries seen above in the lspci suggest that the card is fried. So why is it (at least partially) in lspci? Anyway to resurrect it?

Thanks,

lt_kije

---

### Post by alastair on 2005-02-07
When you boot - is any kernel module attempting a load to support it? 
What kernel module supports it? (some google research perhaps).
What happens in /var/log/syslog (or messages) when the module loads?

---

### Post by traveler on 2005-02-08
You can find details about your card here:
[http://www.scyld.com/rtl8139.html](http://www.scyld.com/rtl8139.html)

The clue is to manually "modprobe" the device and see if it returns any errors:
```
 modprobe 8139cp 
```

If you get errors - post them :)

Regards
-traveler

---

### Post by lt_kije on 2005-02-09
[QUOTE=traveler]You can find details about your card here:
[http://www.scyld.com/rtl8139.html](http://www.scyld.com/rtl8139.html)

The clue is to manually "modprobe" the device and see if it returns any errors:
```
 modprobe 8139cp 
```

If you get errors - post them :)

Regards
-traveler[/QUOTE]
 Thanks for the help! Here's what happens when I try to modprobe 8139cp...
```

$ tail -fs 2 /var/log/syslog
$ sudo modprobe 8139cp
<syslog registers module: 'kernel: 8139cp: 10/100 PCI Ethernet Driver...'>
$ sudo ifconfig -a
<still just eth0, my wireless card (not the NIC I'm trying to get to work)>
$ sudo ifconfig eth1 up
<Error while getting interface flags: no such device>

```

Thanks again,
lt_kije

---

### Post by alastair on 2005-02-09
It would be useful to know the real messages i.e. full listing of output in syslog when module loads i.e.

In one shell : sudo tail -f /var/log/syslog

In another shell : modprobe 8139cp

(you might need to rmmod it first, if it is loaded)

What gets printed into the syslog?

---

