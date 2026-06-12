---
title: "Yet Another Confusing Dell n4010 Wireless Problem"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by Reamer on 2010-12-25
I have done quite a bit of searching on my own and finally got the wireless card working on my Dell Inspiron n4010 laptop... somewhat...

It will not connect to my, or any other access point right away on startup, or even after 10 minutes. During this time the output of dmesg is giving me the notorious "ADDRCONF(NETDEV_CHANGE): wlan0: link not ready" output. After a prolonged period of time it finally says that the link is ready and I can easily connect to my router. 

Any help to make this quicker and more reliable would be greatly appreciated. Also, the more you can tell me to do it in the command line, the more grateful I would be. I just would prefer that so I can more easily configure it in the future from one debian distribution to the next without learning new GUI programs or having to install any that may not be present on the system such as WICD. 

I am trying to switch from Windows to Linux as much as possible (except the damned copyrights Microsoft has on Silverlight for Netflix) so I am pretty new to everything but with minimal experience to be able to navigate from one thing to another. I don't need the guidance of an infant, but probably a smart 5 year old.

Thank you for your help in advance.

---

### Post by relay_man on 2010-12-26
If you can get the connection made again, could you post the output of:

"dmesg|grep eth0" (no quotes)


and:

"ifconfig"

---

### Post by Reamer on 2010-12-30
Sorry about taking so long to reply, didn't have much free time during the holidays and I'm having to even do this a little rushed now. Anyways, here are the outputs you asked for, though eth0 shows up blank when I type that output, so I switched it with wlan0 and here's what I got.

dmesg | grep wlan0
```
[   18.425000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2405.735045] wlan0: direct probe to AP 00:23:69:5c:c6:0f (try 1)
[ 2405.735073] wlan0: deauthenticating from 00:23:69:5c:c6:0f by local choice (reason=3)
[ 2405.735169] wlan0: direct probe to AP 00:23:69:5c:c6:0f (try 1)
[ 2405.737840] wlan0: direct probe responded
[ 2405.737846] wlan0: authenticate with AP 00:23:69:5c:c6:0f (try 1)
[ 2405.744144] wlan0: authenticated
[ 2405.744182] wlan0: associate with AP 00:23:69:5c:c6:0f (try 1)
[ 2405.746644] wlan0: RX AssocResp from 00:23:69:5c:c6:0f (capab=0x411 status=0 aid=1)
[ 2405.746648] wlan0: associated
[ 2405.748875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2416.640800] wlan0: no IPv6 routers present
```

ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9904 (9.9 KB)  TX bytes:9904 (9.9 KB)

pan0      Link encap:Ethernet  HWaddr 46:76:ff:3f:f9:59  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:15:1b:cc:ac  
          inet addr:192.168.2.13  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:15ff:fe1b:ccac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2656949 (2.6 MB)  TX bytes:246919 (246.9 KB)

```


EDIT: I just read kevdog's instructions on setting up your connection in the terminal so I'll probably work on that either tomorrow night or on Saturday to see how it goes. Maybe that's more like what I'm looking for and will hopefully end this issue.

---

### Post by Reamer on 2010-12-31
Ok, I knew there was problems with a hidden network, but I didn't think it would be that bad if you was specifically telling it to connect to that SSID. Apparently as soon as I made my network visible my laptop connects with no problem at all on startup. A little aggravating since I don't want to broadcast like this. Any idea's?

---

### Post by PatchesTheCaveman on 2010-12-31
Disabling SSID broadcasting provides little security.  It's relatively easy to figure it out even when its hidden:
[http://www.wi-fiplanet.com/tutorials/article.php/3576541/Your-SSID-Isnt-Hidden-Forever.htm](http://www.wi-fiplanet.com/tutorials/article.php/3576541/Your-SSID-Isnt-Hidden-Forever.htm)

---

### Post by Reamer on 2010-12-31
I know it isn't a security measure that just prevents anyone from getting on my network, but it greatly reduces the amount of people that don't know what they're doing trying to get on. Which is also why I use WPA and changed the default DHCP addressing from the 192.168.1.100 to my own. I just would prefer to have every security measure I can without getting insane with the highest government encryption possible. Just a personal preference.

---

### Post by relay_man on 2010-12-31
Solved?

---

### Post by Reamer on 2011-01-01
Nope. Got on today and still took an hour for the wireless card to finally start up. In the meantime I jumped on my Ubuntu Netbook to look up those instructions to set it up manually and that didn't change anything. I had pretty low expectations of that since I had a problem with the wireless card starting and not just connecting to my network. But even though it won't connect to a network, it still actively scans and shows them in the GUI, but more often times then not in the terminal it will say "no scan results".

---

### Post by PatchesTheCaveman on 2011-01-01
Hi Reamer!  Happy New Year!

Please run ```
lspci -v
``` and copy/paste the output here.

---

### Post by Reamer on 2011-01-03
Here you go, and Happy New Year to you to! Though mine was a little late.
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0806800 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20)
	Subsystem: Dell Device 0456
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f0807000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0000000-c01fffff
	Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0500000-f05fffff
	Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000c0600000-00000000c07fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20)
	Subsystem: Dell Device 0456
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0807400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Dell Device 0456
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) (prog-if 01)
	Subsystem: Dell Device 0456
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 31
	I/O ports at 1840 [size=8]
	I/O ports at 1814 [size=4]
	I/O ports at 1818 [size=8]
	I/O ports at 1810 [size=4]
	I/O ports at 1820 [size=32]
	Memory at f0806000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Dell Device 0456
	Flags: medium devsel, IRQ 10
	Memory at f0807800 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1860 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: Dell Device 0456
	Flags: fast devsel, IRQ 10
	Memory at f0605000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 57)
	Subsystem: Intel Corporation Device 1321
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Memory at f0500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

```

---

### Post by PatchesTheCaveman on 2011-01-03
Based on your description of the problem, it sounds like the RF kill switch is activated.

Connect to a wired Ethernet connection, and run the following command to install the 'rfkill' package:
```
sudo apt-get install rfkill
```

After that, run it:
```
sudo rfkill list
```

Is your wireless hard or soft-blocked?

If it's hard-blocked, you need to flip your wireless switch.  It might be a physical switch, a discrete button, or a Fn key combination.

If it's soft-blocked, run ```
sudo rfkill unblock 0
``` to unblock it.

If you continue to have trouble, copy/paste the output of *sudo rfkill list* into a reply to this thread.

---

### Post by Reamer on 2011-01-03
It's actually been running pretty good lately. I am connected to my wireless right now and rfkill shows all of them unblocked, which would make sense. Thank you for all the help. I'm not going to mark it solved just yet because as soon as I do then it's going to screw up. If it goes the next few days without any problems then I'll mark it solved. Otherwise I'll post my results of ```
 sudo rfkill list 
``` and go from there. Again, thanks for all the help so far.

---

### Post by Reamer on 2011-01-05
Ok, just as I knew that it would. As soon as I marked it solved, it failed on me again. I had been through I don't know how many restarts I've been through and the wireless would connect flawlessly. I was on the internet just a little while ago and done a restart, came back on and would not connect. the command "sudo rfkill list" also showed that none of them was blocked in any way. What's the next set of output commands y'all would like to see? Haha...

EDIT: oh god... I posted that in Windows, rebooted into Ubuntu and now I'm making my edit with that. I don't what to say...

---

