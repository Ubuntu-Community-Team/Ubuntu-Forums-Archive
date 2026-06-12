---
title: "no internet after install"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by I-Imaging on 2013-08-11
I've been trying to figure this out for a couple of days by reading posts but I need to resort to you guys for help.

After I installed ubuntu 13.04 I have no internet (wired, or wireless). When I use a flash drive as a boot disk the exact same version of linux has both connections on my laptop. After it gets installed I have no connections.

I am a basic user of linux and don't know much so feel free to dumb down your answers.

The computer is an older one. It's a dell vostro 1700 and I think the wireless is a broadcom (bcm2046b1)

---

### Post by chili555 on 2013-08-12
Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep -e 0200 -e 0280
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by I-Imaging on 2013-08-13
Thanks chili, It says:
> 03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

---

### Post by chili555 on 2013-08-13
Hmmm. We see no wireless. Please try again. In the meantime, the driver for your ethernet is b44. If you load it manually, does the ethernet spring to life?```
sudo modprobe b44
```I suspect the wireless has b44 blacklisted. We'll know more after you find the wireless!

Also run and post:```
lsusb
```

---

### Post by I-Imaging on 2013-08-13
"sudo modprobe b44" didn't do anything, was it supposed to?

Here is the output:
> Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 WebcamBus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)




---

### Post by chili555 on 2013-08-13
We still see no wireless. Please try:```
sudo lshw -C network
```> "sudo modprobe b44" didn't do anything, was it supposed to?Is an ethernet interface created, ideally eth0?```
ifconfig
```Is the ethernet cable attached? Does it try to connect?

---

### Post by I-Imaging on 2013-08-13
Yeah the ethernet cable is connected but it doesn't do anything. It works when I use the flash drive as a startup though.

I have no idea if an ethernet interface is created. I'm not very knowledgeable about this kind of thing, sorry.

Here are what the two lines of code above generated:
>   *-network                      description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:23:8a:d8:d9
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:f9bfe000-f9bfffff

> 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)




---

### Post by chili555 on 2013-08-14
We wonder why the ethernet is showing as disabled. Please try:```
sudo modprobe b44
sudo modprobe ssb
sudo lshw -C network
```Is it still disabled? If not, does it work now? If it is still disabled, let's see what the message logs say about this:```
dmesg | grep -e eth1 -e b44
```

---

### Post by I-Imaging on 2013-08-14
the first two commands from above didn't do anything. 

The output from the bottom one is:
```

[2.839797] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[2.860736] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1c:23:8a:d8:d9

```

---

