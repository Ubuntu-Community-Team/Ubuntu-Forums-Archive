---
title: "Deleted NIC"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by peanut99 on 2010-09-08
):P Hi to all,

I've made a silly mistake, but I can't seem to recover.  I deleted one of my wired NICs from my network connections.  ](*,)   I've verified that the NIC is still physically onboard, I performed the lspci and still the NIC showing up with its mac.  However, when I looked in my /etc/networking/interfaces file, I don't see any of my NICs except the looback.  Also, I've been perusing these forums and found the 70-persistent-net.rules file in /etc/udev/rules.d.  That file contained all of my NICs.  My question is, how do I get that NIC back in the network connections?  I've tried to manually add it back using the mac address in the form of: 00:11:22:33:44:55 in the network connections but to no avail... Any assistance would be greatly appreciated.  Thanks!

-Peanut

---

### Post by endotherm on 2010-09-08
easy enough to fix. just click Add to create a new one, and run 
```
sudo ifconfig
``` to find your mac address. just make sure you select the MAC and nothing else (if you copy/paste watch out for spaces on either side).

 nowadays if you are using network-manager, your interfaces are usually not defined in /etc/network/interfaces anymore, but they can be, if you want to jsut manually configure it and stop using network-manager. works well for wired, but not as well for wireless. 
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by peanut99 on 2010-09-08
endotherm,

Thanks for the speedy reply. I'd previously tried to re-add the NIC via the network connections applet with the correct MAC taken from the 70-persistent-net.rules file, all to no avail.  I then added the NICs to the /etc/networking/interfaces file, restarted my network service, but eth2 (the deleted nic) failed to bring up eth2.  I'm assuming because I didn't associate the MAC address to the eth2 in the /etc/networking/interfaces file.  Which file should I manipulate to add the mac address?  Thanks!

-Peanut

---

### Post by endotherm on 2010-09-08
> **peanut99 said:**
> endotherm,

Thanks for the speedy reply. I'd previously tried to re-add the NIC via the network connections applet with the correct MAC taken from the 70-persistent-net.rules file, all to no avail.  I then added the NICs to the /etc/networking/interfaces file, restarted my network service, but eth2 (the deleted nic) failed to bring up eth2.  I'm assuming because I didn't associate the MAC address to the eth2 in the /etc/networking/interfaces file.  Which file should I manipulate to add the mac address?  Thanks!

-Peanut


well you don't have to manually tie the name 'eth0/1/2' to a mac in the interfaces file. be sure to run 'ifconfig' to confirm that you have the right mac. the system will occasionally decide to swap what physical interface is tied to a name (eth0 becomes eth1 and vice versa). 

also the rules file may be out of date, but ifconfig never is. 
give it another try. otherwise, I would just determine teh interface name the nic currently has and config my interfaces file.

---

### Post by BkkBonanza on 2010-09-08
Make sure the interface show up with **sudo ifconfig -a**. The -a will show interfaces that are inactive as well. If it shows there you can try to bring it up manually. If it's not there then you have a driver issue.

---

### Post by peanut99 on 2010-09-08
Thanks for the input.  The device doesn't show with the ifconfig.  My apologies for not stating that... That's when I first noticed.  The driver I don't think had an issue because the NIC was working just fine.  I manually went into the Network Connections and deleted the NIC.  I thought that upon a reboot, it would detect the device and reinstall it.  It was me goofing around that caused it to uninstall.  I know I can get it back with a reinstall, but I'm trying to prevent a reinstall.  Thanks.

-Peanut

---

### Post by endotherm on 2010-09-08
what do you get from 
```
sudo lshw -C network
```

---

### Post by Iowan on 2010-09-08
> **peanut99 said:**
> However, when I looked in my /etc/networking/interfaces file, I don't see any of my NICs except the looback. That's normal for a Network Manager controlled machine.

> **peanut99 said:**
> ... The device doesn't show with the ifconfig. Does the interface show up with **sudo ifconfig -a**?  As **BkkBonaza** pointed out - that will show all configured interfaces - active or not.

---

### Post by peanut99 on 2010-09-08
> **endotherm said:**
> what do you get from 
```
sudo lshw -C network
```
 
I will try this when I get home and post the results.  Thanks.
 
-Peanut

---

### Post by peanut99 on 2010-09-08
> **Iowan said:**
> That's normal for a Network Manager controlled machine.
 
Does the interface show up with **sudo ifconfig -a**? As **BkkBonaza** pointed out - that will show all configured interfaces - active or not.
 
No, the NIC doesn't show up in my ifconfig -a.  I think I'm going to try to reinstall the driver.  I didn't think that would be an issue because the NIC worked flawlessly before I deleted it.  Thanks to all for your inputs thus far.
 
-Peanut

---

### Post by peanut99 on 2010-09-09
> **endotherm said:**
> what do you get from 
```
sudo lshw -C network
```
endotherm,

Here's the output from the "sudo lshw -C network" command:
```

  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:26:18:4d:49:da
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe9fc000-fe9fffff ioport:c800(size=256) memory:fe9c0000-fe9dffff(prefetchable)
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: ADMtek
       vendor: ADMtek
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=128 mingnt=64
       resources: ioport:e800(size=256) memory:feb00000-feb003ff memory:f0800000-f081ffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth1
       version: 14
       serial: 00:26:18:4d:4d:54
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.24.55 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:febf8000-febfbfff ioport:e400(size=256) memory:f0820000-f083ffff(prefetchable)

```The two nics that are present are the ones that are on board.  The PCI NIC that I installed doesn't show up.  It does have a ethernet controller that is "UNCLAIMED".  Does this output raise any flags?

Also, here's the output from my 70-persistent-net.rules file:
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4364 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:18:4d:49:da", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x11ab:0x4320 (skge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:18:4d:4d:54", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x1317:0x0985 (tulip)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:17:4f:47:67", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

```And lastly, here is the output from my ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:26:18:4d:49:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:26:18:4d:4d:54  
          inet addr:192.168.24.55  Bcast:192.168.24.255  Mask:255.255.255.0
          inet6 addr: 2001:a05e:7217:0:226:18ff:fe4d:4d54/64 Scope:Global
          inet6 addr: fe80::226:18ff:fe4d:4d54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2531854 (2.5 MB)  TX bytes:640073 (640.0 KB)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:26:18:4d:49:da  
          inet addr:169.254.7.164  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85664 (85.6 KB)  TX bytes:85664 (85.6 KB)

vmnet3    Link encap:Ethernet  HWaddr 00:50:56:c0:00:03  
          inet addr:172.16.171.1  Bcast:172.16.171.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet4    Link encap:Ethernet  HWaddr 00:50:56:c0:00:04  
          inet addr:192.168.96.1  Bcast:192.168.96.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```Disregard eth0 because its plugged into my "lab network" that is powered off at the time of me writing this.  Any assistance is greatly appreciated.

-Peanut

---

### Post by peanut99 on 2010-09-10
Got it working... I powered the system off, removed the NIC, powered on, ensured that the NIC was no longer recognized by the "lspci".  I then powered off again, reinstalled the NIC and *poof* it reappeared.  Thanks to all that assisted.

-Peanut

---

