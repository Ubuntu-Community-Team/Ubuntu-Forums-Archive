---
title: "No network interfaces (neither ethernet, nor wireless) detected"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by lowjoe55 on 2010-03-02
Hey!
I'm pretty new to Ubuntu, so I'm sorry if i cant give you all the information you need in the first place, but I'll do my best.

Problem:
I got a new Acer Aspire 8935G notebook, installed Ubuntu 9.10 on it and everything is fine, except the fact, that it wont detect any network interfaces (or how to call it ??)
So there are no ethernet or wlan connections available in the network-manager..

lspci gives me following lines:
joe@IGNAZ ~ $ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 9488
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
02:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
02:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)  
  // for that one i found a driver tg3 and installed it
09:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
  // for that one i found a driver iwlagn and installed it

i hope the drivers i installed werent complete bullsh**.. but thats what i found at several researches..


lshw gives me the following (after installing drivers):
joe@IGNAZ ~ $ sudo lshw -C network
[sudo] password for joe: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ba000000-ba00ffff
  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ba100000-ba101fff


ifconfig:
joe@IGNAZ ~ $ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

pan0      Link encap:Ethernet  HWaddr 26:7d:c7:c6:60:b0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig:
joe@IGNAZ ~ $ iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.


another intresting output (because my first believe was, that there is no link between network device and driver) i got for lspci -k:
joe@IGNAZ ~ $ lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Kernel driver in use: i915
	Kernel modules: i915
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc Device 9488
	Kernel modules: radeon
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
02:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
02:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
  // following lines look quite correct for me
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
	Kernel modules: tg3
09:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Kernel modules: iwlagn


i really hope you can help me!
thanks!

---

### Post by lowjoe55 on 2010-03-03
up

i really need help here..

---

### Post by lowjoe55 on 2010-03-03
up

---

### Post by Iowan on 2010-03-03
I'll hazard a guess that there might be a driver problem - since none is listed for either interface. I (or you) can search for other threads about BCM5784M or Intel 5100.

---

### Post by lowjoe55 on 2010-03-03
Thanks for the reply..

The problem is, as I'm not an expert on how the network stuff works on linux I don't really know what to look for..

Of course there are a lot of similar problems, and I tried out everyzthing i found.. 
But there was always some little difference..

But if you say "driver problem" what would be the typical way to solve such a problem?

Any other suggestions?

---

### Post by spiky001 on 2010-03-03
I found this it looks like what you have to do to install drivers bcm43xx-fwcutter

ttp://ubuntuforums.org/showpost.php?p=6028741&postcount=4

let me know how you get on

---

### Post by lowjoe55 on 2010-03-04
Thanks for the reply!
Even if it changed sth. in the ifconfig (see below) i still can't find a network connection or any possibility to establish one..
When installing the package i had an error message which is (as I'm runnning a german system) in german.. Don't know if you can get sth. out of this, but I'll post it here too..

Any other recommendations?

joe@IGNAZ /media/Acer/Users/Joe/Downloads $ sudo dpkg -i b43-fwcutter_011-4ubuntu1_i386.deb 
[sudo] password for joe: 
(Lese Datenbank ... 116416 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von b43-fwcutter 1:011-4ubuntu1 (durch b43-fwcutter_011-4ubuntu1_i386.deb) ...
Entpacke Ersatz fÃ¼r b43-fwcutter ...
Richte b43-fwcutter ein (1:011-4ubuntu1) ...
--2010-03-04 14:54:25--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: Fehler beim Bearbeiten von b43-fwcutter (--install):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurÃ¼ck
Verarbeite Trigger fÃ¼r man-db ...
Fehler traten auf beim Bearbeiten von:
 b43-fwcutter


joe@IGNAZ ~ $ sudo lshw -C network
[sudo] password for joe: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ba000000-ba00ffff
  *-network
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: driver=iwlagn latency=0
       resources: irq:17 memory:ba100000-ba101fff

---

### Post by satty8610 on 2010-03-04
Maybe the network interface is there , but hasnt been brought up.Try: 

```
sudo ifup eth0
```

If problem still persists, give here the contents of the file: /etc/network/interfaces

---

### Post by lowjoe55 on 2010-03-04
joe@IGNAZ ~ $ sudo ifup eth0
[sudo] password for joe: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

contents of /etc/network/interfaces:

auto lo
iface lo inet loopback

//following is what I inserted due to an recommendation of another thread..
auto eth0
iface eth0 inet dhcp

still, no wireless and no ethernet connection..

---

### Post by chili555 on 2010-03-04
b43-fwcutter is not appropriate for your wireless device. It installs firmware for Broadcom wireless cards. > 06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
// for that one i found a driver tg3 and installed it
09:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
// for that one i found a driver iwlagn and installed itThose are correct. Let's try to load them and see what happens:```
sudo modprobe tg3
sudo modprobe iwlagn
dmesg | grep -e iwl -e tg3
ifconfig
```Thanks.

---

### Post by lowjoe55 on 2010-03-04
joe@IGNAZ ~ $ sudo modprobe tg3
[sudo] password for joe: 
joe@IGNAZ ~ $ sudo modprobe iwlagn
joe@IGNAZ ~ $ dmesg | grep -e iwl -e tg3
[    3.806750] tg3.c:v3.99 (April 20, 2009)
[    3.806936] tg3 0000:06:00.0: enabling device (0000 -> 0002)
[    3.806943] tg3 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.806957] tg3 0000:06:00.0: setting latency timer to 64
[    3.813213] tg3 0000:06:00.0: PME# disabled
[    3.981172] tg3: eth%d: Cannot get nvarm lock, tg3_nvram_init failed.
[    4.082618] tg3: (0000:06:00.0) phy probe failed, err -19
[    4.403066] tg3: Problem fetching invariants of chip, aborting.
[    4.403256] tg3 0000:06:00.0: PCI INT A disabled
[    9.801017] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    9.801021] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.801120] iwlagn 0000:09:00.0: enabling device (0000 -> 0002)
[    9.801148] iwlagn 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.801195] iwlagn 0000:09:00.0: setting latency timer to 64
[    9.801241] iwlagn 0000:09:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x7B6A8F56
[    9.954136] iwlagn 0000:09:00.0: Failed, HW not ready
[    9.954185] iwlagn 0000:09:00.0: PCI INT A disabled

joe@IGNAZ ~ $ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

pan0      Link encap:Ethernet  HWaddr 32:c9:9b:39:34:53  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by satty8610 on 2010-03-04
> **lowjoe55 said:**
> joe@IGNAZ ~ $ sudo ifup eth0
[sudo] password for joe: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

contents of /etc/network/interfaces:

auto lo
iface lo inet loopback

//following is what I inserted due to an recommendation of another thread..
auto eth0
iface eth0 inet dhcp

still, no wireless and no ethernet connection..



having included eth0 in the interface list, try restarting the network:
```
/etc/init.d/networking restart
```

and then do again```
 sudo ifup eth0
```

---

### Post by lowjoe55 on 2010-03-04
joe@IGNAZ ~ $ sudo modprobe tg3
[sudo] password for joe: 
joe@IGNAZ ~ $ sudo modprobe iwlagn

joe@IGNAZ ~ $ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                         [ OK ]
joe@IGNAZ ~ $ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

---

### Post by chili555 on 2010-03-04
Let's start with the easier issue. I wonder if the wireless is turned off, either by the hardware switch or by the key combination, for example Fn+F5 on some laptops. Please run:```
rfkill list
```Also, let's start diagnostics on the Broadcom (also known as Tigon):```
ls /lib/firmware/`uname -r`/tigon
lsmod
```Thanks.

---

### Post by lowjoe55 on 2010-03-04
joe@IGNAZ ~ $ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no



joe@IGNAZ ~ $ ls /lib/firmware/2.6.31-14-generic/tigon/
tg3.bin  tg3_tso5.bin  tg3_tso.bin



joe@IGNAZ ~ $ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
ppdev                   6688  0 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
dm_crypt               12928  0 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
joydev                 10272  0 
iwlagn                109052  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iwlcore               112508  1 iwlagn
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci_pci               7100  0 
snd_timer              22276  2 snd_pcm,snd_seq
psmouse                56180  0 
serio_raw               5280  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      8964  0 
parport                35340  2 ppdev,lp
acer_wmi               15936  0 
sdhci                  17472  1 sdhci_pci
mac80211              181236  2 iwlagn,iwlcore
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  0 
soundcore               7264  1 snd
btusb                  11856  2 
led_class               4096  3 iwlcore,acer_wmi,sdhci
ip_tables              11692  1 iptable_filter
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  3 iwlagn,iwlcore,mac80211
x_tables               16544  1 ip_tables
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
i915                  221064  3 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
tg3                   109600  0 
radeon                636000  0 
ttm                    36212  1 radeon
drm                   159584  5 i915,radeon,ttm
i2c_algo_bit            5760  2 i915,radeon
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  3 ttm,drm,intel_agp

---

### Post by chili555 on 2010-03-04
I'm not too sure what this might mean:> [ 3.981172] tg3: eth%d: Cannot get nvarm lock, tg3_nvram_init failed.Let's try:```
sudo rmmod -f tg3
sudo modprobe nvram
sudo modprobe tg3
ifconfig
```Did an interface, eth0 perhaps, appear? Also, please post:```
uname -r
```We may get a better result with an updated kernel.

---

### Post by lowjoe55 on 2010-03-05
joe@IGNAZ ~ $ sudo rmmod -f tg3
[sudo] password for joe:     
joe@IGNAZ ~ $ sudo modprobe nvram
joe@IGNAZ ~ $ sudo modprobe tg3

joe@IGNAZ ~ $ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

pan0      Link encap:Ethernet  HWaddr ee:9d:1f:2e:a0:af  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

joe@IGNAZ ~ $ uname -r
2.6.31-14-generic

---

### Post by chili555 on 2010-03-05
Please let me see:```
cat /sys/devices/platform/acer-wmi/wireless
```The file may be missing. It probably will be a 0 or a 1. We may help the wireless with:```
acer-wmi wireless=1
```Thanks.

---

### Post by lowjoe55 on 2010-03-06
joe@IGNAZ ~ $ cat /sys/devices/platform/acer-wmi/wireless
cat: /sys/devices/platform/acer-wmi/wireless: No such file or directory

joe@IGNAZ ~ $ cat /sys/devices/platform/acer-wmi/
driver/    modalias   rfkill/    threeg     
interface  power/     subsystem/ uevent     

joe@IGNAZ ~ $ acer-wmi wireless=1
acer-wmi: command not found

---

### Post by chili555 on 2010-03-06
We're getting closer! You may have to look around a bit, but see what this says:```
cat /sys/devices/platform/acer-wmi/[COLOR="Blue"]rfkill[/COLOR]
```It may be a directory and not a file. Keep drilling down and let's see if we can find a file, not a directory, that is set to a 1 or a 0 that, if we flip it back to the other value, get's the wireless going. Any *iwlagn* ought to run perfectly. This is a possible clue:> iwlagn 0000:09:00.0: Failed, HW not ready

---

### Post by lowjoe55 on 2010-03-14
Sorry for my late reply.. I hope you are still on it chili555..

Thats what i got for you:

joe@IGNAZ /sys/devices/platform/acer-wmi/rfkill $ ls -al
total 0
drwxr-xr-x 4 root root 0 2010-03-14 13:29 .
drwxr-xr-x 4 root root 0 2010-03-14 13:29 ..
drwxr-xr-x 3 root root 0 2010-03-14 13:29 rfkill1
drwxr-xr-x 3 root root 0 2010-03-14 13:29 rfkill2
joe@IGNAZ /sys/devices/platform/acer-wmi/rfkill $ ls rfkill1 -al
total 0
drwxr-xr-x 3 root root    0 2010-03-14 13:29 .
drwxr-xr-x 4 root root    0 2010-03-14 13:29 ..
-rw-r--r-- 1 root root 4096 2010-03-14 13:33 claim			//is set to 0
lrwxrwxrwx 1 root root    0 2010-03-14 13:33 device -> ../../../acer-wmi
-r--r--r-- 1 root root 4096 2010-03-14 13:33 index			//is set to 1
-r--r--r-- 1 root root 4096 2010-03-14 13:29 name			//is set to acer-wireless
-r--r--r-- 1 root root 4096 2010-03-14 13:33 persistent		//is set to 0
drwxr-xr-x 2 root root    0 2010-03-14 13:33 power
-rw-r--r-- 1 root root 4096 2010-03-14 13:29 state			//is set to 1
lrwxrwxrwx 1 root root    0 2010-03-14 13:29 subsystem -> ../../../../../class/rfkill
-r--r--r-- 1 root root 4096 2010-03-14 13:29 type			//is set to wlan
-rw-r--r-- 1 root root 4096 2010-03-14 13:29 uevent			//see below
joe@IGNAZ /sys/devices/platform/acer-wmi/rfkill $ ls rfkill2 -al
total 0
drwxr-xr-x 3 root root    0 2010-03-14 13:29 .
drwxr-xr-x 4 root root    0 2010-03-14 13:29 ..		
-rw-r--r-- 1 root root 4096 2010-03-14 14:00 claim			//is set to 0
lrwxrwxrwx 1 root root    0 2010-03-14 14:02 device -> ../../../acer-wmi
-r--r--r-- 1 root root 4096 2010-03-14 14:00 index			//is set to 2
-r--r--r-- 1 root root 4096 2010-03-14 13:29 name			//is set to acer-bluetooth
-r--r--r-- 1 root root 4096 2010-03-14 14:00 persistent		//is set to 0
drwxr-xr-x 2 root root    0 2010-03-14 14:00 power
-rw-r--r-- 1 root root 4096 2010-03-14 13:29 state			//is set to 1
lrwxrwxrwx 1 root root    0 2010-03-14 13:29 subsystem -> ../../../../../class/rfkill
-r--r--r-- 1 root root 4096 2010-03-14 13:29 type			//is set to bluetooth
-rw-r--r-- 1 root root 4096 2010-03-14 13:29 uevent			//see below

./rfkill1/uevent
RFKILL_NAME=acer-wireless
RFKILL_TYPE=wlan
RFKILL_STATE=1

./rfkill2/uevent
RFKILL_NAME=acer-bluetooth
RFKILL_TYPE=bluetooth
RFKILL_STATE=1


joe@IGNAZ /sys/devices/platform/acer-wmi/rfkill/rfkill1 $ ls ./device -la
lrwxrwxrwx 1 root root 0 2010-03-14 13:33 ./device -> ../../../acer-wmi

joe@IGNAZ /sys/devices/platform/acer-wmi/rfkill/rfkill1 $ ls ./power -la
total 0
drwxr-xr-x 2 root root    0 2010-03-14 13:33 .
drwxr-xr-x 3 root root    0 2010-03-14 13:29 ..
-rw-r--r-- 1 root root 4096 2010-03-14 13:33 wakeup			//empty file..

joe@IGNAZ /sys/devices/platform/acer-wmi/rfkill/rfkill1 $ ls ./subsystem -la
lrwxrwxrwx 1 root root 0 2010-03-14 13:29 ./subsystem -> ../../../../../class/rfkill


Thanks!

---

### Post by chili555 on 2010-03-14
I am on it! We have couple of things to try. First, please do:```
sudo rmmod -f acer-wmi
sudo modprobe acer-wmi wireless=1
```Now check:```
sudo lshw -C network
```Is your wireless interface disabled? Does it appear in Network Manager?

Second, it looks like rfkill1 is the wireless interface.> ./rfkill[COLOR="Red"]1[/COLOR]/uevent
RFKILL_NAME=acer-[COLOR="Red"]wireless[/COLOR]
RFKILL_TYPE=wlan
RFKILL_STATE=1 Let's try:```
sudo su
echo 0 > /sys/devices/platform/acer-wmi/rfkill/rfkill1/state
```Again check *lshw* and Network Manager. Any improvements?

---

### Post by lowjoe55 on 2010-03-16
IGNAZ joe # rmmod -f acer-wmi
IGNAZ joe # modprobe acer-wmi wireless=1
FATAL: Error inserting acer_wmi (/lib/modules/2.6.31-14-generic/kernel/drivers/platform/x86/acer-wmi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
IGNAZ joe # lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ba000000-ba00ffff
  *-network
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: driver=iwlagn latency=0
       resources: irq:17 memory:ba100000-ba101fff




IGNAZ joe # echo 0 > /sys/devices/platform/acer-wmi/rfkill/rfkill3/state 
//for some reason the rfkill1 and rfkill2 disappeared, and were replaced by rfkill3 and rfkill4 .. the name of rfkill3 was acer-wireless so i suppose what i did wasn't wrong..
IGNAZ joe # lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ba000000-ba00ffff
  *-network
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: driver=iwlagn latency=0
       resources: irq:17 memory:ba100000-ba101fff

---

### Post by lowjoe55 on 2010-03-20
up

---

### Post by chili555 on 2010-03-21
Here is a post suggesting that the latest kernel will help:  [http://ubuntuforums.org/showthread.php?t=1353041&highlight=8935g](http://ubuntuforums.org/showthread.php?t=1353041&highlight=8935g)

See post #2.

You might download linux-image-2.6.31-20-generic if you don't already have it. Find out with:```
uname -r
```Find it here: [http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-20-386](http://packages.ubuntu.com/karmic/any/linux-image-2.6.31-20-386)

You might need the 64-bit version.

Install with:```
sudo dpkg -i linux-image-*
```Reboot and let us know.

---

### Post by lowjoe55 on 2010-03-22
Hey!
The new kernel activated both interfaces.. Got wireless working immediately, but an error with the wired network interface (device not managed) as described in 

[http://ubuntuforums.org/showthread.php?t=1109585](http://ubuntuforums.org/showthread.php?t=1109585)

occured...

Fortunately the steps described in that link solved the problem for me too!

Thank you all for helping with that problems! You are a great community! And chili555, you are a great guy! Thanks alot!

---

