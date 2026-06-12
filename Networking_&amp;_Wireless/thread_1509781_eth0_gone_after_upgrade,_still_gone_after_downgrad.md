---
title: "eth0 gone after upgrade, still gone after downgrade"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by pvermees on 2010-06-14
I have a similar problem. My eth0 also disappeared after an upgrade to Ubuntu 10.04, and didn't come back after downgrading back to 9.10. The LEDs on my ethernet port are *not* flashing. Does this mean my network card is dead, or is there any hope I can get back online?

---

### Post by Iowan on 2010-06-14
Moved from [this]("http://ubuntuforums.org/showthread.php?t=1509366") thread.

From a terminal (Applications>Accessories>Terminal) check **ifconfig -a** to see if interface has an IP Address. If not, check **sudo lshw -C network** to get information about interface, drivers, etc. (Post if possible.)

---

### Post by pvermees on 2010-06-15
Thanks for the reply! I reinstalled Ubuntu 10.04 afresh once again. eth0 still doesn't work, and the lights on my ethernet cable are still not flashing. Here is the output of the two suggested commands:

```
pvermees@LTS:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:05:eb:75:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

```
pvermees@LTS:~$ sudo lshw -C network
[sudo] password for pvermees: 
  *-network               
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:0b:04.0
       logical name: eth0
       version: 10
       serial: 00:30:05:eb:75:56
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=1GB/s
       resources: irq:19 ioport:4000(size=256) memory:f0100000-f01000ff
```

---

### Post by Iowan on 2010-06-15
Does (should) the machine get address via DHCP? You might try **sudo dhclient eth0** Keep an eye on the blinky lights - that *should* trigger some activity (possibly brief). 

You might also right-click the Network Manager icon to verify networking is enabled.

---

### Post by pvermees on 2010-06-15
1) No, I use a static IP address.
2) Yes, Networking is enabled (tickmark in the Network Manager).

---

### Post by Iowan on 2010-06-15
Where is the interface configured - */etc/network/interfaces* or in Network Manager?

---

### Post by pvermees on 2010-06-16
I used to use the Network Manager ('IPv4 Settings'), but that doesn't seem to work anymore. The contents of */etc/network/interfaces* look like this:

```
auto lo
iface lo inet loopback
```

---

### Post by yeleek on 2010-06-16
I've a realtek card, though not the same one.  And had a problem since upgrading to 10.04.  Do you dual boot with windows?  If you do there are various threads online about issues like this.  

No obvious fix either when it occurs, other than power off completely (at wall), leave off for 10 secs, power on.  Its to do with this
[http://ubuntuforums.org/showthread.php?t=1465703](http://ubuntuforums.org/showthread.php?t=1465703)

---

### Post by pvermees on 2010-06-16
Unplugging after shutting down did the trick!

Linux may not be perfect, but thanks to forums like this, it's still by far the best operating system.

Thanks a lot guys! Now I can finally get back to work.

---

### Post by Iowan on 2010-06-16
If it's fixed (might want to give it a couple of days), there's one more little [detail]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). ;)

---

### Post by pvermees on 2010-06-17
Done. Just one more piece of information which may be useful to others. I don't have a Windows partition, so the suggestion on [http://ubuntuforums.org/showthread.php?t=1465703]("http://ubuntuforums.org/showthread.php?t=1465703") that the Ethernet problem has something to do with Windows is incorrect.

---

