---
title: "Disconnected from Network (wired) After Suspend/Resume"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by floborg on 2009-05-16
After some suspend/resume cycles, I lose my wired network connection.  This never happened with Hardy, from which I upgraded to Jaunty.

The network panel applet doesn't allow me to reconnect, as most of the options are greyed out.  I've also tried unchecking Enable Networking and rechecking it, but that does nothing.  I've tried various terminal commands to restart networking (ifup/ifdown, /etc/init.d/networking restart, etc), but none of those worked either.

I've read about a similar bug reported in Intrepid, but the fix put into Jaunty seemed focused on wireless connections.  I would like to know if anyone else is experiencing this with a wired connection.  I've seen no new bugs in Launchpad.  My system uses the e1000e driver.

---

### Post by floborg on 2009-05-19
I am not alone apparently:

[No network after suspend - need ifconfig help, maybe?]("http://ubuntuforums.org/showthread.php?t=1164115")

---

### Post by ENigma885 on 2012-01-31
Faced the same problem with Ubuntu 11.10 and that's how I solved it

**1-** Open a terminal window and
```
gksudo gedit /etc/pm/config.d/unload_modules
```
*(even if the file is not there it will be created)*

**2-** in this document add
SUSPEND_MODULES="Your_Network_Driver" [with the qoutes] *(to get ur network driver's name follow the next step)*

**3-** Open a terminal and
```
sudo lshw
```
- Under "network" section then under "configuration" the driver will be written as "driver=SOMETHING"
*(you can use the search menu in the terminal to search for network)*
- *_Example:-_*
```
*-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:23:8b:62:11:7c
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=r8169[/COLOR] driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.62 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s

```

[B]**##So, what will be written in the document opened in the first step is
SUSPEND_MODULES="r8169"[/B]

then save the file.

- After saving the file resuming after a suspend will reconnect your network automatically.

---

