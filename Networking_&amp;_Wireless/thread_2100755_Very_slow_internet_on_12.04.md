---
title: "Very slow internet on 12.04"
date: 2013-01-02
forum: Networking &amp; Wireless
---

### Post by cL0h on 2013-01-02
Hi there,
I am experiencing extremely slow internet speeds after installing 12.04. Another PC is fine .
I tried this to disable IPV6:

[http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html](http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html)

and I set a static IP but to no avail.

Any ideas?

---

### Post by ahallubuntu on 2013-01-02
To get help, you'll need to give more information about your network and how you are connected to it.  Wired or wireless?

For starters, please give the output of this:

```
sudo lshw -C network
```

Get rid of the static IP for now.  That won't do anything to speed up your connection, but it might make things more confusing later as you try to update/debug your problem.

---

### Post by cL0h on 2013-01-03
Apologies for the delay in replying. Connection is wired and I've set it back to DHCP

```
sudo lshw -C network
```

gives:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 20:cf:30:dd:c4:0c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full  firmware=rtl_nic/rtl8168d-2.fw ip=192.168.1.25 latency=0 link=yes  multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8ff8000-f8ffbfff memory:febf0000-febfffff

```

---

### Post by cL0h on 2013-01-04
Something about ahallubuntu's question made me curious and I googled my NIC "RTL8111/8168B" and discovered the rather common issue of ubuntu loading the wrong driver for cards of this type.
I discovered the suggested solution here 

[http://forums.linuxmint.com/viewtopic.php?f=49&t=80757](http://forums.linuxmint.com/viewtopic.php?f=49&t=80757)

but after following the instructions I now have no internet access at all. After pondering this on the way to work I now suspect that I may have substituted the wrong kernel version for the copy command:

```
sudo cp src/r8168.ko   /lib/modules/3.0.0-1-amd64/kernel/drivers/net/
```

I copied the driver into a 3.2.0-35-PAE[COLOR="Red"](orsomething)[/COLOR]/kernel/drivers/net/ folder but the docs say the 12.04 kernel is 3.2.0-29.46

I'll check when I get home but I'd appreciate some feedback that I'm on the right track.
Thanks
C.

---

