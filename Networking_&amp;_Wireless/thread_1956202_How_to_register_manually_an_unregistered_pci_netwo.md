---
title: "How to register manually an unregistered pci network card"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by HotForLinux on 2012-04-10
After booting, a wifi card is not registered, but its driver: ipw2200, is loaded. How can I manually register the net card? with **setpci** ?

The following lines are extracted from the output of [B]dmesg:

[/B]```

[    0.101562] PCI: Using ACPI for IRQ routing
[    0.101649] PCI: pci_cache_line_size set to 64 bytes
[    0.101696] pci 0000:05:06.0: address space collision: [mem 0x13000000-0x13000fff] conflicts with System RAM [mem 0x00100000-0x7f7dfffb]
[    0.101761] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.101765] reserve RAM buffer: 000000007f7dfffc - 000000007fffffff 
....
[    2.361793] udev: starting version 151
[    2.377119] udevd (83): /proc/83/oom_adj is deprecated, please use /proc/83/oom_score_adj instead.
[    2.477446] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    2.485923] sky2: driver version 1.30
[    2.542530] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[    2.561248] sky2 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.573845] sky2 0000:01:00.0: setting latency timer to 64
[    2.573882] sky2 0000:01:00.0: Yukon-2 FE chip revision 1
[    2.578973] sky2 0000:01:00.0: irq 18 for MSI/MSI-X
[    2.676037] sky2 0000:01:00.0: No interrupt generated using MSI, switching to INTx mode.
[    2.681755] sky2 0000:01:00.0: eth0: addr 00:a0:d1:bb:ae:17
[    5.064691] aufs 3.2-20120109
......
[   68.912204] udev: starting version 151
[   72.639990] intel_rng: FWH not detected
[   73.845070] lib80211: common routines for IEEE802.11 drivers
[   73.845076] lib80211_crypt: registered algorithm 'NULL'
.....
[   78.469978] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[COLOR=Red][   78.720198] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   78.720206] ipw2200: Unable to load firmware: -2
[   78.720214] ipw2200: failed to register network device
[   78.724318] ipw2200 0000:05:04.0: PCI INT A disabled
[   78.724378] ipw2200: probe of 0000:05:04.0 failed with error -5[/COLOR]
[   80.007877] cfg80211: World regulatory domain updated:
[   80.007884] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   80.007889] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   80.007894] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   80.007898] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   80.007902] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   80.007906] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   82.261353] sky2 0000:01:00.0: eth0: enabling interface
[   82.265825] ADDRCONF(NETDEV_UP): eth0: link is not ready


```

---

### Post by nothingspecial on 2012-04-11
*Thread moved to **Networking & Wireless**.*

---

### Post by roelforg on 2012-04-11
It ain't unregisterd,
it's broken.
 
Linux can't read firmware info from it and it's useless if it can't.
 
EDIT: Try pulling the card out (after turning off!), blow in the slot and reinstall it.
There may be some dust in the socket causing communication failures.

---

### Post by HotForLinux on 2012-04-11
> **roelforg said:**
> It ain't unregisterd,
it's broken.
 
Linux can't read firmware info from it and it's useless if it can't.
 
EDIT: Try pulling the card out (after turning off!), blow in the slot and reinstall it.
There may be some dust in the socket causing communication failures.

Broken? broken what? the wifi netcard? ... It works perfectly well!. It has been working well and continues working well with dozens of systems. It is not a USB wifi, it is inside a laptop. I ignore if it is integrated in the MB but it has an external switch.

---

### Post by HotForLinux on 2012-04-18
I have booted thousand of times and dozens of times after this post.
It has only failed with two distros based on ubuntu: always with these ones and only with these ones. Come on! How do you want me to think that the wifi card is broken?
There must be a walk around this problem!
Can anyone help?

```
[   82.194884] mmc1: SDHCI controller on PCI [0000:05:06.4] using PIO
[   82.194914] mmc2: no vmmc regulator found
[   82.195015] Registered led device: mmc2::
[   82.196416] mmc2: SDHCI controller on PCI [0000:05:06.4] using PIO
[   82.369126] cfg80211: Calling CRDA to update world regulatory domain
[COLOR=Red][   82.834656] libipw: 802.11 data/management/control stack, git-1.1.13
[   82.834662] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   83.812504] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   83.812511] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   83.812651] ipw2200 0000:05:04.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   83.812683] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[/COLOR]
[   83.975448] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x300-0x377
[   83.985653] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   83.986408] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   83.987031] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   83.987716] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xe0000-0xfffff
[   83.987784] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   83.987849] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   83.987917] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[COLOR=Red][   84.843653] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   84.843661] ipw2200: Unable to load firmware: -2
[   84.843665] ipw2200: failed to register network device
[   84.843716] ipw2200 0000:05:04.0: PCI INT A disabled
[   84.843766] ipw2200: probe of 0000:05:04.0 failed with error -5
[COLOR=Black][   87[/COLOR][/COLOR][COLOR=Black].16[/COLOR]7149] cfg80211: World regulatory domain updated:
[   87.167155] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   87.167160] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   87.167164] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   87.167168] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
```

---

### Post by matt_symes on 2012-04-18
Hi

> After booting, a wifi card is not registered, but its driver: ipw2200,  is loaded. How can I manually register the net card? with **setpci** ?I don't think that will fix this. setpci is use to set pci configuration space values.

It looks like the issue is with the firmware udev loads for the wireless device.

This is from the firmware documentation.
> 
2.  The following error appears in the dmesg kernel ring buffer output:
ipw2200: ipw-2.4-boot.fw load failed: Reason -2
ipw2200: Unable to load firmware: -2
ipw2200: failed to register network device
ipw2200: probe of 0000:02:03.0 failed with error -5
 
CAUSE: this may be due to any one of the following reasons:
-  firmware in wrong location or wrong firmware version. Follow the
   instructions in the section LOADING FIRMWARE VIA HOT-PLUG above.
-  sysfs may not be mounted. Follow the instructions in the SYSFS section
   above.[FONT=monospace]
What exact card and model of card do you have ? Is it an[/FONT] Intel PRO/Wireless 2200BG ?

[FONT=monospace]Have a read of this. If you have the same card then this fixed it for them.

[http://www.jukie.net/bart/blog/ipw2200-firmware](http://www.jukie.net/bart/blog/ipw2200-firmware)

EDIT: You edited your post while i was typing this one. Your card is different but it still think it's loading the wrong firmware for your card.

Kind regards

[/FONT]

---

### Post by chili555 on 2012-04-18
Matt, I'd be interested to see if OP has the firmware at all and if it's in any way corrupted:```
ls /lib/firmware | grep ipw2200
md5sum /lib/firmware/ipw2200-bss.fw
```Here is my result, for comparison:> $ md5sum /lib/firmware/ipw2200-bss.fw
[COLOR="Red"]045a46163341514ef17490c76bd0c858[/COLOR]  /lib/firmware/ipw2200-bss.fwOK, back to our regularly scheduled Jedi, Matt.

---

### Post by HotForLinux on 2012-04-19
What exact card and model of card do you have ? Is it an Intel PRO/Wireless 2200BG ?

> **matt_symes said:**
> Hi

I don't think that will fix this. setpci is use to set pci configuration space values.

It looks like the issue is with the firmware udev loads for the wireless device.


Do you know where does it loads it from?


> **matt_symes said:**
> 
What exact card and model of card do you have ? Is it an Intel PRO/Wireless 2200BG ?


That's what dmesg, as well as other commands say.


> **matt_symes said:**
> 
Have a read of this. If you have the same card then this fixed it for them.

[http://www.jukie.net/bart/blog/ipw2200-firmware](http://www.jukie.net/bart/blog/ipw2200-firmware)


I'll do that as soon as we clear out what is my card. Shouldn't I?


> **matt_symes said:**
> 
EDIT: You edited your post while i was typing this one. Your card is different but it still think it's loading the wrong firmware for your card.


Now I am puzzled. Do you mean that it might not be an Intel PRO/Wireless 2200BG?
Do you want me to post the output of other commands? or what do we need?
Thanks

---

### Post by HotForLinux on 2012-04-19
Chili555:
What does OP mean?

Look these outputs after booting Ubuntu Hardy, in the same PC, where this wifi card can be used with no problem:

```

**$ ls /lib/firmware/2.6.24-31-generic/ipw***
/lib/firmware/2.6.24-31-generic/ipw2100-1.3.fw
/lib/firmware/2.6.24-31-generic/ipw2100-1.3-i.fw
/lib/firmware/2.6.24-31-generic/ipw2100-1.3-p.fw
/lib/firmware/2.6.24-31-generic/ipw2200-bss.fw
/lib/firmware/2.6.24-31-generic/ipw2200-ibss.fw
/lib/firmware/2.6.24-31-generic/ipw2200-sniffer.fw

**$ md5sum /lib/firmware/2.6.24-31-generic/ipw***
dc1cece9f906f57a98f5a3859dba3e28  /lib/firmware/2.6.24-31-generic/ipw2100-1.3.fw
b956daaa9e59be94ebdf6df0b3365cb6  /lib/firmware/2.6.24-31-generic/ipw2100-1.3-i.fw
a03e4e0a85242356b1d5a1d489fa3a7f  /lib/firmware/2.6.24-31-generic/ipw2100-1.3-p.fw
f0216818744e31f769098c7310688e97  /lib/firmware/2.6.24-31-generic/ipw2200-bss.fw
8bd8a347b63aa732eb36d6b00ab660b4  /lib/firmware/2.6.24-31-generic/ipw2200-ibss.fw
d57c836007d5245522ddbb030e21749c  /lib/firmware/2.6.24-31-generic/ipw2200-sniffer.fw

from **$ sudo lshw -class network**:
*-network
    description: Wireless interface
    product: PRO/Wireless 2200BG Network Connection
    vendor: Intel Corporation
    physical id: 4
    bus info: pci@0000:05:04.0
    logical name: eth1
    version: 05
    serial: 00:0e:35:e4:21:84
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.128 latency=128 maxlatency=24 mingnt=3 module=ipw2200 promiscuous=yes wireless=IEEE 802.11g

from **$ lspci -vv**:
 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
    Subsystem: Intel Corporation Unknown device 2741
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 128 (750ns min, 6000ns max)
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at b800b000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=1 PME-

```

---

### Post by chili555 on 2012-04-19
> Chili555:
What does OP mean?
Original Poster; i.e. you.> I'll do that as soon as we clear out what is my card. Shouldn't I?I'm pretty sure it's an Intel 2200 or 2915. Check:```
lspci -nn | grep 0280
```> look this outputs using Ubuntu Hardy where this wifi card can be used with no problem:Are you dual-booting with Hardy? Do you have another identical computer?? What is the md5sum where it is *NOT* working?

Here is my result, running 12.04:> $ md5sum /lib/firmware/ipw*
dc1cece9f906f57a98f5a3859dba3e28  /lib/firmware/ipw2100-1.3.fw
b956daaa9e59be94ebdf6df0b3365cb6  /lib/firmware/ipw2100-1.3-i.fw
a03e4e0a85242356b1d5a1d489fa3a7f  /lib/firmware/ipw2100-1.3-p.fw
[COLOR="Red"]045a46163341514ef17490c76bd0c858[/COLOR]  /lib/firmware/ipw2200-bss.fw
44cdedc8d5a0eb727466ed982db97a53  /lib/firmware/ipw2200-ibss.fw
ebc70dce66f876695fa8852b8ff757ee  /lib/firmware/ipw2200-sniffer.fwNotice the md5sum is different; I take that to mean either yours is an older version or it's corrupted. I'm hoping Matt will chime in with his thoughts. He or I can provide our copies for you to replace.

---

### Post by HotForLinux on 2012-04-19
Thanks.

No identical PC. It's just that we boot this PC with Hardy (dual with windos, which is used very very very seldom ... what for??) and we boot other distros from live CDs. So, unless I clarify, the outputs are from Hardy where the wifi works perfectly as it does with almost all distros.


**$ lspci -nn | grep 0280**
05:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)

>                               look this outputs using Ubuntu Hardy where this wifi card can be used with no problem:                      All the ipw[COLOR=Red]2200[/COLOR]'s are different. But how can it work well in almost all distros if it is corrupted?

_Note_: I have the same md5sums for the firmware files in  .../2.6.24-30-generic/

---

### Post by chili555 on 2012-04-19
I'm getting more confused as we go! Maybe I'm getting too old. Where, exactly, does it *NOT* work? Maybe I don't understand the problem.> t ain't unregisterd,
it's broken.

Linux can't read firmware info from it and it's useless if it can't.I have had perfectly operating 2200s and 2915s in Linux as recently as 11.10 a few weeks ago. I only got rid of it because the motherboard failed and I was looking for an excuse to get a newer Thinkpad. This statement may be true only for roelforg, but not for me.

---

### Post by HotForLinux on 2012-04-19
I understand it is confusing because I started talking about the problem in a distro based in ubuntu which boots but the wlan is left aside, so I posted the error lines from the output of dmesg after booting it; and I said that the same wifi, in the same PC (not an equivalent one), works perfectly well with other distros, but it only fails, and it always does, with a couple among all the ones we have tried. This, I think, proves that the wifi card is not broken but that the problem is of a different kind. Then I posted the output of certain commands executed in Hardy (because it is easier to copy them and post them here) to see if we could determine what wifi we are dealing with. 

I thought what is the use of examining the firmware in a distro that boots ok (Hardy, installed in HD), but I did not know what were you after.
I will post the output of the firmware commands using the LiveCD, ok?

---

### Post by chili555 on 2012-04-19
> I thought what is the use of examining the firmware in a distro that boots okExactly, but it's also useless to post *any* diagnostics from a computer that works. If I want to see the modinfo, the firmware, etc. I have several computers of my own.> I did not know what were you after.I am trying to see what's wrong or missing on the system that's *not* working.> I will post the output of the firmware commands using the LiveCD, ok? Yes. Do you mind telling us what it is? 

Here are some things to look at:```
modinfo ipw2200
```See what firmware it wants and where it expects to find it:```
$ modinfo ipw2200
filename:       /lib/modules/3.0.0-17-generic-pae/updates/cw-3.1/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw

```Check dmesg for firmware messages:```
dmesg | grep ipw
```See if the firmware exists where the module expects it. With no further data in modinfo, firmware is expected to be in /lib/firmware and in older distributions, /lib/firmware/<kernel_version>```
ls /lib/firmware | grep ipw2200
ls /lib/firmware/`uname -r` | grep ipw2200
```Those tickmarks are on the same key with ~ on my US keyboard. `uname -r` is a quick way to ask the system for your running kernel version.

A number of distros, Arch comes to mind, omit firmware that's commonly installed by default in Ubuntu. Arch, Gentoo and Slackware are all distros for guys who walk eight miles to work and don't use air-conditioning! 

No more Hardy, please.

---

### Post by HotForLinux on 2012-04-19
After Booting the live CD, I executed the following commands and copied the significant lines:

```
**$ lsmod | grep ipw **
ipw2200               140278  0 
libipw                 45395  1 ipw2200
cfg80211              160399  2 ipw2200,libipw
lib80211               13683  2 ipw2200,libipw


**$ lspci -v| egrep -i "ipw|wifi|wire"**
05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Kernel modules: ipw2200

**$ lshw -c network**
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:bb:ae:17
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:11 memory:cc000000-cc003fff ioport:c000(size=256)

  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=128 maxlatency=24 mingnt=3
       resources: memory:b800b000-b800bfff

**$ ls /lib/firmware/** 
....
iwlwifi-1000-3.ucode
iwlwifi-1000-5.ucode
iwlwifi-100-5.ucode
iwlwifi-3945-2.ucode
....
shows no files nor dirs called "ipw*", but I missed looking inside the subdirectories:
2.6.32-28-generic
3.2.4
3.2.6
should I?


```

---

### Post by chili555 on 2012-04-19
> but I missed looking inside the subdirectories:
2.6.32-28-generic
3.2.4
3.2.6
should I?Please look here:```
ls /lib/firmware/`uname -r` | grep ipw2200
```

---

### Post by HotForLinux on 2012-04-19
> A number of distros, Arch comes to mind, omit firmware that's commonly  installed by default in Ubuntu. Arch, Gentoo and Slackware are all  distros for guys who walk eight miles to work and don't use  air-conditioning! 

Hahaha!! ... I'm learning a lot!!!

> No more Hardy, please.
Ok. The output of dmesg in the original post is from the system in the LiveCD, not Hardy, and I'll post the other results later and after checking if you ask for something else in the list.

---

### Post by chili555 on 2012-04-19
From the not-working live CD *only*, please.```
dmesg | grep ipw
ls /lib/firmware/`uname -r` | grep ipw2200
sudo updatedb
locate ipw2200-bss.fw
```updatedb will take a few moments, please be patient. If the firmware is missing, simply transfer it from another system on a USB key and drop it into /lib/firmware and /lib/firmware/`uname -r`. Unload and reload the driver:```
sudo modprobe -r ipw2200
sudo modprobe ipw2200
```So which distro is it?

---

### Post by HotForLinux on 2012-04-19
[COLOR=Red]**Perfect!!**[/COLOR] 

The firmware files were nowhere. The only reference I found was this broken link.

**# ls -l /dev/.udev/firmware-missing/**
total 0
lrwxrwxrwx 1 root root 67 2012-04-19 22:15 ipw2200-bss.fw -> /devices/pci0000:00/0000:00:1e.0/0000:05:04.0/firmware/0000:05:04.0

but copying the ones I use in Hardy and reloading the module, as you told me, worked perfectly. In addition, I understand a little better how this works. Thanks a lot, Chili555!

So... during the boot process, I don't know how, the system detects the hw, and according to that loads certain modules. The command modinfo tells us the location in the file system of the module whose name we give as a parameter (which should normally be in /lib/modules/$(uname -r)/kernel/drivers) and the firmware files needed by the module to work (which should be in /lib/firmware or inside the kernel-in-use directory) -- I thought the firmware was inside the devices and read by the drivers!--. Then, reloading the module we force it to fetch and read again those files that it needs to work.

Should I post all the results just for the record?

My problem now is how to put the firmware files inside the LiveCD because when I mount its corresponding ISO file, everything is inside a squashfs file and I do not know how to work with it.

---

### Post by chili555 on 2012-04-19
> So... during the boot process, I don't know how, the system detects the hw, and according to that loads certain modules. The command modinfo tells us the location in the file system of the module whose name we give as a parameter and the files needed by the module to work (I thought the firmware was inside the devices and read by the drivers!). Then, reloading the module we force it to fetch and read again the files it needs to work.Pretty close to exactly. *modinfo* is actually a human readable extract of useful information from the actual driver. Most of us don't read python or c++.

Some drivers don't require firmware; viz:```
$ modinfo r8187se
filename:       /lib/modules/3.2.0-23-generic-pae/kernel/drivers/staging/rtl8187se/r8187se.ko
description:    Linux driver for Realtek RTL8180 / RTL8185 WiFi cards
author:         Andrea Merello <andreamrl@tiscali.it>
license:        GPL
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
<snip>
srcversion:     8F6B9881D2F05C4A11E407D
alias:          pci:v000010ECd00008199sv*sd*bc*sc*i*
depends:        eeprom_93cx6
staging:        Y
intree:         Y
vermagic:       3.2.0-23-generic-pae SMP mod_unload modversions 686 
parm:           ifname:string
parm:           devname: Net interface name, wlan%d=default
parm:           hwseqnum: Try to use hardware 802.11 header sequence numbers. Zero=default (int)
parm:           hwwep: Try to use hardware WEP support. Still broken and not available on all cards (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

```^^ See, no firmware is mentioned.> Should I post all the results just for the record?Nope. The driver genies out there see it, and probably faster than I did!> My problem now is how to put the firmware files inside the LiveCD because when I mount the ISO everything is inside a squashfs file. Some pretty advanced ideas come to mind. You might Google up 'mount -o loop' or else remastersys.

I'm glad it's working.

---

