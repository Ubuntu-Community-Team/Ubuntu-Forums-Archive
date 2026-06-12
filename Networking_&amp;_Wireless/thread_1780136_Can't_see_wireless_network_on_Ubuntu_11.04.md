---
title: "Can't see wireless network on Ubuntu 11.04"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by prahar on 2011-06-11
I only just installed Ubuntu 11.04 dual booted with Windows 7 which I have been using all this while. On Windows 7, I use a protected wireless network. I also have access to a wired network. Both the wireless and wired network work perfectly on 7.

During the installation of Ubuntu, it asked me to connect to a wireless network, which I could without issue.

However, once Ubuntu 11.04 completed installation, its no longer able to detect the wireless network! It's not even connecting to my wired network.

What should I do?

---

### Post by Talon2 on 2011-06-11
Here is what I would do given your description:

- Connect your system to the internet via ethernet cable.

- Select Hardware Drivers and install any wifi related drivers it suggests.

Reboot and see what happens.

Good luck.

---

### Post by Vxr on 2011-06-17
I have the same problem. Please help

---

### Post by Zhanger on 2011-06-20
Me too, I have the exact same issue.

I installed Ubuntu 11.04 along side Windows Vista and during installation it could connect to my wireless network fine; now it doesn't even detect the presence of any wireless networks.

It is quite frustrating :(

Any help/fix would be appreciated.

---

### Post by mrbunn on 2011-06-26
I'm brand new to Linux. I just installed Ubuntu 11.04 and cannot connect to wifi either. Ethernet works fine, but there are no wireless networks being detected. Updated my drivers, looks like it should be running but nothing is detected in network connections.

Running ubuntu by itself. No dualboot.

Please help!!!!

---

### Post by josephmills on 2011-06-26
hey guy welcome to ubuntu forms first lets take a look at your hardware open your terminals (ctrl+alt+t)and type in ```
lspci -nn
``` then ```
lsmod 
``` then ```
rfkill list all 
``` then this last one takes some time to load ```
sudo lshw -c network 
```  then paste it all here for us to see we will get you fixed up or at least try real hard. Once again welcome to ubuntu forums

---

### Post by shoryuken on 2011-07-10
Since I'm having a similar problem here is the output for my system. My problem is intermittent so my computer works fine for several starts and then for a few starts I won't detect anything.  It will take several reboots before working again.

Here is the output when things aren't working:
```

arash@BeatMachineL:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
arash@BeatMachineL:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
autofs4                27918  2 
snd_usb_audio          91410  1 
snd_usbmidi_lib        24388  1 snd_usb_audio
arc4                   12473  2 
snd_hda_codec_realtek   255820  1 
pcmcia                 39671  0 
snd_hda_intel          24140  2 
ath5k                 144412  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
ath                    19141  1 ath5k
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
gspca_ov519            44223  0 
mac80211              257001  1 ath5k
gspca_main             27894  1 gspca_ov519
joydev                 17322  0 
snd_pcm                80244  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
videodev               75143  1 gspca_main
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
yenta_socket           27230  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  450944  3 
pcmcia_rsrc            18292  1 yenta_socket
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              12898  0 
drm_kms_helper         40745  1 i915
tifm_core              15040  1 tifm_7xx1
snd                    55295  17 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  3 ath5k,ath,mac80211
drm                   180037  4 i915,drm_kms_helper
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
sony_laptop            34432  0 
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49172  0 
arash@BeatMachineL:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
arash@BeatMachineL:~$ sudo lshw -c network
[sudo] password for arash: 
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1a:80:44:65:7b
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d6000000-d6003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:08:a4:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:da000000-da00ffff

```

and here is the output when things work:
```

arash@BeatMachineL:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 16)
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
08:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
arash@BeatMachineL:~$ lsmod
Module                  Size  Used by
md4                    12523  0 
nls_utf8               12493  1 
cifs                  247650  2 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
autofs4                27918  20 
snd_usb_audio          91410  1 
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_hda_codec_realtek   255820  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
pcmcia                 39671  0 
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
snd_pcm                80244  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
gspca_ov519            44223  0 
i915                  450944  3 
snd_seq_midi_event     14475  1 snd_seq_midi
gspca_main             27894  1 gspca_ov519
ath5k                 144412  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
videodev               75143  1 gspca_main
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
psmouse                73312  0 
sony_laptop            34432  0 
yenta_socket           27230  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  4 i915,drm_kms_helper
tifm_7xx1              12898  0 
pcmcia_rsrc            18292  1 yenta_socket
i2c_algo_bit           13184  1 i915
snd                    55295  17 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core              15040  1 tifm_7xx1
cfg80211              156212  3 ath5k,ath,mac80211
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49172  0 
arash@BeatMachineL:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
arash@BeatMachineL:~$ sudo lshw -c network
[sudo] password for arash: 
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1a:80:44:65:7b
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d6000000-d6003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:1c:26:08:a4:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.0.110 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:da000000-da00ffff

```

Any help would be greatly appreciated.

Cheers

---

### Post by nego0 on 2011-08-03
Same here please help!
i've got an LW162 wireless 150n pci card (sweex)

```
desmania@desmania-MS-7100:~$ lspci -nn
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3)
00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev f2)
00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev f3)
00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev f3)
00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2)
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:06.0 Network controller [0280]: Ralink corp. Device [1814:3060]
01:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
01:0c.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46)
01:0d.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
05:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8500 GT] [10de:0421] (rev a1)
desmania@desmania-MS-7100:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vesafb                 13761  1 
nvidia              10709116  40 
snd_ca0106             44783  2 
snd_ac97_codec        134270  1 snd_ca0106
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96391  2 snd_ca0106,snd_ac97_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
rt2800pci              18487  0 
rt2800lib              45181  1 rt2800pci
snd_rawmidi            30486  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
crc_ccitt              12667  1 rt2800lib
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
snd                    67382  11 snd_ca0106,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_ca0106,snd_pcm
cfg80211              178528  2 rt2x00lib,mac80211
i2c_nforce2            13058  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
eeprom_93cx6           12725  1 rt2800pci
ppdev                  17113  0 
parport_pc             36959  1 
k8temp                 13016  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
floppy                 74120  0 
r8169                  48022  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
forcedeth              63555  0 
sata_nv                32054  0 
pata_amd               14130  2 
desmania@desmania-MS-7100:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
desmania@desmania-MS-7100:~$ sudo lshw -c network
[sudo] password for desmania: 
  *-network:0             
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wlan0
       version: 00
       serial: 00:16:0a:28:45:fe
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11 latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fdee0000-fdeeffff
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth0
       version: 10
       serial: 00:16:0a:1c:45:6c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.38 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:dc00(size=256) memory:fdeff000-fdeff0ff memory:fdf00000-fdf1ffff

```

---

### Post by wildmanne39 on 2011-08-03
> **nego0 said:**
> Same here please help!
i've got an LW162 wireless 150n pci card (sweex)

```
desmania@desmania-MS-7100:~$ lspci -nn
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3)
00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev f2)
00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev f3)
00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev f3)
00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2)
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:06.0 Network controller [0280]: Ralink corp. Device [1814:3060]
01:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
01:0c.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46)
01:0d.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
05:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8500 GT] [10de:0421] (rev a1)
desmania@desmania-MS-7100:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vesafb                 13761  1 
nvidia              10709116  40 
snd_ca0106             44783  2 
snd_ac97_codec        134270  1 snd_ca0106
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96391  2 snd_ca0106,snd_ac97_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
rt2800pci              18487  0 
rt2800lib              45181  1 rt2800pci
snd_rawmidi            30486  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
crc_ccitt              12667  1 rt2800lib
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
snd                    67382  11 snd_ca0106,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_ca0106,snd_pcm
cfg80211              178528  2 rt2x00lib,mac80211
i2c_nforce2            13058  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
eeprom_93cx6           12725  1 rt2800pci
ppdev                  17113  0 
parport_pc             36959  1 
k8temp                 13016  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
floppy                 74120  0 
r8169                  48022  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
forcedeth              63555  0 
sata_nv                32054  0 
pata_amd               14130  2 
desmania@desmania-MS-7100:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
desmania@desmania-MS-7100:~$ sudo lshw -c network
[sudo] password for desmania: 
  *-network:0             
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wlan0
       version: 00
       serial: 00:16:0a:28:45:fe
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11 latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fdee0000-fdeeffff
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth0
       version: 10
       serial: 00:16:0a:1c:45:6c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.38 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:dc00(size=256) memory:fdeff000-fdeff0ff memory:fdf00000-fdf1ffff

```Hi, here is a link with a good guide for setting up your wireless card.
[http://ubuntuforums.org/showthread.php?t=1608095&highlight=rt3562sta](http://ubuntuforums.org/showthread.php?t=1608095&highlight=rt3562sta)
Thank you

---

### Post by josephmills on 2011-08-03
> **nego0 said:**
> Same here please help!
i've got an LW162 wireless 150n pci card (sw
desmania@desmania-MS-7100:~$ lspci -nn
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3)
00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev f2)
00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev f3)
00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev f3)
00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2)
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
[COLOR="Red"]01:06.0 Network controller [0280]: Ralink corp. Device [1814:3060][/COLOR]
01:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
01:0c.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46)
01:0d.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
05:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8500 GT] [10de:0421] (rev a1)
desmania@desmania-MS-7100:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vesafb                 13761  1 
nvidia              10709116  40 
snd_ca0106             44783  2 
snd_ac97_codec        134270  1 snd_ca0106
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96391  2 snd_ca0106,snd_ac97_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
[COLOR="red"]rt2800pci              18487  0 
rt2800lib              45181  1 rt2800pci[/COLOR]
snd_rawmidi            30486  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
[COLOR="red"]crc_ccitt              12667  1 rt2800lib[/COLOR]
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
[COLOR="red"]rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci[/COLOR]
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
[COLOR="red"]mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib[/COLOR]
snd                    67382  11 snd_ca0106,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_ca0106,snd_pcm
[COLOR="red"]cfg80211              178528  2 rt2x00lib,mac80211[/COLOR]
i2c_nforce2            13058  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
[COLOR="red"]eeprom_93cx6           12725  1 rt2800pci[/COLOR]
ppdev                  17113  0 
parport_pc             36959  1 
k8temp                 13016  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
floppy                 74120  0 
r8169                  48022  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
forcedeth              63555  0 
sata_nv                32054  0 
pata_amd               14130  2 
desmania@desmania-MS-7100:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
desmania@desmania-MS-7100:~$ sudo lshw -c network
[sudo] password for desmania: 
  *-network:0             
       [COLOR="red"]description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp[/COLOR].
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wlan0
       version: 00
       serial: 00:16:0a:28:45:fe
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes[COLOR="red"] driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11[/COLOR] latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fdee0000-fdeeffff
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth0
       version: 10
       serial: 00:16:0a:1c:45:6c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.38 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:dc00(size=256) memory:fdeff000-fdeff0ff memory:fdf00000-fdf1ffff
[/code]

Hi there lets look at the part that I put in red this shows the mods and what is loaded (driver) I see that you need the rt2800pci   looks like you got that and maybe more 1st lets try this ```
sudo modprobe rt2800pci
``` anything ? if no could we please see a ```
 cat /etc/modprobe.d/blacklist.conf 
``` thanks



**wildmanee did not see you there sorry. must have been typing at the same time :)**

---

### Post by nego0 on 2011-08-03
```
desmania@desmania-MS-7100:~$  cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by wildmanne39 on 2011-08-03
Hi, the driver you have installed is the wrong one, the link I gave you has the right one and the procedure to install it and blacklist the ones you have installed.

Unless josephmills as a different idea.
Thank you

---

### Post by nego0 on 2011-08-03
here the code ```
desmania@desmania-MS-7100:~$  cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

> **josephmills said:**
> Hi there lets look at the part that I put in red this shows the mods and what is loaded (driver) I see that you need the rt2800pci   looks like you got that and maybe more 1st lets try this ```
sudo modprobe rt2800pci
``` anything ? if no could we please see a ```
 cat /etc/modprobe.d/blacklist.conf 
``` thanks



**wildmanee did not see you there sorry. must have been typing at the same time :)**

---

### Post by nego0 on 2011-08-03
> **wildmanne39 said:**
> Hi, the driver you have installed is the wrong one, the link I gave you has the right one and the procedure to install it and blacklist the ones you have installed.

Unless josephmills as a different idea.
Thank you

I installed the gcc build- essential downloaded the driver from the link u gave me. changed (n) in to (y)
then went to the terminal:
```
desmania@desmania-MS-7100:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.

```
did i need to unpack the file or something
if yes where should i put it?

---

### Post by wildmanne39 on 2011-08-03
Hi, you need to change into the directory where you downloaded the file.

Also make sure you have installed linux-headers.

---

### Post by nego0 on 2011-08-03
> **wildmanne39 said:**
> Hi, you need to change into the directory where you downloaded the file.

Also make sure you have installed linux-headers.

I'm new to these kind of things so what do you mean by that

I'm a bit of a newb:-k

---

### Post by wildmanne39 on 2011-08-03
Hi, to make it easier since you do not know where you downloaded it too, redownload it and choose the Desktop. Then run this command.
```
cd ~/Desktop

``` 
then 
```
sudo make
```
then
```
sudo make install
```
then continue with the instructions on that page.
Thank you

---

### Post by wildmanne39 on 2011-08-03
Hi, also use the instructions from the other page and blacklist rt2x00pci and the one listed on the other page.
Thank you

---

### Post by nego0 on 2011-08-04
> **wildmanne39 said:**
> Hi, also use the instructions from the other page and blacklist rt2x00pci and the one listed on the other page.
Thank you

Can you tell me in wich order i need to do everything exactly
Thnx

---

### Post by wildmanne39 on 2011-08-04
Hi, first please run this command:
```
sudo apt-get install build-essential linux-headers-generic
```

Then download the driver to your Desktop:
[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D)

Then follow the instructions in the README file.
Navigate to downloaded_driver_folder/os/linux and open config.mk in a text editor.
Find and set so that it indicates ( y ) at the end of this text string:
```
HAS_WPA_SUPPLICANT=y
```
and also set 
```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```
Then run this command:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Add this to the end of that file:
```
blacklist rt2800pci
blacklist rt2x00pci 
```
```
cd ~/Desktop
```
then
```
sudo make
```
then
```
sudo make install
```
then
```
sudo modprobe rt3562sta
```
then
```
sudo ifconfig ra0 inet up
```
Do this please:
Code:

```
gksu gedit /etc/modules
```

Add **rt3562sta.ko** right under lp
rtc then save and close gedit and restart your computer.
Thank you

---

### Post by shoryuken on 2011-08-05
Not sure if the problem I had posted here was exactly the same as the one posted in the OP, but I tried booting with Kernel 2.6.35-28-generic and notice a significant improvement with the wireless connection.

After a lot of frustrating searches I stumbled on a bug report: 
[Regression latest kernel breaks my Atheros AR5001 wifi]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710738")

This lead me to install Kernel 2.6.39 rc4 by downloading the 3 deb files listed on this ubuntuguide.net page:
[http://ubuntuguide.net/how-to-install-linux-kernel-2-6-39-rc4-in-ubuntu-11-04-natty]("http://ubuntuguide.net/how-to-install-linux-kernel-2-6-39-rc4-in-ubuntu-11-04-natty")

My wireless connection problem seems to be fixed as a result of the upgrade (although I notice some flickering of my screen on logon - I can live with that).

Just thought I would share my experience, in case it could be useful to others here.

Cheers

---

### Post by nego0 on 2011-08-05
> **wildmanne39 said:**
> Hi, first please run this command:
```
sudo apt-get install build-essential linux-headers-generic
```

Then download the driver to your Desktop:
[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D)

Then follow the instructions in the README file.
Navigate to downloaded_driver_folder/os/linux and open config.mk in a text editor.
Find and set so that it indicates ( y ) at the end of this text string:
```
HAS_WPA_SUPPLICANT=y
```
and also set 
```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```
Then run this command:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Add this to the end of that file:
```
blacklist rt2800pci
blacklist rt2x00pci 
```
```
cd ~/Desktop
```
then
```
sudo make
```
then
```
sudo make install
```
then
```
sudo modprobe rt3562sta
```
then
```
sudo ifconfig ra0 inet up
```
Thank you

Thnx for the help wildmanne39!!
can somebody else help me with the readme file? 

i get this part:
```
In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
(But thats already there)
```

```
HAS_WPA_SUPPLICANT=y
```

```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

need help with this:
```
 [COLOR="red"]define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.[/COLOR]
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y'
 and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.

	  [COLOR="Blue"]
**Or is this Irrelevant?**
 => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d[/COLOR]
[COLOR="red"]
4> $make			
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2860sta[/COLOR]

```

---

### Post by wildmanne39 on 2011-08-05
Hi, if you run the commands I gave you it should get it working, do not worry about what the file says, you only needed to do this part from the file.

> HAS_WPA_SUPPLICANT=y

and also set
Code:
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Then run this command:
Code:

gksu gedit /etc/modprobe.d/blacklist.conf


So all the directions you need have been typed here in the thread for you.
Thank you

---

### Post by nego0 on 2011-08-08
> **wildmanne39 said:**
> Hi, if you run the commands I gave you it should get it working, do not worry about what the file says, you only needed to do this part from the file.


So all the directions you need have been typed here in the thread for you.
Thank you

Is there something i need to do with the file i downloaded
I'm always getting this code:
```
desmania@desmania-MS-7100:~/Downloads$ sudo make
make: *** No targets specified and no makefile found.  Stop.
```
doesn't mather where i download it to

---

### Post by wildmanne39 on 2011-08-08
Hi, give me a few minutes I am working on it.
Thank you

---

### Post by wildmanne39 on 2011-08-08
Hi, I just compiled it on my system.

After you cd ~Desktop do this cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217  and then run the make install commands.
Thank you

---

### Post by nego0 on 2011-08-08
> **wildmanne39 said:**
> Hi, I just compiled it on my system.

After you cd ~Desktop do this cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217  and then run the make install commands.
Thank you

Yeah it working finally!!!
Thnx man

Damn!! i restarted the pc and now its gone??
how do i save those settings?

---

### Post by wildmanne39 on 2011-08-08
Hi, ok we are almost there.

Do this please:
```
gksu gedit /etc/modules

```
Add rt3562sta.ko right under lp
rtc then save and close gedit and restart your computer.
Thank you

---

### Post by nego0 on 2011-08-08
> **wildmanne39 said:**
> Hi, ok we are almost there.

Do this please:
```
gksu gedit /etc/modules

```
Add rt3562sta.ko right under lp
rtc then save and close gedit and restart your computer.
Thank you

Ok so i did this 
code:```
gksu gedit /etc/modules
```
and then added the line:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt3562sta.ko
```
but i did that when i coulldn' t see any wireless connection
i then restarted again still didn't work

then i typed these codes:
```
sudo modprobe rt3562sta
sudo ifconfig ra0 inet up
```
and worked again.

so i did this again:```
gksu gedit /etc/modules
```
and saved should it work now?

No it doesn't!!

Now when i type this command:
```
gksu gedit /etc/modules
```
and saved the file the terminal shows me this:
```

desmania@desmania-MS-7100:~$ gksu gedit /etc/modules

(gedit:2152): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WB5YZV': No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.XRA3ZV': No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.SB74ZV': No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.S76F0V': No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Y7LA0V': No such file or directory

(gedit:2152): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

---

### Post by wildmanne39 on 2011-08-08
Hi, you may have other issue going on.

You only want that driver in the etc/modules once.

Please run this command.
```
lsmod | grep rt3
```
Thank you

---

### Post by nego0 on 2011-08-09
> **wildmanne39 said:**
> Hi, you may have other issue going on.

You only want that driver in the etc/modules once.

Please run this command.
```
lsmod | grep rt3
```
Thank you

I reinstalled ubuntu and went over it from the beginning
and now when i type this command:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
It show me this when i save the file:
```
desmania@desmania-MS-7100:~$ gksu gedit /etc/modprobe.d/blacklist.conf

(gedit:4075): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.PQ93ZV': No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.MD3D0V': No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.5K7C0V': No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NTUI0V': No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NLE9ZV': No such file or directory

(gedit:4075): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

``` I am gonna reinstall again and use a 32bit version





And it's the same with the 32 bit version
```
desmania@desmania-MS-7100:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for desmania: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
desmania@desmania-MS-7100:~$ gksu gedit /etc/modprobe.d/blacklist.conf

(gedit:1859): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.34PXZV': No such file or directory

(gedit:1859): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1859): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.09BB0V': No such file or directory

(gedit:1859): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
desmania@desmania-MS-7100:~$ 
```

---

### Post by chili555 on 2011-08-09
Please do:```
sudo mkdir -p /root/.local/share
```Now continue as wildmanne39 asks.

---

### Post by llukac on 2012-01-27
Hello,
 
from I can see I have the same problem. However I already can't find the driver used in the link you offered. Could you, please, propose an alternative one?
 
Thank you
 
Lucky
 
> **wildmanne39 said:**
> Hi, the driver you have installed is the wrong one, the link I gave you has the right one and the procedure to install it and blacklist the ones you have installed.
 
Unless josephmills as a different idea.
Thank you

---

### Post by Killer Klownz37 on 2012-02-22
I am also new to Linux, but I did do what you said to do here. Here is my output.

> *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: c8:2a:14:01:41:8a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=57765-v1.37 ip=192.168.1.45 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:a0600000-a0603fff

---

### Post by wildmanne39 on 2012-02-22
Hi Killer Klownz37, please refer to this link post 179.
[http://ubuntuforums.org/showthread.php?p=11710392#post11710392](http://ubuntuforums.org/showthread.php?p=11710392#post11710392)
Thanks

---

### Post by ptomulto on 2012-06-26
i had a problem with ubuntu 12.04  i typed rfkill lit  in terminal and it showed  blocked wifi soft blocked and hard blocked
i then typed rfkill unblock all and now im connected 
im not sure how that solved it my concerbin is how to make this permanent

---

### Post by wildmanne39 on 2012-06-26
Hi, it may stay unblocked if not post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
here by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

