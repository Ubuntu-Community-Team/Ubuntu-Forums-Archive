---
title: "Sporadic Wifi Problem in Natty with Thinkpad X201"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by jullyfush on 2011-06-07
I've had recurring problems with Ubuntu wifi on my Thinkpad before. Usually powering down and toggling the physical wifi switch off, then toggling wifi on again after the system has booted would solve the problem.

This time that isn't working. Wireless is completely absent from the network-manager applet.

[IMG]http://i440.photobucket.com/albums/qq122/jullyfush/wireless.png[/IMG]

Wireless works for me 99% of the time for me, but every few months will "disappear" for some reason. Does anyone have any advice or know a thread they can point me to? I've posted the results for 'lspci -k', iwconfig and 'lshw -C network' bellow: 

```
$:lspci -k

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Lenovo Device 2193
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Lenovo Device 215a
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Lenovo Device 215f
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
	Subsystem: Lenovo Device 2162
	Kernel driver in use: serial
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
	Subsystem: Lenovo Device 2153
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
	Subsystem: Lenovo Device 2163
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Lenovo Device 215e
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
	Subsystem: Lenovo Device 2163
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Lenovo Device 2166
	Kernel modules: iTCO_wdt
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
	Subsystem: Lenovo Device 2169
	Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Lenovo Device 2167
	Kernel modules: i2c-i801
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
	Subsystem: Lenovo Device 216a
	Kernel driver in use: ata_piix
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: Lenovo Device 2190
	Kernel driver in use: intel ips
	Kernel modules: intel_ips
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Lenovo Device 2196
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Lenovo Device 2196
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Lenovo Device 2196
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Lenovo Device 2196
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Lenovo Device 2196
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Lenovo Device 2196
```

```
$: iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```

```
$: sudo lshw -C network

*-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 5c:ff:35:04:fb:11
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.12-1 ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)

```

---

### Post by rpdillon on 2011-06-07
So, I've been tackling this problem for weeks now.  It worked really well for some time on my X201, and since I did an update a few weeks ago to Natty, wireless is anything from sporadic (requiring frequent reassociation to the AP) to causing complete system hangs than require hard reboots.

I've found very limited public acknowledgement of the problem, so I thought I'd chime in here to let you know that it's not just you.

Currently, I'm using the laptop wired, which is really awful for my needs.  I've been tracking Linux Wireless nightlies and building them and installing them in hopes of an improvement, but have gotten nowhere so far.

I saw a posting indicating that a change back in mid-May caused the issue, so I tried rolling back to early-May, then mid-April and finally early-April builds of Linux wireless, but they aren't compiling for me on Natty, unlike the more recent builds that do, so I haven't had any luck going that route either.

There have been scattered posts about using the drivers from RealTek, but most user recommend against it for stability reasons, so I haven't explored that yet.

I'll watch this thread and post updates as I try things.

---

### Post by jullyfush on 2011-06-07
Wow, thanks for the info. Sounds like you're spending a lot of time on this too. I've looked into this before, but the problem would resolve itself without a clear reason. So now I'm in the same boat again.

I've experimented with the RealTek driver and also tried replacing the Network Manager with Wicd, both without luck...

There are a lot of threads on this, so hopefully somebody will figure it out soon!

---

### Post by jullyfush on 2011-06-07
I made a post over on Launchpad in case you want to follow. I'll post anything useful back over here asap.

[https://answers.launchpad.net/ubuntu/+question/160581](https://answers.launchpad.net/ubuntu/+question/160581)

---

### Post by jullyfush on 2011-06-08
I tried installing linux-backports-modules-net-natty-generic via synaptic and rebooted, but the problem persists.

---

### Post by jullyfush on 2011-06-08
I've just discovered that if I use an Ubuntu install cd/usb and select 'try Ubuntu without installing' that wireless suddenly works again (only while in trial mode) like it used to.

So, it's definitely not a hardware problem. I guess, I've either installed something that broke wireless or an update did it.

---

### Post by jullyfush on 2011-06-08
So, I got tired of sifting through countless threads and getting nowhere. I was messing around with the live cd and noticed that I could upgrade from 11.04 to 11.04 while keeping all my files and many of my preferences.

I tried it and it eventually worked, but it was NOT SMOOTH. A few things broke and after boot I just had a blank desktop with nothing there, no power button, nothing.

Nautilus couldn't create some folders before launching, so I had to do it manually. ctrl + alt + t luckily still brought up the terminal so I could create the files and then launch Unity. Update Manager was hanging because a file was corrupted, but after I commented out a repository it worked.

After an update everything is working again, including wireless.

I would NOT recommend this way as it barely worked for me and I'm not sure how stable everything is any more. And I'd still really like to know what was wrong with wireless in the first place in case it happens again.

---

### Post by Spike the Dingo on 2011-07-30
I think I may be having the same issue (Thinkpad X201) with Natty (amd64) and now Oneiric. Has anyone filed a bug report on this?

---

