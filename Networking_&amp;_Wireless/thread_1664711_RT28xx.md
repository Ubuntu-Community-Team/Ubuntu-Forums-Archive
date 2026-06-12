---
title: "RT28xx"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by zipeppe on 2011-01-11
After the last system update (few days ago) the wireless box disconnects and reconnects continuously (every 60-90 secs).

This is the pertinent /var/log/messages when it disconnects:

```
[COLOR="Navy"]Jan 11 16:16:24 ibm kernel: [ 8073.320442] -->RTUSBVenderReset
Jan 11 16:16:24 ibm kernel: [ 8073.321453] <--RTUSBVenderReset
Jan 11 16:16:26 ibm kernel: [ 8075.624596] Key1Str is Invalid key length(0) or Type(0)
Jan 11 16:16:26 ibm kernel: [ 8075.624632] Key2Str is Invalid key length(0) or Type(0)
Jan 11 16:16:26 ibm kernel: [ 8075.624668] Key3Str is Invalid key length(0) or Type(0)
Jan 11 16:16:26 ibm kernel: [ 8075.624705] Key4Str is Invalid key length(0) or Type(0)
Jan 11 16:16:26 ibm kernel: [ 8075.625355] 1. Phy Mode = 0
Jan 11 16:16:26 ibm kernel: [ 8075.625358] 2. Phy Mode = 0
Jan 11 16:16:26 ibm kernel: [ 8075.741083] 3. Phy Mode = 0
Jan 11 16:16:26 ibm kernel: [ 8075.780107] MCS Set = 00 00 00 00 00
Jan 11 16:16:26 ibm kernel: [ 8075.795195] <==== rt28xx_init, Status=0
Jan 11 16:16:26 ibm kernel: [ 8075.807107] 0x1300 = 000a4200
Jan 11 16:16:28 ibm kernel: [ 8077.937015] pci 0000:02:1d.0: wake-up capability enabled by ACPI
Jan 11 16:16:28 ibm kernel: [ 8077.960539] pci 0000:02:1d.0: wake-up capability disabled by ACPI
Jan 11 16:16:28 ibm kernel: [ 8077.977291] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
Jan 11 16:16:29 ibm kernel: [ 8078.097571] ADDRCONF(NETDEV_UP): eth1: link is not ready[/COLOR]
```

And this when manually reconnected:

```
[COLOR="Navy"]Jan 11 16:16:37 ibm kernel: [ 8086.167522] -->RTUSBVenderReset
Jan 11 16:16:37 ibm kernel: [ 8086.168530] <--RTUSBVenderReset
Jan 11 16:16:39 ibm kernel: [ 8088.464724] Key1Str is Invalid key length(0) or Type(0)
Jan 11 16:16:39 ibm kernel: [ 8088.464760] Key2Str is Invalid key length(0) or Type(0)
Jan 11 16:16:39 ibm kernel: [ 8088.464796] Key3Str is Invalid key length(0) or Type(0)
Jan 11 16:16:39 ibm kernel: [ 8088.464833] Key4Str is Invalid key length(0) or Type(0)
Jan 11 16:16:39 ibm kernel: [ 8088.465510] 1. Phy Mode = 0
Jan 11 16:16:39 ibm kernel: [ 8088.465513] 2. Phy Mode = 0
Jan 11 16:16:39 ibm kernel: [ 8088.581175] 3. Phy Mode = 0
Jan 11 16:16:39 ibm kernel: [ 8088.621207] MCS Set = 00 00 00 00 00
Jan 11 16:16:39 ibm kernel: [ 8088.636185] <==== rt28xx_init, Status=0
Jan 11 16:16:39 ibm kernel: [ 8088.648150] 0x1300 = 000a4200
Jan 11 16:16:39 ibm kernel: [ 8088.751141] ERROR!!! RTMPSetTimer failed, Halt in Progress![/COLOR]

```

What is going on?

---

### Post by PatchesTheCaveman on 2011-01-11
There is a faulty kernel update that is causing problems with some Realtek adapters.  To see if you have this update and fix it, follow the instructions I provided in this post:  
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

---

### Post by chili555 on 2011-01-11
> **PatchesTheCaveman said:**
> There is a faulty kernel update that is causing problems with some Realtek adapters.  To see if you have this update and fix it, follow the instructions I provided in this post:  
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)Could we get a link to the bug report please? Thanks.

---

### Post by PatchesTheCaveman on 2011-01-12
chili555:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509)

I added that link to that post too since I link to it quite often.

---

### Post by zipeppe on 2011-01-12
> **PatchesTheCaveman said:**
> There is a faulty kernel update that is causing problems with some Realtek adapters.  To see if you have this update and fix it, follow the instructions I provided in this post:  
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

I got the following 'uname -r' output:

2.6.35-**22**-generic

It applies anyway?

---

### Post by PatchesTheCaveman on 2011-01-12
No.  You have a different problem.

You might try the official driver for your wireless device from Realtek.  Many users have a better experience using that.  Unfortunately, we need the last two digits of the Realtek chipset number to figure out what that is!

You can discover that by running:
```
lshw -C network
```

---

### Post by zipeppe on 2011-01-12
> **PatchesTheCaveman said:**
> No.  You have a different problem.

You might try the official driver for your wireless device from Realtek.  Many users have a better experience using that.  Unfortunately, we need the last two digits of the Realtek chipset number to figure out what that is!

You can discover that by running:
```
lshw -C network
```

Hmmm... that's not clear for me.
with the command above I have the following:

```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5703X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       logical name: eth1
       version: 02
       serial: 00:10:dc:f5:39:71
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=5703-v2.21c ip=192.168.1.9 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:48 memory:fb100000-fb10ffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:30:84:3f:21:46
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.1.12 latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:21 ioport:a000(size=256) memory:fb305000-fb3050ff
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:a0:a2:43:9b:bf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 multicast=yes wireless=Ralink STA
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

What about the *last two digits* now?

---

### Post by PatchesTheCaveman on 2011-01-12
Just to be clear, this is the device you're experiencing trouble with?
```
 *-network:0
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:a0:a2:43:9b:bf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 multicast=yes wireless=Ralink STA
```

---

### Post by PatchesTheCaveman on 2011-01-12
Is this a USB dongle wireless adapter, one built into a laptop, or a PCI card on your desktop?

If it's USB there's a driver update but if it's the latter two you have the newest driver.

---

### Post by zipeppe on 2011-01-12
> **PatchesTheCaveman said:**
> Is this a USB dongle wireless adapter, one built into a laptop, or a PCI card on your desktop?

If it's USB there's a driver update but if it's the latter two you have the newest driver.

Mine it's a USB dongle wireless adapter, as shown by the **lsusb** command:

Bus 002 Device 004: ID 083a:7522 Accton Technology Corp. Arcadyan 802.11N Wireless Adapter

What do you suggest for the upgrade you've mentioned before?

---

### Post by PatchesTheCaveman on 2011-01-12
The *RT2870USB(RT2870/RT2770)* driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by chili555 on 2011-01-12
> You might try the official driver for your wireless device from Realtek. This is, however, a Ralink. The driver module rt2870sta claims your device:```
~$ modinfo rt2870sta | grep 7522
alias:          usb:v[COLOR="Red"]083A[/COLOR]p[COLOR="Red"]7522[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```So does rt2800usb. I suspect my colleague Patches will inquire as to a blacklist.

---

### Post by PatchesTheCaveman on 2011-01-12
@chili555:  I totally forgot about that.  ](*,)  Thanks.

@zipeppe:  Please copy/paste the output of:
```
lsmod
cat /etc/modprobe.d/*
```

---

