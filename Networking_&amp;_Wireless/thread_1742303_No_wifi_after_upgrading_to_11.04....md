---
title: "No wifi after upgrading to 11.04..."
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by funnysnoot on 2011-04-28
...and I even tried re-installing, but still nothing.

Here's the output of my rfkill list all:

```

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: i2400m-usb:2-1.4:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

So, something that is bizarre is that I have no idea what the acer-wireless device is. Wasn't there in Maverick. When I upgraded it was set to position 0, and the device ideapad_wlan was at position 0. Now they've flip-flopped.

I've even tried the rfkill unblock all, but that doesn't seem to help.

Any ideas?

Thanks.

---

### Post by akin-lombok on 2011-04-28
have you try to use rfkill unblok wifi ???

---

### Post by funnysnoot on 2011-04-28
Yeah, I tried that too after looking at a bunch of posts on here with folks with similar problems as mine...I went through a whole slew of rfkill commands to no avail.

I think once I finish syncing all of my files to Ubuntu One, I'm just going to format and install from scratch and see where that gets me, unless there is something else I might try in the interim...

---

### Post by josephmills on 2011-04-28
```
lspci -nn 
```
```
sudo lshw -C network
```
please take out all ip address thanks

---

### Post by funnysnoot on 2011-04-28
> **josephmills said:**
> ```
lspci -nn 
```
```
sudo lshw -C network
```
please take out all ip address thanks

For lspci -nn:

```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
04:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0089] (rev 5f)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

```

For lshw -C network:

```

  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f2400000-f243ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 5f
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic-pae firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:f2500000-f2501fff
  *-network
       description: Ethernet interface
       physical id: 4
       bus info: usb@2:1.4
       logical name: wmx0
       serial: 
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i6050-fw-usb-1.5.sbcf link=no

```

---

### Post by josephmills on 2011-04-28
```
 dmesg | grep iwl
```
```
lsmod | grep dell
```
thanks

---

### Post by funnysnoot on 2011-04-28
> **josephmills said:**
> ```
 dmesg | grep iwl
```
```
lsmod | grep dell
```
thanks

For dmesg | grep iwl (note: I've never used the WiMax device before):

```

[   32.079980] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   32.079983] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   32.080085] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   32.080121] iwlagn 0000:04:00.0: setting latency timer to 64
[   32.080198] iwlagn 0000:04:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[   32.090161] iwlagn 0000:04:00.0: device EEPROM VER=0x554, CALIB=0x6
[   32.090163] iwlagn 0000:04:00.0: Device SKU: 0Xb
[   32.090185] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   32.090334] iwlagn 0000:04:00.0: irq 42 for MSI/MSI-X
[   32.574531] iwlagn 0000:04:00.0: loaded firmware version 41.28.5.1 build 33926
[   32.786012] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  835.507301] iwlagn 0000:04:00.0: RF_KILL bit toggled to enable radio.
[ 1037.423964] iwlagn 0000:04:00.0: RF_KILL bit toggled to disable radio.
[ 1050.355660] iwlagn 0000:04:00.0: RF_KILL bit toggled to enable radio.

```

For lsmod | grep dell (note: I changed dell to ideapad since I don't have a dell):

```

ideapad_laptop         13262  0 
sparse_keymap          13666  2 acer_wmi,ideapad_laptop

```

Thanks for your help.

---

### Post by josephmills on 2011-04-28
what kind of computer is this?

---

### Post by josephmills on 2011-04-28
> For lsmod | grep dell (note: I changed dell to ideapad since I don't have a dell):
do you get any thing with? 
```

lsmod | grep dell 

```
thanks

---

### Post by willm.wade on 2011-04-28
I just fixed (seconds ago) this issue.  blacklist acer-wmi.  Not sure what all it does, but it is causing the issue with the wireless.

---

### Post by funnysnoot on 2011-04-28
> **josephmills said:**
> do you get any thing with? 
```

lsmod | grep dell 

```
thanks

Nah, I tried it and it returned nothing, that's why I switched "dell" with "ideapad" and it returned what you saw above.

---

### Post by funnysnoot on 2011-04-28
> **willm.wade said:**
> I just fixed (seconds ago) this issue.  blacklist acer-wmi.  Not sure what all it does, but it is causing the issue with the wireless.

How does one "blacklist" a device? Thanks in advance...

---

### Post by Stord on 2011-04-28
You place in one of the  .conf files in /etc/modprobe.d/
the statement 

blacklist device

I think they forgot to unblacklist some stuff, like various wireless drivers that didnt previoiusly work but now do...

On startup, blacklisted devices are soft blocked . so 'rfkill unblock all' should unblock all these soft blocks...

---

### Post by funnysnoot on 2011-04-28
Thanks, Stord. That did the trick.

And thanks to willm and joseph for you input.

Blacklisting the acer-wmi solved it. I assume this can be reported somewhere. How would one go about doing that?

---

### Post by eortiz on 2011-04-29
The blacklisting worked perfectly. I have a Lenovo Ideapad v560 and was experiencing the exact same issue.

Thanks a lot!

---

### Post by tom67 on 2011-04-30
Thanx willm.wade[]("http://ubuntuforums.org/member.php?u=1020440") and Stord, it workes also for my acer notebook (atheros wifi card). You saved my eyes from browsing another several hours on tiny cellphone screen (and time as well) when looking for solution. 
Anyway, I like the new ubuntu 11.04, at last the suspend and hibernate function is working on acer emachines g640, finally.

---

