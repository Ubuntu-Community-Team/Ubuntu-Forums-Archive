---
title: "Wireless intermittently stops."
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by Tom_T on 2009-09-20
Hi

ACER 1694 WMLI Laptop. Just reinstalled Ubuntu 9.04 and I find every 10 minutes or so my wireless just stops.

No disconnection but no Web browsing or pinging etc.

Other devices on my wireless network work fine, so I think it's just me.
Before I reinstalled Ubuntu it worked fine.

Any ideas ??  I run update manager and have updated..

uname -a
```
Linux default-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

```

LSPCI:

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)

```

Thanks

---

### Post by louigi600 on 2009-09-20
I had a very similar problem but with wired network.
I could see in dmes and messages that the link actually went up and down but the leds on the plugs were always lit.
I noticed that sometimes the speed negotiation went 10Mb/s and some other times 100Mb/s so I decided force it allways 10Mb/s .... and that stopped the intermittent link.

But in your case it's a wireless link ....
what do you see in you run iwconfig bothe when link is up and when link is down ?
Do you see any errors in /var/log/messages ?or if you examine the kernel ring buffer ?

---

### Post by Tom_T on 2009-09-20
Hi

No change in iwconfig or /var/log/messages when the wireless stops.

How do I check the kernel ring buffer ??

Connection looks fine, just no traffic !!

Any other ideas ?
Thanks :)

---

### Post by louigi600 on 2009-09-21
Issue the command "dmesg" to look at the kernel ring buffer.
Can you thenalso show me the output of "sudo iwconfig" after you get associated ?
Can you also show me the output of "sudo ifconfig -a" after the wireless link is up ?

---

### Post by Tom_T on 2009-09-21
Thanks Results below:


I've blanked out the ESSID, MAC Address and Encryption Key.
sudo iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"MYSSID"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:XX:XX:XX:XX:XX   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:xxxxxxxxx   Security mode:open
          Power Management:off
          Link Quality=83/100  Signal level=-47 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```


sudo ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:XX:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:XX:XX:XX:XX:XX  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe3c:970b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12590 errors:1 dropped:1 overruns:0 frame:0
          TX packets:11562 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4130070 (4.1 MB)  TX bytes:1259881 (1.2 MB)
          Interrupt:17 Base address:0x6000 Memory:c8219000-c8219fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

pan0      Link encap:Ethernet  HWaddr 00:XX:XX:XX:XX:XX  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


dmesg | grep kernel
```
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.004000] Memory: 1016984k/1047040k available (4115k kernel code, 29244k reserved, 2199k data, 532k init, 141832k highmem)
[    0.004000] virtual kernel memory layout:
[    0.468001] Booting paravirtualized kernel on bare hardware
[    2.179775] Freeing unused kernel memory: 532k freed
[    2.179878] Write protecting the kernel text: 4116k
[    2.179914] Write protecting the kernel read-only data: 1528k

```

---

### Post by louigi600 on 2009-09-22
"dmesg |grep kernel" is useless
Ither do "dmesg |tail -40" 
or 
dmesg |grep -iE "<whatever the module is called>|eth1" 
and substitute <whatever the module is called> with iwlagn or whatever module is used for your wifi card.
And can you do this after the link has stopped working and come back up again ?

---

### Post by Tom_T on 2009-09-27
Hi
This is driving me mad !!

dmesg |tail -40
> [   13.600782] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   13.602499] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   13.603211] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.603799] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.604550] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   13.780768] lp: driver loaded but no devices found
[   13.834218] Adding 1172704k swap on /dev/sda6.  Priority:-1 extents:1 across:1172704k
[   14.062688] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   14.099827] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   14.362899] EXT3 FS on sda5, internal journal
[   15.339054] type=1505 audit(1254086238.652:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1980
[   15.387578] type=1505 audit(1254086238.700:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1984
[   15.387699] type=1505 audit(1254086238.700:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1984
[   15.387745] type=1505 audit(1254086238.700:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1984
[   15.387786] type=1505 audit(1254086238.700:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1984
[   15.539936] type=1505 audit(1254086238.852:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1989
[   15.540241] type=1505 audit(1254086238.856:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1989
[   15.564421] type=1505 audit(1254086238.880:9): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=1993
[   15.590487] type=1505 audit(1254086238.904:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1997
[   17.459858] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.459862] Bluetooth: BNEP filters: protocol multicast
[   17.467262] Bridge firewalling registered
[   18.722573] pci 0000:01:00.0: power state changed by ACPI to D0
[   18.722585] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.745401] [drm] Initialized drm 1.1.0 20060810
[   18.748939] pci 0000:01:00.0: setting latency timer to 64
[   18.749092] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   19.626315] ppdev: user-space parallel port driver
[   19.832075] [drm] Setting GART location based on new memory map
[   19.833684] [drm] Loading R400 Microcode
[   19.833727] [drm] Num pipes: 2
[   19.833733] [drm] writeback test succeeded in 1 usecs
[   22.960758] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.656820] synaptics: using relaxed packet validation
[   27.862928] ieee80211_crypt: registered algorithm 'TKIP'
[   33.392042] eth1: no IPv6 routers present
[ 1098.204046] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 4579.322181] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 4579.322185] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 4579.322188] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.


Does this help ??
Thanks :)

---

