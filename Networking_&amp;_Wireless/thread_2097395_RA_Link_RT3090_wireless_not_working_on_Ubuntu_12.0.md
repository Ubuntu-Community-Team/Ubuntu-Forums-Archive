---
title: "RA Link RT3090 wireless not working on Ubuntu 12.04 LTS"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by klaszlo on 2012-12-23
MSI Wind U160 laptop with RA LINK wireless network built-in
Dual boot, Win7 starter , Ubuntu 12.04 LTS

Wireless works in Windows, but doesn't in Ubuntu.

In Ubuntu menu says "Wireless networks device not ready"

I'm not a Linux user; have read lot about similar issues with RT3090 and tried most of solutions.
Wireless still not working.

Any help is greatly appreciated.
Thank you.

*******
I use for test a wireless router with encryption disabled.

****************
Soft and hard block seems to work OK.
rfkill output is consistent with the state of hardware switch or software setting in menu.
 
****************
output of "lspci"

03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

****************
output of "sudo lshw -class network"

*-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: ra0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.4 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:fd600000-fd60ffff

****************
output of "iwconfig"

lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

****************
output of "nm-tool"

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             unavailable
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

****************
System settings, Additional drivers shows 'rt390sta" activated and in use.

****************
Output of "lsmod"

Module                  Size  Used by
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
msi_laptop             14503  0 
sparse_keymap          13658  1 msi_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67203  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  0 
ppdev                  12849  0 
videodev               86588  1 uvcvideo
bnep                   17830  2 
snd_timer              28931  2 snd_pcm,snd_seq
bluetooth             158479  7 bnep
psmouse                96718  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  419262  4 
drm_kms_helper         45466  1 i915
drm                   197641  5 i915,drm_kms_helper
binfmt_misc            17292  1 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  19068  1 i915
mac_hid                13077  0 
rt3090sta             844169  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
r8169                  56368  0 

****************
output of "lspci -nnk"

00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:6891]
	Kernel driver in use: rt2860
	Kernel modules: rt3090sta, rt2800pci

****************
kernel modules "rt2800pci" is blacklisted

---

### Post by Pjotr123 on 2012-12-23
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by Hadaka on 2012-12-23
Hi, it looks like you may have blacklisted the wrong driver.
please read this thread..

[http://ubuntuforums.org/showthread.php?t=2040240&highlight=rt3090](http://ubuntuforums.org/showthread.php?t=2040240&highlight=rt3090)

thanks.

---

### Post by klaszlo on 2012-12-24
Thank you for help.

Finally, after reinstalling Ubuntu 12.04 and trying without luck several other Linuxes (Moblin, PCLinuxOS, Mint), I noticed that the hardware switch doesn't block the wireless. Or activate it...

So I upgraded the BIOS to last version and this solved the problem completely.

Conclusion: 
RA Link RT3090 hardware in MSI WIND U160 with latest BIOS (13 May 2011) works out-of-the-box in Ubuntu 12.04 LTS. It uses the rt2800pci driver. No need for other drivers.
Hopefully it will behave well and will be stable.

Some details:

********
Linux WindU160 3.2.0-35-generic-pae #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 i686 i686 i386 GNU/Linux

**********
NetworkManager Tool

State: connected (global)

- Device: wlan0  [xxxSSIDxxx] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        40:61:86:9B:23:4F

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    elcid:           Infra, 00:21:91:76:D2:34, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    default:         Infra, 00:1F:1F:1C:DA:D8, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    linksys:         Infra, 00:14:BF:F2:A0:13, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    *xxxxSSIDxxxx: Infra, 00:21:27:ED:FE:B4, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA2

*********

Module                  Size  Used by
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
msi_laptop             14503  0 
sparse_keymap          13658  1 msi_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              18340  0 
rt2800lib              53298  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48875  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436493  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  419297  3 
psmouse                86520  0 
cfg80211              178877  2 rt2x00lib,mac80211
serio_raw              13027  0 
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6           12687  1 rt2800pci
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158479  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
soundcore              14635  1 snd
drm_kms_helper         45466  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
r8169                  56368  0 

************
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 40:61:86:9b:23:4f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-35-generic-pae firmware=0.34 ip=192.168.100.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fd600000-fd60ffff

*************
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xxxxSSIDxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:27:ED:FE:B4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:26  Invalid misc:53   Missed beacon:0

eth0      no wireless extensions.
**************

---

