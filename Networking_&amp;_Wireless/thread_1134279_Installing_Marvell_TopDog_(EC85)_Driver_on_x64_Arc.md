---
title: "Installing Marvell TopDog (EC85) Driver on x64 Architecture"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by ok123jump on 2009-04-23
**HELP!!!!**

I have been trying for days to get my on-board wifi working for my Gateway M-6319 laptop. There are several posts describing how to get this to work, but none which are applicable to 64-bit architecture.

Here are the sites that I've used and am 99% of the way done:

1.) [mt6456 marvell topdog 802.11n Wireless (EC85) Solved]("http://ubuntuforums.org/showthread.php?t=575785")

2.) [Gateway M-6750 Marvell TOPDOG (EC85) Vista Driver Issue]("http://www.pcreview.co.uk/forums/thread-3459428.php")

3.) [DRIVER NEEDED: Marvell® Marvell TOPDOG PCI Express 802.n wireless (EC85) (Windows XP Professional)]("http://forums.driverguide.com/showthread.php?t=37046&vforum=0c2329d12")



***Here are the steps I've taken - with output:***

*IN TERMINAL*

1) **lspci -nn**

05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a08] (rev 03)

*-- I downloaded and installed the driver the Netgear WNR311T  driver - wnr311t_setup_4_1.exe. Then I make a copy of netmw145.sys and rename it netme146.sys (as required in the 1st forum post) *

2) **cd .wine/dosdevices/c:/Program\ Files/NETGEAR/WN311T**

3)** sudo ndiswrapper -i NetMW14x.inf**

installing netmw14x ...

4) **sudo ndiswrapper -a 11ab:2a08 netmw14x**

WARNING: Driver 'netmw14x' will be used for '11AB:2A08'
This is safe _only_ if driver netmw14x is meant for chip in device 11AB:2A08

5) **sudo ndiswrapper -l**

netmw14x : driver installed
	device (11AB:2A08) present

6) **sudo depmod -a**

*-- No output*

7) **sudo modprobe ndiswrapper**

*-- No output, but still no wifi. So, I checked the network logs.*

8) **sudo lshw -C Network**

  *-network UNCLAIMED     
       description: Ethernet 
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 04
       width: 32 bits
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  
*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e8:41:5b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
   
*-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:7b:eb:98:4e:9c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

*-- I see that the my device is unclaimed, so I check the logs for the wlan drivers.*

9) **dmesg | grep -e ndis -e wlan**

[ 2767.030327] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 2767.052613] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 2767.052629] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netmw14x'
[ 2767.055758] ndiswrapper (load_wrap_driver:108): couldn't load driver netmw14x; check system log for messages from 'loadndisdriver'

[I]--So then, upon reading the forums, I found that people who have x64 architecture have been using the WNR511T driver. I download, install and try to configure that. Same result.

--Last, I download and install the driver topdog-drv10049.exe, which others have been using successfully in Windows. This time, the process is successfully completed, but then I have NO internet AT ALL. Not even through my USB stick (which I am using now). It does not come back until I remove the associated driver.[/I]


[B]I think the best solution is to use the x32 drivers on my x64 architecture. It has been done before! Someone in the first link made it work - they didn't explain their methods though.

Can someone help me use the x32 WNR311T or WNR511T drivers on my x64 architecture? [/B]

---

### Post by ok123jump on 2009-04-24
Anyone?

---

### Post by ok123jump on 2009-04-26
I don't want to keep bumping this, but I need help!

---

### Post by ok123jump on 2009-04-26
How about simply running 32 bit drivers on a 64-bit OS?

---

### Post by ok123jump on 2009-04-30
Help with running a 32-bit driver on x64 architecture!

---

### Post by kiwisoup on 2009-07-19
I found 64-bit drivers for it, but haven't tried using them myself.

[http://support.gateway.com/support/drivers/getFile.asp?id=21850&dscr=Marvell%20Wireless%20LAN%20Driver](http://support.gateway.com/support/drivers/getFile.asp?id=21850&dscr=Marvell%20Wireless%20LAN%20Driver)

Let me know if you have any success.

---

### Post by spindzy on 2009-10-11
Found 64bit XP marvell drivers here.. [http://www.station-drivers.com/telechargement/marvell/marvell_top_1004-vista-xp.exe](http://www.station-drivers.com/telechargement/marvell/marvell_top_1004-vista-xp.exe)

says its valid for TOPDOG 802.11n/g/b Wireless (W8385-W8382).. they install fine thru ndiswrapper on ubuntu-studio amd64..  But im not getting a new device alias or any errors in dmesg.. I get this in dmesg:

```

[ 1900.682721] ndiswrapper version 1.53 loaded (smp=yes, preempt=rt)
[ 1900.748364] usbcore: registered new interface driver ndiswrapper

```

so... I'll update if I get it working.

---

### Post by ZazzyE on 2011-02-09
Similar problem.

The XP 64-bit TopDog driver doesn't exist.  That Gateway driver ports the Vista-64 bit driver back onto XP-64.  It's still an NDIS6 driver.  We need one that's NDIS5, or for Ndiswrapper to finally upgrade their support - that page of their wiki hasn't updated in over a year.

---

