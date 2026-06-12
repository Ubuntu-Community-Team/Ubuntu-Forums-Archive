---
title: "Help With USB Ethernet - 10.04"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by Go3Team on 2010-08-15
I have a USB Ethernet adapter that I had on a modded WDTV box, that worked perfectly with whatever flavor of linux it was using.  I tried adding the adapter to a new install of 10.04 Server Edition, and am failing miserably at trying to get it to work.

The computer seems to recognize it:
```

burke@router:/etc/grub.d$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0bb4:0ff9 High Tech Computer Corp.
Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 005: ID 0b95:1780 ASIX Electronics Corp. AX88178
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lshw:
```
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:11:6b:f0:32:e7
       size: 1GB/s
       capacity: 1GB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88178 USB 2.0 Ethernet link=yes multicast=yes port=MII speed=1GB/s

```

ifconfig:
```

eth1      Link encap:Ethernet  HWaddr 00:11:6b:f0:32:e7
          inet6 addr: fe80::211:6bff:fef0:32e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:17100 (17.1 KB)

```

For all appearances, it seems to be recognized and working.  If I set it up for DHCP, it fails @ retrieving an IP from the router.  If I set a static ip, it also does not work, and I cannot ping it from another computer.  

How do I know its using the right driver?  I came across this trying to figure it out:
[http://manpages.ubuntu.com/manpages/lucid/man4/axe.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/axe.4freebsd.html)
Beyond the info listed there, I couldn't find any info on how to make the changes it listed.

The device in question is a Level One USB Ethernet Adapter - model USB-0201.  The power light is lit, as well as the 1000M light as well.


Any help would be appreciated!

---

### Post by Kerubu on 2010-08-15
If you right click on the network icon, top-right of the desktop, and select 'edit connections' can you find the device listed in one of the tabs?

If so, highlight it and select edit.

Look under IPv4, is DHCP set to automatic ?

---

### Post by Go3Team on 2010-08-15
I'm using the server version, no GUI on this one.  

/etc/network/interfaces:
```

auto eth1
iface eth1 inet dhcp

```

---

### Post by Go3Team on 2010-08-15
Solved.

Found a solution on a Debian bug list.

Downloaded new driver from Asix. 

modprobe -r asix
untar the archive
make
sudo make install
modprobe asix

plug in the device. 

Works now.

Hopefully someone who needs the info stumbles across this.

---

### Post by lincoln32 on 2011-01-09
thanks I am loading it now and it helps us all a lot when some leave the instructions to make it work:KS

---

