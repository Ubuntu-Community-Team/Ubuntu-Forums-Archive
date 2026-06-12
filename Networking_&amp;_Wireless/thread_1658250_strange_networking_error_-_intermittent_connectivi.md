---
title: "strange networking error - intermittent connectivity"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by andy-roo on 2011-01-02
I have a strange problem where my machine will suddenly stop responding to connections while still remaining partially connectible.  Here's an example 

sequence of events I have taken (numerous times).  If anyone can spot something else I should check or has seen these symptoms before please let me know.

1) System is using an Edimax 7318-usg, Ubuntu 10.04

2) Wifi connection is working, with power management turned off (iwconfig)

3) Signal strength does not cause the connection to drop (confirmed with router logs)

4) When in a ssh session on the problem machine suddenly the ssh session is dropped "host is down"

5) When I attempt to re-initiate ssh it fails, no route to host...

6) Pinging it fails, accessing a webpage hosted on it fails, all access fails

7) The machine I'm pinging/sshing from still has a good network connection

8 ) I check my routers DHCP leases, problem machine still has a valid lease

9) Router still shows problem machine in routing & arp table & shows active traffic going to and from (I checked the routers states and bandwidth monitor for this)

10) I try sshing and pinging the problem machine from the laptop on the local network, it still fails, no route to host, wtf?

11) I go to the problem machine _physically_, wifi connection is up with decent signal

12) ifconfig indicates it still holds an IP address

13) I open a browser on the problem machine, any webpage loads fine

14) I ping the laptop from the problem machine, ok

15) I ssh from the problem machine to my laptop, it works

16) At this point I ssh from the laptop to the problem machine, sometimes it works sometimes it fails
(it seems that pinging/sshing the laptop FROM the problem machine sometimes makes it connectable again)

17) Usually if I wait a while the problem machine will randomly become connectable again at random intervals

18 ) The only reliable way to make the problem machine connectable again is manually reconnecting it to the wireless network

19) I tailed auth.log ufw.log, etc. nothing suspicious disallowing my ssh connection

20) dmesg shows nothing unusual, as far as I can tell, just some activity negotiating WPA keys and such
By looking at the timestamp for the WPA negotiation and cross referencing the router bandwidth monitor I can tell the WPA negotiation doesn't make it drop the conection

So that's it, lol.  This problem has been ongoing for months and is not a unique occurance.  I'm finally fed up with it...

---

### Post by perspectoff on 2011-01-02
Are you using Network Manager?

If so, join the thousands of people with the same problem.

I had the same problem for months as well, then uninstalled Network Manager and installed Wicd instead (for wireless). I don't have the problems anymore.

---

### Post by andy-roo on 2011-01-03
Thanks,

I did use network manager and it worked fine for a while until the last few months.

Per your recommendation, network manager is now purged and I am now using wicd.  The exact same symptoms occur...  Any other ideas?

I am beginning to suspect general wireless issues / hardware issues with the Edimax adapter.  Next I'll be trying other adapters and ethernet to rule it out...

---

### Post by PatchesTheCaveman on 2011-01-03
Hi andy-roo!  Happy New Year!

Run these commands and copy/paste the output:
```
sudo iwconfig
lspci -vnn
```

---

### Post by andy-roo on 2011-01-04
Thanks!

Note, turning power management on/off for wlan0 made no improvement in symptoms when using either wicd or network manager.  Also, I filtered lscpi entries for video cards & etc to the bottom.  I tried to put the important ones on top that directly relate to my usb2 controller, the pci bus it's on and the ralink adapter connected to it.

--------------------------------------

"lsbusb"  --->  Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

--------------------------------------

"iwconfig" --->

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"yadayada"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00 (intentional)   
          Bit Rate=54 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

--------------------------------------

"lspci -vvm" --->

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: e8000000-efffffff
	Kernel modules: shpchp

04:0f.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43) (prog-if 10)
	Subsystem: NEC Corporation USB [1033:0035]
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fe9fe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

04:0f.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43) (prog-if 10)
	Subsystem: NEC Corporation USB [1033:0035]
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at fe9fd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

04:0f.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04) (prog-if 20)
	Subsystem: HaSoTec GmbH Device [0e55:2928]
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at fe9ff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

--------------------------------------
--------------------------------------

(extraneous lspci continued, maybe not related to Ralink USB wireless adapter)

00:00.0 Host bridge [0600]: Intel Corporation 82860 860 (Wombat) Chipset Host Bridge (MCH) [8086:2531] (rev 04)
	Subsystem: Dell Device [1028:00d8]
	Flags: bus master, fast devsel, latency 0
	Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: i82860_edac, intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge [8086:2532] (rev 04)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: f0000000-f7ffffff
	Kernel modules: shpchp

00:02.0 PCI bridge [0604]: Intel Corporation 82860 860 (Wombat) Chipset AGP Bridge [8086:2533] (rev 04)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa800000-fbffffff
	Prefetchable memory behind bridge: 40000000-400fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 04)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 04) (prog-if 80 [Master])
	Subsystem: Dell Device [1028:00d8]
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 04)
	Subsystem: Dell Device [1028:00d8]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 04)
	Subsystem: Dell Device [1028:00d8]
	Flags: medium devsel, IRQ 17
	I/O ports at ccd0 [size=16]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c-i801

00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 04)
	Subsystem: Dell Device [1028:00d8]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 04)
	Subsystem: Dell Device [1028:00d8]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at c800 [size=256]
	I/O ports at cc40 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV20 [GeForce3] [10de:0200] (rev a3)
	Subsystem: VISIONTEK Device [1545:001b]
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Memory at f3f80000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at f0000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidia-96, nvidiafb, rivafb, nouveau

02:1f.0 PCI bridge [0604]: Intel Corporation 82806AA PCI64 Hub PCI Bridge [8086:1360] (rev 03)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fb000000-fbffffff
	Prefetchable memory behind bridge: 40000000-400fffff
	Kernel modules: shpchp

03:00.0 PIC [0800]: Intel Corporation 82806AA PCI64 Hub Advanced Programmable Interrupt Controller [8086:1161] (rev 01) (prog-if 20)
	Subsystem: Intel Corporation 82806AA PCI64 Hub Advanced Programmable Interrupt Controller [8086:1161]
	Flags: fast devsel
	Memory at fbeff000 (32-bit, non-prefetchable) [disabled] [size=4K]

03:0c.0 RAID bus controller [0104]: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID [13c1:1001] (rev 01)
	Subsystem: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID [13c1:1001]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	I/O ports at ecf0 [size=16]
	Memory at fbefec00 (32-bit, non-prefetchable) [size=16]
	Memory at fb000000 (32-bit, non-prefetchable) [size=8M]
	Expansion ROM at fbf00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 3w-xxxx
	Kernel modules: 3w-xxxx

03:0e.0 SCSI storage controller [0100]: Adaptec AIC-7892P U160/m [9005:008f] (rev 02)
	Subsystem: Dell Device [1028:00d8]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	BIST result: 00
	I/O ports at e800 [disabled] [size=256]
	Memory at fbefd000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at 40000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: aic7xxx
	Kernel modules: aic7xxx

04:0b.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
	Subsystem: Dell Device [1028:00d8]
	Flags: bus master, medium devsel, latency 64, IRQ 23
	I/O ports at dc80 [size=128]
	Memory at fe9ffc00 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at fe900000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

04:0c.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) [104c:8020] (prog-if 10)
	Subsystem: Dell Device [1028:00d8]
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at fe9ff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fe9f8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

04:0d.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder [4444:0016] (rev 01)
	Subsystem: Hauppauge computer works Inc. Device [0070:37f1]
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at ec000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: ivtv
	Kernel modules: ivtv

04:0e.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder [4444:0016] (rev 01)
	Subsystem: Hauppauge computer works Inc. Device [0070:37f1]
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at e8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: ivtv
	Kernel modules: ivtv

---

### Post by PatchesTheCaveman on 2011-01-04
You probably need to compile and install the official drivers from Ralink:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

A lot of users find they work better than the ones included with the Linux kernel.

In order to do that, you will need the build-essential package and the headers for your version of the Linux kernel.  To install them, run this command:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

There is a README file that explains how to build and install them.  If you run into the trouble, some of the drivers require slight changes that can be found by searching this forum for the error.

As always, let us know if you run into trouble.  Good luck!

---

### Post by andy-roo on 2011-01-08
blank

---

