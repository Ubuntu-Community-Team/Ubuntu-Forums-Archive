---
title: "Updated ubuntu won't connect"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by tdrules on 2010-12-30
Hello all, 

I recently updated my ubuntu to the newest version 10.  I have a DSL router with a password.  When I try to connect to the net it will try to connect for about 5 or so min then say that I am disconnected.  I cannot remember what option I had before to connect but its not on this version.  

Please help need net on this pc :p

Thanks you guys :guitar:

---

### Post by anystupidname1 on 2010-12-30
I'd suggest you try these steps:

1 right click the network manager applet on your gnome panel and choose "edit connections"
2 on the wireless tab, pick the connection you're having a problem with and hit "edit"
3 on the wireless security tab, make sure the correct encryption is selected and retype the password.
4 apply that and close the windows
5 try to connect to your router again

---

### Post by PatchesTheCaveman on 2010-12-30
Hi tdrules!  I'm sorry you're having trouble keeping a wireless connection for longer than 5 minutes.

To try and figure out what's going on, I'm going to have you gather a little information.  To start, go to Applications > Accessories > Terminal in your top panel.  In the black box that appears, type the following command and press Enter:
```
lspci -v
```

Copy and paste what appears in a reply to this thread.  Then, type this in and press Enter:
```
sudo iwconfig
```
You will need to enter your password and press Enter when asked.  Then, copy and paste that into a post here too.

Finally, type this last one in and hit Enter:
```
uname -r
```

Copy and paste that, and you're done!  With all that we should be able to figure out what's going on.  Thank you!

---

### Post by tdrules on 2010-12-30
Here is what you requested

> brad@brad-laptop:~$ lspci -v
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
Flags: bus master, medium devsel, latency 0
Memory at f0000000 (32-bit, prefetchable) [size=64M]
Capabilities: <access denied>
Kernel driver in use: agpgart-ali
Kernel modules: ali-agp
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
Flags: bus master, slow devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
Memory behind bridge: f7f00000-fdffffff
Prefetchable memory behind bridge: 38000000-380fffff
Kernel modules: shpchp
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3) (prog-if e0)
Subsystem: Toshiba America Info Systems Device 0004
Flags: bus master, medium devsel, latency 64, IRQ 255
[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
I/O ports at eff0 [size=16]
Capabilities: <access denied>
Kernel driver in use: pata_ali
Kernel modules: pata_ali
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device 
(rev 01)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, medium devsel, latency 64, IRQ 11
I/O ports at 1000 [size=256]
Memory at 38100000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: ALI 5451
Kernel modules: snd-ali5451
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
Subsystem: Toshiba America Info Systems Device 0004
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>
Kernel modules: alim7101_wdt, alim1535_wdt
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
Subsystem: Toshiba America Info Systems Device 0001
Flags: medium devsel
Kernel driver in use: ali1535_smbus
Kernel modules: alim7101_wdt, i2c-ali15x3, i2c-ali1535
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, medium devsel, latency 64, IRQ 11
Memory at f7eff000 (32-bit, non-prefetchable) [size=4K]
I/O ports at eec0 [size=64]
Memory at f7ec0000 (32-bit, non-prefetchable) [size=128K]
Capabilities: <access denied>
Kernel driver in use: e100
Kernel modules: e100
00:0c.0 USB Controller: NEC Corporation USB (rev 41) (prog-if 10)
Subsystem: Toshiba America Info Systems Device 0003
Flags: bus master, medium devsel, latency 64, IRQ 11
Memory at f7ebf000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: ohci_hcd
00:0c.1 USB Controller: NEC Corporation USB (rev 41) (prog-if 10)
Subsystem: Toshiba America Info Systems Device 0003
Flags: bus master, medium devsel, latency 64, IRQ 11
Memory at 38101000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>
Kernel driver in use: ohci_hcd
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02) (prog-if 20)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, medium devsel, latency 64, IRQ 11
Memory at 38105200 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
Subsystem: Lucent Technologies Device ab01
Flags: bus master, medium devsel, latency 168, IRQ 11
Memory at 38102000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
Memory window 0: 20000000-23fff000 (prefetchable)
Memory window 1: 24000000-27fff000
I/O window 0: 00001400-000014ff
I/O window 1: 00001800-000018ff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV 
Support (rev 32)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, slow devsel, latency 168, IRQ 11
Memory at 38103000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=00, secondary=06, subordinate=09, sec-latency=0
Memory window 0: 28000000-2bfff000 (prefetchable)
Memory window 1: 2c000000-2ffff000
I/O window 0: 00001c00-00001cff
I/O window 1: 00002000-000020ff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV 
Support (rev 32)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, slow devsel, latency 168, IRQ 11
Memory at 38104000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=00, secondary=0a, subordinate=0d, sec-latency=0
Memory window 0: 30000000-33fff000 (prefetchable)
Memory window 1: 34000000-37fff000
I/O window 0: 00002400-000024ff
I/O window 1: 00002800-000028ff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
Subsystem: Toshiba America Info Systems Device 0001
Flags: medium devsel, IRQ 255
Memory at 38105000 (32-bit, non-prefetchable) [disabled] [size=512]
Capabilities: <access denied>
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
Subsystem: Toshiba America Info Systems Device 0010
Flags: bus master, 66MHz, medium devsel, latency 8, IRQ 11
Memory at fc000000 (32-bit, non-prefetchable) [size=32M]
Memory at fbc00000 (32-bit, non-prefetchable) [size=4M]
Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
Memory at f7ff8000 (32-bit, non-prefetchable) [size=32K]
[virtual] Expansion ROM at 38000000 [disabled] [size=64K]
Capabilities: <access denied>
Kernel modules: tridentfb
brad@brad-laptop:~$ sudo iwconfig
[sudo] password for brad: 
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11b  ESSID:"ZyXEL_CE1"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
brad@brad-laptop:~$ uname -r
2.6.32-27-generic
brad@brad-laptop:~$ 

---

### Post by PatchesTheCaveman on 2010-12-30
I didn't see your wireless card in there.  Is it a USB dongle?

If so, run:
```
sudo lshw -C network
```
and copy and paste.

If it is built in to your laptop, try running
```
lspci -v
```
again.  Maximize the window and scroll up to make sure you get everything.

---

