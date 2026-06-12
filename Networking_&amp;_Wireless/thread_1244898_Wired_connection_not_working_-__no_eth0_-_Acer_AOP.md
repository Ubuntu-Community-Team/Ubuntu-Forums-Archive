---
title: "Wired connection not working -  no eth0 - Acer AOP531h Netbook"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by metaljacket on 2009-08-19
Hi,

I installed Ubuntu Netbook Remix as soon as I bought my new Acer AOP531H-1CK 10" netbook. The wired connection (both static IP and PPPoe) does not work because the machine cannot find eth0. Below is my procedures and outputs.

First I manually edit this file:
```

**$ sudo vim /etc/network/interfaces**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.**.90
netmask 255.255.128.0
gateway 192.168.0.1
hwaddress ether 00:02:2e:f1:**:52
/etc/network/interfaces (END) 
```

Then I restarted the network without success.
```

**$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...            
SIOCSIFHWADDR: No such device
Failed to bring up eth0.
```

It seems that ifconfig cannot find eth0.
```

**@Hal:~$ ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:2b:1d:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-2B-1D-B4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

But there IS a ethernet controller.
```
**$ lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
[B]01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)[/B]

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:2b:1d:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 92:34:1b:dc:62:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I also tried the Preferences->Network Connections but the problem remains. I read a few relevant threads but still cannot make the ethernet work. I would really appreciate it if anyone can throw some sunshine on this. 

BTW. I have already tried Fedora Core and Mandriva, and the problem are similar. If Ubuntu cannot get this netbook onto the internet, then I have to seriously consider going back to Linpus.

---

### Post by madhavhmk on 2009-08-20
can you spot eth0 in:
sytem>admin>network tools

---

### Post by metaljacket on 2009-08-20
Hi madhavhmk,

Attached are the screenshots of the four network devices recognized by Network Tools.
 
I notice that the wlan0 and the "unknown interface" wmaster0 have the same MAC address. Is it possible that this wmaster0 is the real eth0?

> **madhavhmk said:**
> can you spot eth0 in:
sytem>admin>network tools

---

### Post by karthick87 on 2009-08-20
I have the same problem,but i can spot eth0 in System>Administration>Network Tools..

---

### Post by metaljacket on 2009-08-20
> **metaljacket said:**
> ....If Ubuntu cannot get this netbook onto the internet, then I have to seriously consider going back to Linpus.

Last night I DID go back to Linpus. I installed Linpus Lite (with a GUI, the linpus that comes with the netbook is just TUI). It took me a while to get used to that gigantic cursor. Well, network device eth0 was not found and the problem was basically the same as described above.

Still waiting and searching for a solution ...

---

### Post by metaljacket on 2009-08-20
Finally I found my way out following this thread,
[http://ubuntuforums.org/showthread.php?t=1141529&highlight=D250&page=2](http://ubuntuforums.org/showthread.php?t=1141529&highlight=D250&page=2) 

SOLUTION:

Download AR81Family-linux-v1.0.0.10.tar.gz from 
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)
Put it in a directory

```
$ gunzip AR81Family-linux-v1.0.0.10.tar.gz
$ tar xvf AR81Family-linux-v1.0.0.10.tar
$ cd src
$ make
$ sudo make install
$ cd /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e/
$ sudo insmod ./atl1e.ko 
```

Thus the driver is installed and the eth0 deviced can be detected and configured. Problem solved.

---

### Post by afp_sch on 2009-09-06
I do  this but i cant conet to internet.

Help!!!

---

### Post by mateusss on 2009-09-12
Thanks for posting this. My AspireOne can now work with wired lan.

---

