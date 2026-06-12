---
title: "Second wired adapter not showing in network manager"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by Dude-PWB- on 2012-06-06
I have two wired adapters in my computer.

The onboard 1000mbit adapter for my local network and a dlink dfe530tx 100mbit adapter for my internet.

Both of my adapters show in the terminal with lspci:

```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:07.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)

```lshw -C network shows my 100mbit adapter as unclaimed

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:11:5d:4a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.106 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:41 ioport:ce00(size=256) memory:fd8ff000-fd8fffff memory:fd8f8000-fd8fbfff
  *-network UNCLAIMED
       description: Ethernet controller
       product: VT86C100A [Rhine]
       vendor: VIA Technologies, Inc.
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64 maxlatency=152 mingnt=102
       resources: ioport:bf00(size=128) memory:fdd00000-fdd0007f memory:fdc00000-fdc0ffff

```My interfaces file seems to be correct by all of my reading.

I will preface this by saying that I just built this machine, and while it was on my workbench and I was installing 12.04 and setting things up, I only had the 1000mbit adapter hooked up, and turned the slider to off for the 100mbit to stop the pop up saying it was disconnected so the card WAS working at one time. Now, I can not seem to turn it back on anywhere.

I'm sure it is a simple solution, but for some reason my bleeding eyes can't seem to find the answer. 

Paging chili555!!  :lol:

---

### Post by papibe on 2012-06-06
Hi Dude-PWB-.

It looks no driver is assigned to the card.

Could you post the result of this command?
```
lsmod | grep -i via
```
If the result is empty, it means that is not loaded. I believe the correct driver is called 'via-rhine'. Try loading it manually:
```
sudo modprobe via-rhine
```
Now check Network Manager. If it still doesn't appear on NM, restart it:
```
sudo service network-manager restart
```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by Dude-PWB- on 2012-06-06
Thanks for the suggestion papibe.

lsmod | grep -i via seems to show the driver listed.

```
lsmod | grep -i via
via_rhine              32192  0
```

Tried modprobe via-rhine anyway for giggles and restarted network, no change except for a warning when doing modprobe.

```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
```

---

### Post by Dude-PWB- on 2012-06-07
Any more suggestions?

---

### Post by Dude-PWB- on 2012-06-09
Seems I have solved this.

Turns out it seems the ethernet adapter was at fault. 

I updated the mainboard bios and the adapter finally showed up but would not connect no matter what i did.

Installed W7 on another hard drive to troubleshoot this some more, and it turns out it couldn't allocate resources for the adapter. Popped out the dfe530 that was in there and replaced it with another dfe530 I had laying around and it is singing along like nobody's business.

Thanks for the suggestions at any rate.

---

