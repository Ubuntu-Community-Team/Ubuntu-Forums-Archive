---
title: "D-Link DWL Air 650 problem"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by moose3 on 2009-01-24
New Ubuntu user, trying to install 8.04 LTS on an IBM Thinkpad T21 for a techno-illiterate aunt.  

Problem is with the pcmcia card listed in the title.  On Ubuntu boot, there is no wireless activity, the LED just blinks, and no wlan is configured.  When the card is re-plugged it is recognized and the card works.

There appears a problem with the initial driver loading or the assigning of irq 3 to the card.

I am looking for help on getting the card to be loaded properly on boot so it does not have to be re-plugged to work. If all else fails, instructions on a permanent assignment of irq 4 for the card on boot if a real solution is not available, as that might work (if all else fails: use brute force) 

Below is the info from several command line commands as noted in other similar problem posts (lshw -C network, lspcmcia -vvv, and dmesg) for information that will hopefully lead to a solution.  Command results are displayed from first boot, and changes when the card is re-plugged)

---sudo lshw -C network
(***boot)
*-network               
       description: Link DWL-650 11Mbps WLAN Card
       product: Version 01.02
       vendor: D
       physical id: 0
       slot: Socket 0
(***re-plug) same with this after slot info
       resources: irq:4

---lspcmcia -vvv
(***boot)
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:02.0)
	Configuration:	state: on	ready: unknown
			Voltage: 3.3V Vcc: 3.3V Vpp: 0.0V
--none--
--none--
Socket 0 Device 0:	[-- no driver --]	(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   D Link DWL-650 11Mbps WLAN Card Version 01.02 
	Identification:	manf_id: 0x0156	card_id: 0x0002
			function: 6 (network)
			prod_id(1): "D" (0x71b18589)
			prod_id(2): "Link DWL-650 11Mbps WLAN Card" (0xb6f1b0ab)
			prod_id(3): "Version 01.02" (0x4b74baa0)
			prod_id(4): --- (---)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:02.1)
	Configuration:	state: on	ready: unknown
--none--
--none--

(***re-plug) same except for this line:
Socket 0 Device 0:	[hostap_cs]		(bus ID: 0.0)

--dmesg
(***boot)
[    0.000000] Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:44:42 UTC 2008 (Ubuntu 2.6.24-23.46-generic)
[   47.841421] pcmcia: registering new device pcmcia0.0
[   49.174074] ieee80211_crypt: registered algorithm 'NULL'
[   49.249966] hostap_cs: setting Vcc=33 (constant)
[   49.249991] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[   49.249999] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[   49.250006] io->flags = 0x0046, io.base=0x0000, len=64
[   49.250898] hostap_cs: Registered netdevice wifi0
[   49.290773] hostap_cs: index 0x01: , irq 3, io 0x0100-0x013f
[   49.486778] prism2_hw_init: initialized in 196 ms
[   49.495662] wifi0: hfa384x_cmd: entry still in list? (entry=cf940940, type=0, res=0)
[   49.495678] wifi0: hfa384x_cmd: command was not completed (res=0, entry=cf940940, type=0, cmd=0x0021, param0=0xfd0b, EVSTAT=8010 INTEN=0010)
[   49.495688] wifi0: interrupt delivery does not seem to work
[   49.495696] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fd0b, len=8)
[   49.495703] Could not get RID for component NIC
[   49.495711] hostap_cs: Initialization failed
[   49.495716] prism2_config() failed
[   49.495746] hostap_cs: probe of 0.0 failed with error 1
[   49.572269] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   49.582086] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   49.582371] Trying to free already-free IRQ 3
[   49.582401] orinoco_cs: GetNextTuple(): No matching CIS configuration.  Maybe you need the ignore_cis_vcc=1 parameter.
[   49.582409] 0.0: GetFirstTuple: No more items
[   49.582609] orinoco_cs: GetNextTuple(): No matching CIS configuration.  Maybe you need the ignore_cis_vcc=1 parameter.
[   49.582619] 0.0: GetFirstTuple: No more items

[  354.488324] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.488339] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.488348] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.488356] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.488364] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fdc6, len=12)
[  354.502899] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.502919] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.502927] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.502935] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.502943] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fdc1, len=2)
[  354.512515] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.512526] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.512534] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.512541] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.512548] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fd41, len=34)
[  354.530373] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.530390] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.530399] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.530406] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.530414] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fdc6, len=12)
[  354.550218] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.550234] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.550243] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.550250] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.550258] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fd42, len=6)
[  354.566010] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.566031] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.566040] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.566048] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.566057] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fc84, len=2)
[  354.594729] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.594747] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.594756] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.594763] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.594771] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fc09, len=2)
[  354.618120] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.618139] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.618148] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.618156] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.618163] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fc0e, len=34)
[  354.628296] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.628309] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.628317] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.628324] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.628331] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fc06, len=2)
[  354.647157] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.647174] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.647183] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.647191] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.647199] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fd48, len=2)
[  354.659348] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.659364] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.659372] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.659380] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.659388] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fc83, len=2)
[  354.669392] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  354.669404] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  354.669412] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  354.669419] wifi0: hfa384x_cmd: interrupted; err=-110
[  354.669426] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fc82, len=2)
[  384.869748] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  384.869768] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  384.869777] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[  385.392680] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  385.392701] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[  385.392711] wifi0: hfa384x_cmd: entry still in list? (entry=cfdad400, type=0, res=-1)
[  385.392718] wifi0: hfa384x_cmd: interrupted; err=-110
[  385.392726] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fdc6, len=12)

(***re-plug)
[  474.761406] pccard: card ejected from slot 0
[  476.073747] pccard: PCMCIA card inserted into slot 0
[  476.074010] pcmcia: registering new device pcmcia0.0
[  476.074293] hostap_cs: setting Vcc=33 (constant)
[  476.074344] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[  476.074352] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[  476.074358] io->flags = 0x0046, io.base=0x0000, len=64
[  476.076404] hostap_cs: Registered netdevice wifi1
[  476.116198] hostap_cs: index 0x01: , irq 4, io 0x0180-0x01bf
[  476.312215] prism2_hw_init: initialized in 196 ms
[  476.313663] wifi1: NIC: id=0x800c v1.0.0
[  476.314136] wifi1: PRI: id=0x15 v1.0.7
[  476.314577] wifi1: STA: id=0x1f v1.3.5
[  476.315840] wifi1: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS
[  476.321732] wifi1: registered netdevice wlan0
[  477.379461] ADDRCONF(NETDEV_UP): wifi1: link is not ready
[  477.379726] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  477.495169] wifi1: LinkStatus=2 (Disconnected)
[  477.495757] wifi1: LinkStatus: BSSID=44:44:44:44:44:44
[  477.968742] wifi1: LinkStatus=1 (Connected)
[  477.969334] wifi1: LinkStatus: BSSID=00:0c:41:4f:b4:08
[  477.969680] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  477.970017] ADDRCONF(NETDEV_CHANGE): wifi1: link becomes ready
[  478.619443] wlan0: no IPv6 routers present
[  479.360445] NET: Registered protocol family 17
[  479.392667] wifi1: CMD=0x0121 => res=0x7f, resp0=0x0004
[  479.392685] wifi1: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
[  479.394918] wifi1: LinkStatus=2 (Disconnected)
[  479.395367] wifi1: LinkStatus: BSSID=00:0c:41:4f:b4:08
[  479.407868] wifi1: LinkStatus=2 (Disconnected)
[  479.413869] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[  479.413939] wifi1: LinkStatus: BSSID=44:44:44:44:44:44
[  479.425413] wifi1: LinkStatus=1 (Connected)
[  479.425686] wifi1: LinkStatus: BSSID=00:0c:41:4f:b4:08
[  483.212738] wlan0: no IPv6 routers present
[  580.069626] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  580.069645] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  580.069654] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.

Looks like there will be pcmica problems in the near future, so I'll have to look into that too....fun.

Thanks for any help and thanks to those who are still reading.

---

### Post by nixscripter on 2009-01-24
Interrupt problems are generally caused when one device wants to share an interrupt and another doesn't.

First, add "irqpoll" to your boot options and see if it still happens. It shouldn't. This is just to check to make sure I'm right about an interrupt problem.

If I am right, look through the entire dmesg output to find another thing being assigned to IRQ 3. Serial ports and PCI cards come to mind. If I'm wrong, then we can move on to looking at the driver.

By the way, that last thing about deprecated usage is the problem with the **lshw** command, not the card (it was using an old kernel interface to collect the information). I assume its creators will fix that in time to avoid that "breakage".

---

### Post by moose3 on 2009-01-24
Added irqpoll to the end of the kernel boot line - no change, dmsg has this added 
[    0.000000] Kernel command line: root=UUID=a8ffb49f-1169-449c-97e2-13be9ceb377c ro quiet splash irqpoll

[    0.000000] Misrouted IRQ fixup and polling support enabled


Added irqpoll to the end of the intrid line on the next restart, nothing changed, and adding it to the fourth line with "quiet" caused a system reboot.

Instances after a search for irq in the result from dmesg:

[   55.156577] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)

[   55.157219] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)

[   55.157853] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)

[   55.158486] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   55.278827] PCI: Using ACPI for IRQ routing
[   96.261429] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[  101.958242] hostap_cs: index 0x01: , irq 3, io 0x0100-0x013f
[  102.270555] Trying to free already-free IRQ 3  <--(in between listings related to orinoco_cs: seen after trying to initialize the card in my previously posted dmesg segment, above it's at [49.582371])

Thanks so far.

---

### Post by nixscripter on 2009-01-25
First of all, this appears to be a bug in the driver without resolution: [http://hostap.epitest.fi/bugz/show_bug.cgi?id=121](http://hostap.epitest.fi/bugz/show_bug.cgi?id=121) 

So now I'm trying to figure a workaround.

If "irqpoll" doesn't work, the next step is to try and find a way to reset the driver. Is **hostap_cs** the name of the driver? Replug the card to make it work, and then look for it in your **lshw -C network**; there should be a "driver=" part.

Once you find that, try: ```
modprobe -r **driver-name** && modprobe **driver-name**
``` and see what dmesg says.

---

### Post by moose3 on 2009-01-25
This was at the end of lshw -C network (top part already displayed above, and ethernet info in the middle not needed)

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:05:5d:da:d3:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap firmware=1.3.5 ip=192.168.1.105 multicast=yes wireless=IEEE 802.11b


Then tried 'modprobe -r hostap && modprobe hostap' which gives: 
FATAL: Module hostap is in use.

same with modprobe -r hostap by itself, and modprobe hostap just brings up another command line (in case those were meant to be run separately) also with hostap_cs used instead of hostap, just to check, and the same results apply.

dmesg remains the same, no further entries from those listed after the card is ejected and re-plugged, based on what I assume is some sort of timestamp with the numbers in brackets.

From that post you referenced, and what is listed from my dmesg, it does seem to be very similar, both cards seem to use prism2 and a re-insert for him seemed to set things right, though it appears his stayed on irq 3 whereas my setup is re-directed to irq 4.

---

### Post by nixscripter on 2009-01-25
Yes, modprobe loading a module already in does nothing.

Dang, I was hoping it was smarter than "in use".

I'm afraid that exhausts everything obvious. I see you should try that IRQ 4 hardcoding suggestion, though I suspect (given the irqpoll test) it won't work either.

---

### Post by moose3 on 2009-01-26
I'll try and look into how to set Ubuntu to initially assign irq 4 to the wireless card tomorrow while at work, unless someone happens to know off hand how to do that (I'm new to linux in general).  I appreciate your time and effort in this endeavor.

I am guessing it involves finding the proper conf file and editing it, seeing as how that was the suggestion in trying to get this t21 to work with xubuntu by modifying the xorg.conf file.  

Unfortunately that didn't work too well hence I'm working with ubuntu now, and hopefully I'll have more luck this time around, though you seem doubtful.

---

### Post by moose3 on 2009-01-26
Long story short for others with this problem, see if any of your devices through dmesg are set with the same IRQ and then check if they are disabled in the BIOS, if so, enable them, and hope ubuntu sorts things out. 

More detailed story:

One problem down, bigger can of worms opened up...

In trying to solve the IRQ conflict, nsc_ircc_pnp_probe(): from dmesg caught my eye, and I searched on this, seems this is related to the infrared com port on the laptop.  To my surprise, it was disabled in the BIOS, but for some reason Ubuntu thinks it working and tries to enable it:

[   44.641682] irda_init()
[   44.641732] NET: Registered protocol family 23
[   44.709462] nsc-ircc 00:0e: activated
[   44.709479] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   44.709506] nsc-ircc, chip->init
[   44.709513] nsc-ircc, Found chip at base=0x02e
[   44.709605] nsc-ircc, driver loaded (Dag Brattli)
[   44.710510] IrDA: Registered device irda0
[   44.710518] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500

So I enabled it and set it to irq4 in BIOS and this caused the system to lock up with a kernel panic msg about IRQ's not syncing up.  I'll see about trying to backup my syslogs and try and capture the crash if I find a "kernel crash test dummy" section in the forum... 

Enabling the device and then setting it to IRQ3 however allowed Ubuntu to load, however the IR was set to DMA3 (default) in the BIOS, and Ubuntu wanted it in DMA1, so it was disabled

[   44.322114] nsc-ircc, chip->init
[   44.322121] nsc-ircc, Found chip at base=0x02e
[   44.322153] nsc-ircc, driver loaded (Dag Brattli)
[   44.322169] nsc_ircc_open(), can't get iobase of 0x2f8
[   44.322195] nsc-ircc, Found chip at base=0x02e
[   44.322226] nsc-ircc, driver loaded (Dag Brattli)
[   44.322232] nsc_ircc_open(), can't get iobase of 0x2f8
[   44.322639] nsc-ircc 00:0e: disabled

Which is fine by me because now the wireless card is working because the IR device is now seen as disabled by the OS, and the IRQ conflict is no more with the device disabled in software instead of being a phantom that didn't feel like sharing the IRQ.  

My guess, since it was supposedly enabled in software, but disabled in hardware, the software tried to see which was active to allow resource sharing, but with the device not really present, it could not get a response.  Luckilly it didn't crash the system, just made a wireless connection impossible.  On a re-insertion of the card, Ubuntu decides to try a different IRQ, causing the wireless card to function.

Since this is now going off-topic in regards to wireless, I put a new post in the general help section trying to get pointed in where to go next to submit what I have found: [http://ubuntuforums.org/showthread.php?t=1051557](http://ubuntuforums.org/showthread.php?t=1051557)

---

### Post by munooka on 2009-01-30
Did you try blacklisting hostap?

sudo nano /etc/modprobe.d/blacklist

then add the following lines:

#switch to orinoco driver
blacklist hostap
blacklist hostap_pci

Works for me and my X23.

---

### Post by nixscripter on 2009-01-31
I read something about the orinoco driver, but I wasn't sure if it would work for the OP's card.

In the face of this impass, however, I would suggest trying it.

---

### Post by moose3 on 2009-02-01
I decided to just leave the infrared port activated in BIOS, and then let Ubuntu disable the device itself for what ever reason.  This way only the wireless card is using IRQ 3, and works just fine on booting the system.

I was thinking about blacklisting the infrared device since that is the real problem apparently, but it is not causing a problem right now, so I figured I'd just leave well enough alone.

---

### Post by munooka on 2009-02-01
Seemingly there were three different chipsets supplied with the card. However [http://linuxwireless.org/en/users/Drivers/orinoco/devices](http://linuxwireless.org/en/users/Drivers/orinoco/devices) states that it should be OK. Worth a try as hostap is buggy for his card. You will also have to blacklist the hostap_cs as this is a usb card.

---

### Post by munooka on 2009-02-01
You may also want to report a bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.27](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.27)

---

### Post by munooka on 2009-02-02
Also you may want to check to see if the firmware is up-to-date.
[ftp://ftp.dlink.com/Wireless/DWL650/Firmware/](ftp://ftp.dlink.com/Wireless/DWL650/Firmware/)

---

