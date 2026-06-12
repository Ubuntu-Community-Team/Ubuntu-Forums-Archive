---
title: "No wireless on BCM4313 after upgrade to Oneiric (11.10)"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by kwaanens on 2011-10-14
PROBLEM SOLVED.

According to [http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt) I needed to blacklist the bcma driver.
To do this, put in "blacklist bcma" (without the quotes) on a new line in /etc/modprobe.d/blacklist.conf
Easiest way: Do this in terminal: 
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Reboot, and you're done.
Thanks to user ezramorris for the solution. I did not try praseodyms tip as ezramorris' solution worked.


-----------------------

Laptop: Samsung x125. Broadcom 4313 wireless card.

lspci
```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Samsung Electronics Co Ltd Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

```

lsusb:
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2232:1001  
Bus 004 Device 002: ID 0a5c:219c Broadcom Corp. 
```

lspci -nn | grep Broadcom
```
$ lspci -nn | grep Broadcom
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

ifconfig:
```
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:54:fe:14:80  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:54ff:fefe:1480/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2547715 (2.5 MB)  TX bytes:579287 (579.2 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5059 (5.0 KB)  TX bytes:5059 (5.0 KB)
```

iwconfig:
```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.
```

iwconfig wlan0:
```
$ iwconfig wlan0
wlan0     No such device

```

lsmod:
```
$ lsmod
Module                  Size  Used by
wl                   2646601  0 
lib80211               14570  1 wl
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
rfcomm                 38408  8 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
uvcvideo               67271  0 
samsung_laptop         13287  0 
videodev               85626  1 uvcvideo
snd_hda_codec_realtek   254125  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  18160  1 
psmouse                73673  0 
bluetooth             148839  23 bnep,rfcomm,btusb
serio_raw              12990  0 
sp5100_tco             13495  0 
snd_timer              28932  2 snd_seq,snd_pcm
k10temp                12990  0 
fglrx                2595570  36 
i2c_piix4              13093  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_rawmidi,snd_hda_codec_realtek,snd_hda_intel,snd_seq,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer,snd_seq_device
bcma                   19571  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
video                  18908  0 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 
ahci                   21634  2 
libahci                25727  1 ahci

```

dmesg | grep bcma
```
$ dmesg | grep bcma
[   18.498099] bcma-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.498116] bcma-pci-bridge 0000:02:00.0: setting latency timer to 64
[   18.498183] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   18.498208] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   18.498257] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   18.574458] bcma: Bus registered

```

sudo lshw -C network
```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:16 memory:d0200000-d0203fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:fe:14:80
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.192 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:d0300000-d0303fff ioport:a000(size=256)
```

iwlist scan:
```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

sudo /etc/init.d/networking restart
```
$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```



Upgraded via the default tools from 11.04. 32 bit.
On installing Natty I blacklisted acer_wmi, but that does not work on 11.10. (It does not matter if it's blacklisted or not.)

Jockey reports the STA driver active and currently in use. 

I have no wireless connections showing in network-manager.

Have a bunch of times tried to reinstall the bcmwl-kernel-source. Also tried purging it completely, then reinstalling, restarting between tries.

Hoping for some help, this is getting pretty annoying.

Thanks!

---

### Post by praseodym on 2011-10-14
Please show:

```
rfkill list
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by ezramorris on 2011-10-14
Hi,
A [note on the Broadcom website](http://www.broadcom.com/docs/linux_sta/bcma.txt) recommends removing/blacklisting the bcma driver.

I had a similar issue to this, but was using B43, not STA.

Hope this helps,
Ezra.

---

### Post by kwaanens on 2011-10-14
> **praseodym said:**
> Please show:

```
rfkill list
cat /etc/udev/rules.d/70-persistent-net.rules
```

```
$ rfkill list
1: samsung-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
```

```
$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:54:fe:14:80", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcm80211)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="4c:ed:de:73:87:ed", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="4c:ed:de:73:87:ed", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

---

### Post by praseodym on 2011-10-14
Blacklist this module:

```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

and reboot

---

### Post by kwaanens on 2011-10-14
> **ezramorris said:**
> Hi,
A [note on the Broadcom website](http://www.broadcom.com/docs/linux_sta/bcma.txt) recommends removing/blacklisting the bcma driver.

I had a similar issue to this, but was using B43, not STA.

Hope this helps,
Ezra.

THANK*you! That's all it took.
I'll update the original post to reflect that.

---

### Post by collisionystm on 2011-10-14
I did a clean install of 11.10 with the BCM4313. Everything worked out of the box... except my graphics

---

### Post by RiskyShift on 2011-10-15
Disregard... Going to create a new topic since this is marked resolved.

---

### Post by jebblue on 2011-10-22
Thanks, nice work, it worked here too.

---

### Post by codecks on 2012-05-18
Blacklisting bcma as mentionned in the first post worked for me, thanks!

---

