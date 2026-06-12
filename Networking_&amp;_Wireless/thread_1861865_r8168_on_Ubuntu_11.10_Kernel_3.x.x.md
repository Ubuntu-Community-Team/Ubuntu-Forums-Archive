---
title: "r8168 on Ubuntu 11.10 Kernel 3.x.x"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by matera.ttp on 2011-10-16
I don't know why but origin autorun.sh from drivers archive doesn't work anymore with next error: "FATAL: Module r8168 not found"

Here are instructions that works for me:

1. Download script here
[http://www.jamesonwilliams.com/bin/r8168_scripts.tar.bz2](http://www.jamesonwilliams.com/bin/r8168_scripts.tar.bz2)
( [http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168) )

2. Download r8168-8.025.00.tar.bz2 here 
[http://code.google.com/p/r8168/downloads/list](http://code.google.com/p/r8168/downloads/list)

3. Extract r8168_scripts.tar.bz2 and go to the extracted dir
cd r8168_scripts

4. Copy new r8168-8.025.00.tar.bz2 drivers to this directory

5. Edit "switchmods" end set VERSION to
VERSION=r8168-8.025.00

6. run switchmods
sudo ./switchmods

---

### Post by darkenergizerbunny on 2011-10-21
Thanks! This works perfectly.

---

### Post by haynest on 2011-10-22
I tried this and got a message that ended with "could not build module." This 8168 driver has been a pain for me...

---

### Post by vikketorr on 2011-10-22
I can get the network to work by following your steps but only untill next reboot.

---

### Post by Barn35 on 2011-10-22
Worked great for me, but doesn't hold persistent after a reboot. Have to re-run ./switchmods.

---

### Post by vikketorr on 2011-10-22
Solved the problem with the driver not working after reboot

Easiest way:

Follow the steps from matera.ttp and but replace the switchmod file with this one before running it:

[https://gist.github.com/gists/1306500](https://gist.github.com/gists/1306500)

Alternate way:

Change the "TMP=$(mktemp -d)" line in the switchmods file to:

```
TMP="compiled_driver"
```

and delete the line 
```
rm -r $TMP 
```

run the switchmode script

copy the file compiled_drivers/r8168-8.025.00/src/r8168.ko 
into /lib/modules/`uname -r`/kernel/drivers/net/r8168.ko

```
cd complied_drivers
cp r8168-8.025.00/src/r8168.ko /lib/modules/`uname -r`/kernel/drivers/net/r8168.ko

```


Move the one created by the original driver script (the problem was that this one was used when the linux image was created instead of the working one)

```
mv /lib/module/`uname -r`/kernel/drivers/net/r8168.o /lib/module/`uname -r`/kernel/drivers/net/r8168.o.bak
```

Update the linux image
```

update-initramfs -u
```

---

### Post by Tjkent on 2011-10-26
also you may need to go into the script for switchmods and change version to the one that you have placed in there. I did that and it worked perfectly.

---

### Post by matera.ttp on 2011-11-26
Thanks a lot for updated script **vikketorr**

---

### Post by SnatchAttack on 2011-12-01
Does anyone have, or know where i can find a copy of the script and patch file from jamesonwilliams.com because the site has been down for at least a couple days? Thanks

---

### Post by Master_T on 2011-12-01
I second that, does anyone have the scripts?

---

### Post by praseodym on 2011-12-01
Try it with:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget [http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2)
tar xvf r8168-8.026.00.tar.bz2
cd r8168-8.026.00/
sudo modprobe -rfv r8169
sudo make
sudo cp src/r8168.ko /lib/modules/$(uname -r)/kernel/drivers/net/
sudo depmod -a
sudo modprobe -v r8168
```

---

### Post by Master_T on 2011-12-01
I already tried that, but it didn't work for me. The thing that drives me mad is that although I can compile and activate the driver correctly, it still doesn't work! And before it worked, it broke with an update... I guess the only solution is to reinstall from scratch and avoid updating the kernel... not nice after spending hours ironing out problems and fixing scripts to make it work properly :(

---

### Post by vikketorr on 2011-12-01
Here's the complete package for 3.x.x so simply unpack and
```
sudo ./switchmods
```

A lot of excess files could probably be removed but I don't want to risk removing anything necessary ;)

Mirror: [http://ge.tt/90DpydA](http://ge.tt/90DpydA)

---

### Post by Master_T on 2011-12-01
> **vikketorr said:**
> Here's the complete package for 3.x.x so simply unpack and
```
sudo ./switchmods
```

A lot of excess files could probably be removed but I don't want to risk removing anything necessary ;)

Mirror: [http://ge.tt/90DpydA](http://ge.tt/90DpydA)

Thanks, tho in the end since I had nothing to do I just reinstalled the whole system and disabled updates so it wouldn't screw up again. Thx anyway for the help.

---

### Post by matera.ttp on 2012-04-15
in 12.04 module path was updated
replace
MODULEPATH=/lib/modules/`uname -r`/kernel/drivers/net/
with
MODULEPATH=/lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek

---

### Post by thebignose on 2012-09-04
Hello all.
I've been attempting to replace the r8169 driver with r8168 as described and have come up against a similar problem to that described in [this thread]("http://ubuntuforums.org/showthread.php?t=1581160"). 
The card was actually working fine before I started, except that it wouldn't WoL so I thought I would try the r8168 driver to see if it helped at all. The interface was previously part of a bonded interface along with another ethernet controller, which uses a different driver so is still working fine. 
ifconfig shows the other interface and the bonded interface as both up fine, but the Realtek device doesn't appear. It was previously eth0.
lspci shows the following for the ethernet devices:

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
    Subsystem: Netgear GA311
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 5
    I/O ports at b800 [size=256]
    Memory at ff6ff400 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at 40000000 [disabled] [size=128K]
    Capabilities: [dc] Power Management version 2

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
    Subsystem: ASRock Incorporation K7VT6 motherboard
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at e800 [size=256]
    Memory at ff6ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine


dmesg | grep eth returns the following:

[    0.787467] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xff6ffc00, <MAC address removed>, IRQ 23
[    0.788230] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1
[   12.262899] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.074123] bonding: bond0: Adding slave eth1.
[   14.078952] bonding: bond0: enslaving eth1 as an active interface with an up link.
[   14.389323] bonding: bond0: link status definitely up for interface eth1, 100 Mbps full duplex.
[   15.445007] bonding: bond0: Interface eth0 does not exist!

and lshw -c network returns:

  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:b800(size=256) memory:ff6ff400-ff6ff4ff memory:40000000-4001ffff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: <MAC address removed, same as for eth0 above>
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII slave=yes speed=100Mbit/s
       resources: irq:23 ioport:e800(size=256) memory:ff6ffc00-ff6ffcff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: bond0
       serial: <MAC address removed, same address as network 1 above>
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bonding driverversion=3.7.1 firmware=2 ip=192.168.0.10 link=yes master=yes multicast=yes

What's the network "UNCLAIMED" bit about? I'm kind of hoping if I can get something to "claim" it I'll be on my way.

If I run lsmod it shows r8168, which I think means the new module is loading, and doesn't show r8169, surely meaning the blacklist must be preventing the r8169 driver from loading. I can't think of any other findings to report but I'd welcome any suggestions. Apologies if I've omitted anything I should obviously have included.

Edited to add: I'm using Ubuntu Server Quantal 64 bit.

---

### Post by kamazee on 2013-03-04
... And it's broken again in 3.8 kernel.
So if you're willing to upgrade to raring (13.04) consider waiting until [this defect]("https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1108068") is resolved.
Hope, another version of [r8168 linux driver]("http://code.google.com/p/r8168/") will be rolled out soon and the driver will become buildable on 3.8.

---

