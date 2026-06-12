---
title: "Weird problem with ethernet"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by c0dege3k on 2011-08-02
I recently noticed that my laptop's ethernet wouldn't work, so in checking the ifconfig I found that I no longer have an eth0 (I used to)- instead I have an eth41. I try doing ifconfig eth0 up, and it tells me that there is "no such device".

I don't know much about networking, so I don't know what info to give, but any and all help is appreciated.

---

### Post by Iowan on 2011-08-02
You can check **sudo lshw -C network** to see what is there for a definition. You might also check contents of */etc/udev/rules.d/70-persistent-net.rules*

---

### Post by c0dege3k on 2011-08-02
Okay, the output for the first command is:
```


  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 02
       serial: c4:42:67:39:16:00
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:e800(size=256) memory:f6fff000-f6ffffff memory:f6fe0000-f6feffff memory:f6f00000-f6f0ffff

```

But where I think the trouble is is in that file. It's current contents are: 
```


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:8c:0f:7e:13", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4232 (iwlagn)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:21:5d:5a:9d:84", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="c4:42:67:39:16:00", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

However, there used to be up to eth41, until i deleted all but eth0 and wlan0 and rebooted. Now eth1 is back and ifconfig is reporting an eth1 in existence, but still no eth0.

---

### Post by Iowan on 2011-08-02
I'm curious what has the (hardware) address 00:24:8c:0f:7e:13...

---

### Post by c0dege3k on 2011-08-02
Um, just to be clear- was that you just wondering, or are you expecting me to do something? Like I said- I don't know much about this stuff.

---

### Post by nm_geo on 2011-08-02
Try 

```
lspci -nn | grep -e 0280 -e 0200
```That should give the wireless & wired information.

Do you have 2 ethernet cards?? Oops..probably not huh?  
> **laptop's ethernet wouldn't work**

Note to self read the whole message.

---

### Post by c0dege3k on 2011-08-02
The output is:
```

03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)

```

and no- as displayed above, I only have a WiFi card & one ethernet card

---

### Post by nm_geo on 2011-08-02
Yeah i saw that 

```
ifconfig
```

Let's see that too..

---

### Post by c0dege3k on 2011-08-02
```


eth1      Link encap:Ethernet  HWaddr c4:42:67:39:16:00  
          inet6 addr: fe80::c642:67ff:fe39:1600/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3960 (3.9 KB)  TX bytes:3772 (3.7 KB)
          Interrupt:45 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21871 (21.8 KB)  TX bytes:21871 (21.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:5a:9d:84  
          inet addr:192.168.43.242  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fe5a:9d84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99510339 (99.5 MB)  TX bytes:100629328 (100.6 MB)

```

---

### Post by nm_geo on 2011-08-02
Okay 

```
sudo ifconfig eth0 down && sudo ifconfig eth0 up
```Then full output of

```
sudo lshw -C network
```I would then recommend trying to reboot with ethernet cable installed..
See what happens..

---

### Post by c0dege3k on 2011-08-02
The first command outputs:
```

eth0: ERROR while getting interface flags: No such device

```

and the second one:
```

  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:5a:9d:84
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-10-generic firmware=8.83.5.1 build 33692 ip=192.168.43.242 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:fcffe000-fcffffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 02
       serial: c4:42:67:39:16:00
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:e800(size=256) memory:f6fff000-f6ffffff memory:f6fe0000-f6feffff memory:f6f00000-f6f0ffff

```

will report soon with the results of the reboot

---

### Post by c0dege3k on 2011-08-03
Some weird stuff happened when booting- shown in pics attached

---

### Post by mitchman333 on 2011-09-15
> **c0dege3k said:**
>  will report soon with the results of the reboot

any updates on this issue..?  i have the exact same problem and your steps so far seem identical - my Ethernet controller just stopped working on my last update (4 days ago).

Nothing has helped so far.

-  Mitchman

UPDATE:  Don't quite know how or why, but followed these instructions and Ethernet Connection is back up, [http://ubuntuforums.org/showpost.php?p=8275776&postcount=6](http://ubuntuforums.org/showpost.php?p=8275776&postcount=6) (it was a long 4 days)

---

