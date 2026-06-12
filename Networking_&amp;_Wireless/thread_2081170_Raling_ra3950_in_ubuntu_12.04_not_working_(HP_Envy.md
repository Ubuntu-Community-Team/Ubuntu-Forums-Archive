---
title: "Raling ra3950 in ubuntu 12.04 not working (HP Envy m4-1015dx)"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by mabelzunce on 2012-11-06
Hi, 
My wireless adapter is not working in ubuntu 12.04. The adapter is the ralink rt5390 in a HP envy m4-1015dx laptop.
The system doesn't loads any driver module for this adapter. I've tried installing the ralink driver in:
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
But I couldn't make it work. I could compiled and install the rt5390sta module but it is not associated with my adapter. I've seen other threads solving this for previous versions of ubuntu but not for 12.04.
Some info about my system:

$iwconfig
lo        no wireless extensions.
eth0      no wireless extensions

$ sudo rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no[/CODE]```
$lspci -vv

$sudo lspci -vv
02:00.0 Network controller: Ralink corp. Device 539b
    Subsystem: Hewlett-Packard Company Device 18ed
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at c0600000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
```[CODE]$ sudo uname -r
3.2.0-32-generic

Please, if anybody knows how to fixed this I will appreciate it.

Martin

---

### Post by shadowlab on 2012-12-04
Any luck with this problem? I was considering buying this same laptop, but now I'm a little hesitant.

Thanks, Kevin.

---

### Post by chili555 on 2012-12-04
I'm not quite sure why the OP got no reply, it's fairly easy to get this device working. In fact, in Ubuntu 12.10, the driver is built-in: rt2800pci.

---

### Post by mabelzunce on 2012-12-26
It's true that in ubuntu 12.10 the wireless works with rt2800pci driver. But in ubuntu 12.04 the adapter is unclaimed even with that driver that is built-in in the kernel. I couldn't make it work in 12.04.
I've been using 12.10 for a few weeks, but the / and /home partitions were mounted all the time as read only because of a supossed error in the filesystem. This was reported as a bug in 12.10 and it's impossible to work with that bug. So I decided to downgrade to 12.04 and I am still without succes with the wireless adapter.

---

### Post by chili555 on 2012-12-26
> **mabelzunce said:**
> It's true that in ubuntu 12.10 the wireless works with rt2800pci driver. But in ubuntu 12.04 the adapter is unclaimed even with that driver that is built-in in the kernel. I couldn't make it work in 12.04.
I've been using 12.10 for a few weeks, but the / and /home partitions were mounted all the time as read only because of a supossed error in the filesystem. This was reported as a bug in 12.10 and it's impossible to work with that bug. So I decided to downgrade to 12.04 and I am still without succes with the wireless adapter.Do you have the same device 1814:539B?```
lspci -nn | grep 0280
```We can probably get it working fairly easily.

---

### Post by mcwescott on 2012-12-27
support for 539b chip didn't show up until 2012-05-16. Currently in the 3.5.7 and 3.6.11 kernels (as well as even later kernels).

use one of the backport meta packages:

linux-backports-modules-cw-3.5-precise-generic
linux-backports-modules-cw-3.6-precise-generic

---

### Post by dg520 on 2012-12-30
I'm having the same problem with an HP Pavilion p7-1420t. I have an RALink RT5390.

I tried following the instructions here but have not been successful:
[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

I also tried calling "sudo apt-get install linux-backports-modules-cw-3.6-precise-generic", still no luck.

iwconfig:
```
lo        no wireless extensions.
eth0      no wireless extensions.
```

lspci -vv:
```
...
03:00.0 Network controller: Ralink corp. Device 539b
    Subsystem: Hewlett-Packard Company Device 18ed
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at f7d00000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel modules: rt2800pci
...

```

I'm a bit of a linux newbie. Any suggestions on how to fix this? Thank you.

---

### Post by chili555 on 2012-12-30
> **dg520 said:**
> I'm having the same problem with an HP Pavilion p7-1420t. I have an RALink RT5390.

I tried following the instructions here but have not been successful:
[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

I also tried calling "sudo apt-get install linux-backports-modules-cw-3.6-precise-generic", still no luck.

I'm a bit of a linux newbie. Any suggestions on how to fix this? Thank you.Please let us see:```
sudo modprobe rt2800pci
dmesg | grep -i rt2
rfkill list all
```Thanks.

---

