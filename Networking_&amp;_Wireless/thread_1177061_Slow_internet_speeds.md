---
title: "Slow internet speeds"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by spleblem on 2009-06-03
hey
just upgraded to 64bit ubuntu 9.04 and am now getting slow internet speeds around 40kbs instead of the normal 300kbs which i was getting on 32bit
anyhelp would be great 
here is the out put for ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:22:15:35:14:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:63:1b:89  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe63:1b89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1858654 (1.8 MB)  TX bytes:421240 (421.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-63-1B-89-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

thanks for nay advice you can give
also i'm fairly new to linux

---

### Post by superprash2003 on 2009-06-03
try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by spleblem on 2009-06-03
i have tried this but it does not seem to work
i added it to the file and saved
but when i type ip a | grep inet6
i get
```
    inet6 ::1/128 scope host 
    inet6 fe80::211:50ff:fe63:1b89/64 scope link 

```

im assuming this is an output and its not working.
internet speeds are still slow.

---

### Post by dmizer on 2009-06-03
> **superprash2003 said:**
> try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

Since IPv6 is a part of the Jaunty kernel (not a module) the above fix won't work anymore.

Try this: [http://ubuntuforums.org/showpost.php?p=7059555&postcount=24](http://ubuntuforums.org/showpost.php?p=7059555&postcount=24)

---

### Post by spleblem on 2009-06-03
ok as i said above im new to linux
how do i do this
i could not find a disable_ipv6 in ipv6 or how do i add something to the grub kernal command line
thanks

---

### Post by dmizer on 2009-06-03
Open a [terminal](https://help.ubuntu.com/community/UsingTheTerminal) and copy/paste the following command:
```
sudo sh -c "echo TRUE > /proc/sys/net/ipv6/disable_ipv6"
```

---

### Post by spleblem on 2009-06-03
thanks
did that and get this message
```
sh: cannot create /proc/sys/net/ipv6/disable_ipv6: Directory nonexistent

```

---

### Post by dmizer on 2009-06-04
Okay, this is a bit more complex.

Take a look here: [http://helpdeskgeek.com/virtualization/error-when-booting-ubuntu-in-virtual-pc-the-first-time/](http://helpdeskgeek.com/virtualization/error-when-booting-ubuntu-in-virtual-pc-the-first-time/)
(start at "When booting Ubuntu ...")

Rather than entering "noreplace-paravirt" as suggested in the above link, add "ipv6.disable=1" instead.

---

### Post by spleblem on 2009-06-04
i have done that its has not fixed the problem
still slow and no faster than 40kbs

---

### Post by dmizer on 2009-06-04
Okay, please post the output of:
```
lshw -C network
```

---

### Post by spleblem on 2009-06-04
here it is
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:35:14:52
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 module=atl1e multicast=yes
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:11:50:63:1b:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.2.104 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:38:7d:0d:54:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by dmizer on 2009-06-04
Try this: [s][http://blog.slettevoll.no/node/7](http://blog.slettevoll.no/node/7)[/s]

Scratch that, here's one that's Jaunty specific: [http://ubuntuforums.org/showthread.php?t=1148109](http://ubuntuforums.org/showthread.php?t=1148109)

---

### Post by spleblem on 2009-06-04
thanks alot for your help and patients
its working great now
thanks

---

