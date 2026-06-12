---
title: "Wifi Gone when installed 10.10"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by SteveS1949 on 2010-09-03
Hi,
I have an Acer Aspire One D250 with an Intel Ultimate-N 6300 Wifi card installed. It worked in 10.04, but as soon as I have installed 10.10 it has disappeared (i.e. it is undetected).

It does appear when I use the 'lspci' command.

How could I 'activate' the card?

---

### Post by SteveS1949 on 2010-09-03
I have a Intel 6300 Wifi card. It was working fine in 10.04 as wlan2. Now, I have installed 10.10 and it no longer appears as wlan2 or anything in 'ifconfig'

It appears in 'lspci'

How can I get wifi back?

Acer Aspire One D250

---

### Post by supermario641996 on 2010-09-03
I have an acer aspire one d260 and mine works just fine.  By the way, its recommended to not upgrade to ubuntu 10.10 on a machine do to driver problems.  I did it because if it didn't work or died I could easily install ubuntu 10.04 back on the computer.

---

### Post by uRock on 2010-09-03
Please post in the proper section to avoid others from being confused into thinking 10.10 is out of testing.

Thanks,
uRock

---

### Post by Tracy177 on 2010-09-03
> **supermario641996 said:**
> I have an acer aspire one d260 and mine works just fine.  By the way, its recommended to not upgrade to ubuntu 10.10 on a machine do to driver problems.  I did it because if it didn't work or died I could easily install ubuntu 10.04 back on the computer.


one day 10.10 will work other not :)

it is beta so bugs 

but u could check up lsusb and lspci and dmesg maybe your issue is just no firmware if so still chance to get it work

---

### Post by overdrank on 2010-09-03
Hi and welcome, please do not create multiple threads on the same issue.
Threads merged and moved to Maverick Meerkat Testing and Discussion

---

### Post by cariboo on 2010-09-03
Seeing as lshw is broken at the moment, could you install hwinfo and run it, and post the results for your wireless device. This is just to see if the proper driver was loaded.

---

### Post by SteveS1949 on 2010-09-03
92: udi = '/org/freedesktop/Hal/devices/pci_8086_422b'
  info.vendor = 'Intel Corporation'
  pci.product = 'Centrino Ultimate-N 6300'
  pci.subsys_vendor = 'Intel Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  pci.subsys_product = 'Centrino Ultimate-N 6300 3x3 AGN'
  info.subsystem = 'pci'
  info.product = 'Centrino Ultimate-N 6300'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_422b'
  pci.product_id = 16939 (0x422b)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 4353 (0x1101)
  pci.subsys_vendor_id = 32902 (0x8086)
  pci.device_class = 2 (0x2)
  pci.device_subclass = 128 (0x80)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'


That is the relevant part of the output.
Just a note: The original wireless card works with 10.10 with the hardware switch. It worked in 10.04 but no hardware switch support.
The new one (6300) worked in 10.04 with the hardware switch and now nothing at all.

Regards

---

### Post by cariboo on 2010-09-03
The information we're looking for, should look something like this:

```
60: None 01.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: L2Ua.ndpeucax6V1
  Parent ID: JNkJ.+S2X8jXF4X1
  SysFS ID: /class/net/eth1
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  [B]Driver: "wl"
  Driver Modules: "wl"[/B]
  Device File: eth1
  HW Address: 90:4c:e5:41:e4:2f
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (Ethernet controller)
```

the above output is what I get when running hwinfo, it shows up at the very end of the list. As you can see it very clearly show what driver my device uses.

If you look at the final pci address it is 01:00:0 which matches with the lspci output:

```
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

 We need to see the same type of output from you.

---

### Post by SteveS1949 on 2010-09-03
I think that is really the reason. I believe it may be an issue where the device is set to disabled. My reason for thinking this is that as you say there is no driver info and also the dev team has set something that allows the hardware switch to work, this may be interfering with the device?

I have given you a full printout of the returned info, nothing is missed. The next device is:

92: udi = '/org/freedesktop/Hal/devices/pci_8086_422b'
  info.vendor = 'Intel Corporation'
  pci.product = 'Centrino Ultimate-N 6300'
  pci.subsys_vendor = 'Intel Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  pci.subsys_product = 'Centrino Ultimate-N 6300 3x3 AGN'
  info.subsystem = 'pci'
  info.product = 'Centrino Ultimate-N 6300'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_422b'
  pci.product_id = 16939 (0x422b)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 4353 (0x1101)
  pci.subsys_vendor_id = 32902 (0x8086)
  pci.device_class = 2 (0x2)
  pci.device_subclass = 128 (0x80)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  93: udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family PCI Express Port 1'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family PCI Express Port 1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'
  info.linux.driver = 'pcieport'
  pci.product_id = 10192 (0x27d0)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 559 (0x22f)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

---

### Post by SteveS1949 on 2010-09-03
29: PCI 100.0: 0280 Network controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_422b
  Unique ID: VCu0.oULv2Z9H2b2
  Parent ID: z8Q3.xoLVOCcRtX4
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: network
  Model: "Intel Network controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x422b 
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1101 
  Revision: 0x09
  Memory Range: 0x95100000-0x95101fff (rw,non-prefetchable)
  IRQ: 16 (18885 events)
  Module Alias: "pci:v00008086d0000422Bsv00008086sd00001101bc02sc80i00"
  Driver Info #0:
    Driver Status: iwlagn is active
    Driver Activation Cmd: "modprobe iwlagn"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (PCI bridge)

30: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1969_1062
  Unique ID: rBUF.OEOQjQTk3EB
  Parent ID: hoOk.+S7VJU4G_36
  SysFS ID: /devices/pci0000:00/0000:00:1c.2/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Attansic Ethernet controller"
  Vendor: pci 0x1969 "Attansic Technology Corp."
  Device: pci 0x1062 
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x022f 
  Revision: 0xc0
  Driver: "atl1c"
  Driver Modules: "atl1c"
  Device File: eth0
  Memory Range: 0x93000000-0x9303ffff (rw,non-prefetchable)
  I/O Ports: 0x1000-0x2fff (rw)
  IRQ: 44 (no events)
  HW Address: 00:23:5a:82:53:5c
  Link detected: no
  Module Alias: "pci:v00001969d00001062sv00001025sd0000022Fbc02sc00i00"
  Driver Info #0:
    Driver Status: atl1c is active
    Driver Activation Cmd: "modprobe atl1c"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (PCI bridge)


Sorry, here is the output hidden above.

---

### Post by SteveS1949 on 2010-09-03
The only output with a HW address and a 'eth0' or similar tag is my eth0 and my usb0.

---

### Post by cariboo on 2010-09-03
One last thing, I just tried lshw on my netbook, and it works again. Could you post the output of:

```
lshw -C network
```

---

### Post by SteveS1949 on 2010-09-03
I am running now. But last time i tried, it crashed my netbook :)

---

### Post by SteveS1949 on 2010-09-03
*-network UNCLAIMED     
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:95100000-95101fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:82:53:5c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 multicast=yes
       resources: irq:44 memory:93000000-9303ffff ioport:1000(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: ee:61:4a:20:9e:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.55 multicast=yes

---

### Post by cariboo on 2010-09-03
Your wireless device didn't show up in the listing you posted, is should have at least showed unclaimed. I don't suppose you know what driver it was using in Luicd?

Try:

```
sudo rmmod iwlagn
```

The reboot to see if the same driver, or another gets loaded.

---

### Post by SteveS1949 on 2010-09-03
It did show up as unclaimed... The top of the list. ill reboot now

---

### Post by SteveS1949 on 2010-09-03
*-network UNCLAIMED     
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:95100000-95101fff

This was after the command + reboot.

I am downloading the 10.04 iso and will boot live and test when it completes (6 mins on my connection). What do you think it could be?

---

### Post by SteveS1949 on 2010-09-03
This is the output of lshw -C network from 10.04

*-network               
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 09
       serial: 00:15:00:56:f7:90
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:95100000-95101fff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:82:53:5c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:93000000-9303ffff ioport:1000(size=128)

---

### Post by cariboo on 2010-09-03
According to your output, it looks like wireless should work now. Can you connect?

---

### Post by seeker5528 on 2010-09-03
Looks to me like Centrino Ultimate-N 6300 should be supported by in-kernel drivers with firmware included in the linux-firmware package, you might want to install the wireless module backports to see if it makes a difference, currently linux-backports-modules-wireless-2.6.35-19-generic in Maverick.

Later, Seeker

---

### Post by SteveS1949 on 2010-09-03
The previous output was from 10.04 not 10.10 So Maverick is still bust...

I am just about to test the backports

---

### Post by SteveS1949 on 2010-09-03
Tried the backports install, I wasnt sure what to do so i just installed via synaptic and restarted. If that is the process, it has not helped :(

---

### Post by SteveS1949 on 2010-09-04
Update:

This is my output from 'dmesg | grep iwlagn'

[    8.038681] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    8.038690] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    8.038819] iwlagn 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.038835] iwlagn 0000:01:00.0: setting latency timer to 64
[    8.038891] iwlagn 0000:01:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[    8.054863] iwlagn 0000:01:00.0: Unsupported (too old) EEPROM VER=0x423 < 0x434 CALIB=0x5 < 0x4
[    8.055025] iwlagn 0000:01:00.0: PCI INT A disabled
[    8.055048] iwlagn: probe of 0000:01:00.0 failed with error -22

lspci -v

01:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 09)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: fast devsel, IRQ 16
    Memory at 95100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel modules: iwlagn

lshw -C network

  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:95100000-95101fff


Any ideas?

---

### Post by seeker5528 on 2010-09-04
According to this:

> **SteveS1949 said:**
> [    8.054863] iwlagn 0000:01:00.0: Unsupported (too old) EEPROM VER=0x423 < 0x434 CALIB=0x5 < 0x4

Looks like your version of the hardware is not supported anymore by the newer driver.

You might have to go to the upstream to see if there is a solution....

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

Later, Seeker

---

### Post by Scallyph on 2010-09-04
Hi, 
I'm not sure but would  ndiswrapper would help you?

---

### Post by ktp on 2010-09-04
> **SteveS1949 said:**
> Update:

This is my output from 'dmesg | grep iwlagn'

[    8.038681] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    8.038690] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    8.038819] iwlagn 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.038835] iwlagn 0000:01:00.0: setting latency timer to 64
[    8.038891] iwlagn 0000:01:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[    8.054863] iwlagn 0000:01:00.0: Unsupported (too old) EEPROM VER=0x423 < 0x434 CALIB=0x5 < 0x4
[    8.055025] iwlagn 0000:01:00.0: PCI INT A disabled
[    8.055048] iwlagn: probe of 0000:01:00.0 failed with error -22

lspci -v

01:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 09)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: fast devsel, IRQ 16
    Memory at 95100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel modules: iwlagn

lshw -C network

  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:95100000-95101fff


Any ideas?

This thread might be worth reading also:

[http://ubuntuforums.org/showthread.php?t=1546409](http://ubuntuforums.org/showthread.php?t=1546409)

---

### Post by SteveS1949 on 2010-09-04
Right,

I have tried ndiswrapper earlier to no avail. I have now got a copy of the ucode driver and copied it to /lib/fimware

What else am i supposed to do to get it to load the driver?

Is there currently an issue with the iwlagn and 10.10?

---

