---
title: "Acer netbook w/ atheros wifi and pci express fast ethernet not turning on and connect"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by Stolgrove on 2011-09-19
Ok, I am running this Acer Aspire One netbook with Realtek Ethernet port and Atheros wifi AR5001 series wifi. I went on to get the drivers for the wifi since that is my primary internet source. But ndiswrapper and ndisgtk won't load, can't find package "*".  How can I get these loaded and get on with life and learning Linux like I said I should've in 94?

---

### Post by Stolgrove on 2011-09-25
So the deeper I look into getting this machine setup, the more frustrated I'm becoming as I have little time to my days and time is running short before I'm stranded with what will become a paperweight.  
I am running Lucid 10.04 with kernal version 2.6.32 on x 86, I am now trying to install ndiswrapper....
CODE
[EMAIL="anonymous@anonymous:~/ndiswrapper-1.57rc1$"]anonymous@anonymous:~/ndiswrapper-1.57rc1$[/EMAIL] sudo make install
make -C driver install
make[1]: Entering directory `/home/anonymous/ndiswrapper-1.57rc1/driver'
make modules
make[2]: Entering directory `/home/anonymous/ndiswrapper-1.57rc1/driver'
make -C /usr/src/linux-headers-2.6.32-21-generic M=/home/anonymous/ndiswrapper-1.57rc1/driver
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[3]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[3]: gcc: Command not found
  LD      /home/anonymous/ndiswrapper-1.57rc1/driver/built-in.o
/bin/sh: ar: not found
make[4]: *** [/home/anonymous/ndiswrapper-1.57rc1/driver/built-in.o] Error 127
make[3]: *** [_module_/home/anonymous/ndiswrapper-1.57rc1/driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/home/anonymous/ndiswrapper-1.57rc1/driver'
make[1]: *** [ndiswrapper.ko] Error 2
make[1]: Leaving directory `/home/anonymous/ndiswrapper-1.57rc1/driver'
make: *** [install] Error 2
[EMAIL="anonymous@anonymous:~/ndiswrapper-1.57rc1$"]anonymous@anonymous:~/ndiswrapper-1.57rc1$[/EMAIL] 
/CODE
I am also reading about updating the headers in the kernal. someone help me get on the right track. being fulltime school and learning this. well its a load

---

### Post by Stolgrove on 2011-09-25
```
:~/ndiswrapper-1.57rc1$ sudo make install
make -C driver install
make[1]: Entering directory `/home/anonymous/ndiswrapper-1.57rc1/driver'
make modules
make[2]: Entering directory `/home/anonymous/ndiswrapper-1.57rc1/driver'
make -C /usr/src/linux-headers-2.6.32-21-generic M=/home/anonymous/ndiswrapper-1.57rc1/driver
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[3]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[3]: gcc: Command not found
  LD      /home/anonymous/ndiswrapper-1.57rc1/driver/built-in.o
/bin/sh: ar: not found
make[4]: *** [/home/anonymous/ndiswrapper-1.57rc1/driver/built-in.o] Error 127
make[3]: *** [_module_/home/anonymous/ndiswrapper-1.57rc1/driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/home/anonymous/ndiswrapper-1.57rc1/driver'
make[1]: *** [ndiswrapper.ko] Error 2
make[1]: Leaving directory `/home/anonymous/ndiswrapper-1.57rc1/driver'
make: *** [install] Error 2
```
 
 
```
 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:e8:2e:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:658248 (658.2 KB)  TX bytes:8928 (8.9 KB)
          Interrupt:28 Base address:0xe000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116714 (116.7 KB)  TX bytes:116714 (116.7 KB)
 

```
 
 
```
 
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
 

```
 
 
 
```
:~$ sudo lspci -v
[sudo] password for anonymous: 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0
 Capabilities: [e0] Vendor Specific Information <?>
 Kernel driver in use: agpgart-intel
 Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0, IRQ 16
 Memory at 78480000 (32-bit, non-prefetchable) [size=512K]
 I/O ports at 60c0 [size=8]
 Memory at 60000000 (32-bit, prefetchable) [size=256M]
 Memory at 78500000 (32-bit, non-prefetchable) [size=256K]
 Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
 Capabilities: [d0] Power Management version 2
 Kernel driver in use: i915
 Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0
 Memory at 78400000 (32-bit, non-prefetchable) [size=512K]
 Capabilities: [d0] Power Management version 2
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0, IRQ 16
 Memory at 78540000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: [50] Power Management version 2
 Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
 Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
 Capabilities: [100] Virtual Channel <?>
 Capabilities: [130] Root Complex Link <?>
 Kernel driver in use: HDA Intel
 Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
 I/O behind bridge: 00005000-00005fff
 Memory behind bridge: 77300000-783fffff
 Prefetchable memory behind bridge: 0000000070000000-0000000070ffffff
 Capabilities: [40] Express Root Port (Slot+), MSI 00
 Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
 Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 015b
 Capabilities: [a0] Power Management version 2
 Capabilities: [100] Virtual Channel <?>
 Capabilities: [180] Root Complex Link <?>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
 I/O behind bridge: 00003000-00004fff
 Memory behind bridge: 76300000-772fffff
 Prefetchable memory behind bridge: 0000000071000000-00000000720fffff
 Capabilities: [40] Express Root Port (Slot+), MSI 00
 Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
 Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 015b
 Capabilities: [a0] Power Management version 2
 Capabilities: [100] Virtual Channel <?>
 Capabilities: [180] Root Complex Link <?>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
 I/O behind bridge: 00002000-00002fff
 Memory behind bridge: 75200000-762fffff
 Prefetchable memory behind bridge: 0000000072100000-00000000730fffff
 Capabilities: [40] Express Root Port (Slot+), MSI 00
 Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
 Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 015b
 Capabilities: [a0] Power Management version 2
 Capabilities: [100] Virtual Channel <?>
 Capabilities: [180] Root Complex Link <?>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
 I/O behind bridge: 00001000-00001fff
 Memory behind bridge: 74100000-751fffff
 Prefetchable memory behind bridge: 0000000073100000-00000000740fffff
 Capabilities: [40] Express Root Port (Slot+), MSI 00
 Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
 Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 015b
 Capabilities: [a0] Power Management version 2
 Capabilities: [100] Virtual Channel <?>
 Capabilities: [180] Root Complex Link <?>
 Kernel driver in use: pcieport
 Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, medium devsel, latency 0, IRQ 16
 I/O ports at 6080 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, medium devsel, latency 0, IRQ 17
 I/O ports at 6060 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, medium devsel, latency 0, IRQ 18
 I/O ports at 6040 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, medium devsel, latency 0, IRQ 19
 I/O ports at 6020 [size=32]
 Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, medium devsel, latency 0, IRQ 16
 Memory at 78544400 (32-bit, non-prefetchable) [size=1K]
 Capabilities: [50] Power Management version 2
 Capabilities: [58] Debug port: BAR=1 offset=00a0
 Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
 Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 015b
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, medium devsel, latency 0
 Capabilities: [e0] Vendor Specific Information <?>
 Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
 I/O ports at 01f0 [size=8]
 I/O ports at 03f4 [size=1]
 I/O ports at 0170 [size=8]
 I/O ports at 0374 [size=1]
 I/O ports at 60a0 [size=16]
 Capabilities: [70] Power Management version 2
 Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: medium devsel, IRQ 11
 I/O ports at 6000 [size=32]
 Kernel modules: i2c-i801
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0, IRQ 28
 I/O ports at 3000 [size=256]
 Memory at 71010000 (64-bit, prefetchable) [size=4K]
 Memory at 71000000 (64-bit, prefetchable) [size=64K]
 Expansion ROM at 71020000 [disabled] [size=128K]
 Capabilities: [40] Power Management version 3
 Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
 Capabilities: [70] Express Endpoint, MSI 01
 Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
 Capabilities: [cc] Vital Product Data <?>
 Capabilities: [100] Advanced Error Reporting <?>
 Capabilities: [140] Virtual Channel <?>
 Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-00-04
 Kernel driver in use: r8169
 Kernel modules: r8169
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
 Subsystem: Foxconn International, Inc. Device e008
 Flags: bus master, fast devsel, latency 0, IRQ 18
 Memory at 75200000 (64-bit, non-prefetchable) [size=64K]
 Capabilities: [40] Power Management version 2
 Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
 Capabilities: [60] Express Legacy Endpoint, MSI 00
 Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
 Capabilities: [100] Advanced Error Reporting <?>
 Capabilities: [140] Virtual Channel <?>
 Kernel driver in use: ath5k
 Kernel modules: ath5k
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0, IRQ 19
 Memory at 74100300 (32-bit, non-prefetchable) [size=256]
 [virtual] Expansion ROM at 73100000 [disabled] [size=32K]
 Capabilities: [a4] Power Management version 3
 Capabilities: [80] Express Endpoint, MSI 00
 Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
 Kernel driver in use: sdhci-pci
 Kernel modules: sdhci-pci
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0, IRQ 19
 Memory at 74100200 (32-bit, non-prefetchable) [size=256]
 Capabilities: [a4] Power Management version 3
 Capabilities: [80] Express Endpoint, MSI 00
 Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
 Kernel modules: sdhci-pci
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0, IRQ 19
 Memory at 74100100 (32-bit, non-prefetchable) [size=256]
 Capabilities: [a4] Power Management version 3
 Capabilities: [80] Express Endpoint, MSI 00
 Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
 Kernel driver in use: jmb38x_ms
 Kernel modules: jmb38x_ms
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
 Subsystem: Acer Incorporated [ALI] Device 015b
 Flags: bus master, fast devsel, latency 0, IRQ 11
 Memory at 74100000 (32-bit, non-prefetchable) [size=256]
 Capabilities: [a4] Power Management version 3
 Capabilities: [80] Express Endpoint, MSI 00
 Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

```
 
```
:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
04:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
04:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
04:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
04:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]

```
 
```
:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8901  2 
fat                    47767  1 vfat
nls_utf8                1069  1 
isofs                  29250  1 
usb_storage            39425  3 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
joydev                  8708  0 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
arc4                    1153  2 
snd_mixer_oss          13746  1 snd_pcm_oss
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121792  0 
snd_timer              19098  2 snd_pcm,snd_seq
mac80211              204922  1 ath5k
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  4 
ath                     7611  1 ath5k
drm_kms_helper         29297  1 i915
acerhdf                 6691  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               56990  0 
drm                   162471  5 i915,drm_kms_helper
cfg80211              126485  3 ath5k,mac80211,ath
jmb38x_ms               7311  0 
lp                      7028  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24177  2 i915
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
memstick                8237  1 jmb38x_ms
led_class               2864  2 ath5k,sdhci
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
parport                32635  2 ppdev,lp
r8169                  33884  0 
mii                     4381  1 r8169

```
 
```
:~$ dmesg | grep ath
[64951.196320] ath5k 0000:03:00.0: PCI INT A disabled
[64951.824406] ath5k 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[64951.824456] ath5k 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x75200004)
[64951.824471] ath5k 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[64951.824490] ath5k 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[64952.127578] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[68412.540327] ath5k 0000:03:00.0: PCI INT A disabled
[68413.168414] ath5k 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[68413.168465] ath5k 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x75200004)
[68413.168480] ath5k 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[68413.168498] ath5k 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[68413.451593] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

```
 
```
:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:e8:2e:4c
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:3000(size=256) memory:71010000-71010fff(prefetchable) memory:71000000-7100ffff(prefetchable) memory:71020000-7103ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:6c:93:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:75200000-7520ffff

```
 
```
:~$ iwlist wlan0 scan
wlan0     Failed to read scan data : Network is down

```
 
```
:~$ iwlist wifi0 scan
wifi0     Interface doesn't support scanning.

```
 
```
:~$ lsb_release -d
Description: Ubuntu 10.04 LTS

```
 
```
:~$ uname -mr
2.6.32-21-generic i686

```
 
```
:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                               [ OK ] 

```

---

### Post by Stolgrove on 2011-10-01
My first roadblock to fixing this issue is that I do not have root "SU" access. Once this is fixed hopefully I can install "ndiswrapper" successfully. 
 
```

[EMAIL="anonymous@anonymous:~/src/ndiswrapper-1.57rc1$"]anonymous@anonymous:~/src/ndiswrapper-1.57rc1$[/EMAIL] su
Password: 
su: Authentication failure
anonymous@anonymous:~/src/ndiswrapper-1.57rc1$ sudo make install
[sudo] password for anonymous: 
make -C driver install
make[1]: Entering directory `/home/anonymous/src/ndiswrapper-1.57rc1/driver'
make modules
make[2]: Entering directory `/home/anonymous/src/ndiswrapper-1.57rc1/driver'
make -C /usr/src/linux-headers-2.6.32-21-generic M=/home/anonymous/src/ndiswrapper-1.57rc1/driver
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-21-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[3]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[3]: gcc: Command not found
  LD      /home/anonymous/src/ndiswrapper-1.57rc1/driver/built-in.o
/bin/sh: ar: not found
make[4]: *** [/home/anonymous/src/ndiswrapper-1.57rc1/driver/built-in.o] Error 127
make[3]: *** [_module_/home/anonymous/src/ndiswrapper-1.57rc1/driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/home/anonymous/src/ndiswrapper-1.57rc1/driver'
make[1]: *** [ndiswrapper.ko] Error 2
make[1]: Leaving directory `/home/anonymous/src/ndiswrapper-1.57rc1/driver'
make: *** [install] Error 2

```

---

### Post by Stolgrove on 2011-10-01
"su" was giving me an issue because the "passwd" was not set for it, even though "sudo" was set.  "sudo passwd" (also could have been "sudo bash") fixed this small issue.
But I still recieve the same errors in installing ndiswrapper..

---

### Post by Stolgrove on 2011-10-01
Running under "su"
"service network-manager restart"
 
my wifi light came on and allowed me to access the connection tools in the program bar. so far it has been showing activity, trying to connect for 5 minutes. After this it quit and gave me a "network disconnected" notice. this is progress...
 
I still believe I need ndiswrapper installed to allow driver updates for both wifi and ethernet.

---

