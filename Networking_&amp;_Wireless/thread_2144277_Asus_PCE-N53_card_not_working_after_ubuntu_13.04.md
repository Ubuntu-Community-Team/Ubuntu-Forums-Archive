---
title: "Asus PCE-N53 card not working after ubuntu 13.04"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by liutszho on 2013-05-11
Recently came from Ubuntu 12.04 where my wifi card Asus PCE-N53 was working fine.

Now after installing 13.04 it no longer works.

Before, I had to install by doing "make" and "sudo make install" and that worked.

However, I am now getting this error in 13.04:

```
make -C /home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
mkdir: cannot create directory ‘/etc/Wireless’: File exists
make[1]: Entering directory `/home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install: cannot stat ‘rt5592sta.ko’: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
make: *** [install] Error 2
```


Here is my terminal outputs for my system info etc:

```
liutszho@liutszho-desktop:~$ uname -a
Linux liutszho-desktop 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:36:13 UTC 2013 i686 athlon i686 GNU/Linux
liutszho@liutszho-desktop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
    Subsystem: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
    Kernel driver in use: pcieport
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604]
    Kernel driver in use: pcieport
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
    Kernel driver in use: pcieport
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
    Kernel driver in use: pcieport
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40)
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 42)
    Kernel driver in use: piix4_smbus
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
    Kernel driver in use: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Jetway Information Co., Ltd. Device [16f3:888f]
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Kernel driver in use: ohci_hcd
00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
    Kernel driver in use: pcieport
00:15.1 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
    Kernel driver in use: pcieport
00:15.2 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
    Kernel driver in use: pcieport
00:15.3 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3]
    Kernel driver in use: pcieport
00:16.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:16.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Cayman PRO [Radeon HD 6950] [1002:6719]
    Subsystem: XFX Pine Group Inc. Device [1682:3127]
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series] [1002:aa80]
    Subsystem: XFX Pine Group Inc. Device [1682:aa80]
    Kernel driver in use: snd_hda_intel
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Ralink corp. Device [1814:5592]
    Subsystem: ASUSTeK Computer Inc. Device [1043:851a]
04:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
    Kernel driver in use: xhci_hcd
06:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
    Subsystem: JMicron Technology Corp. Device [197b:2363]
    Kernel driver in use: pata_jmicron
liutszho@liutszho-desktop:~$ lsusb
Bus 002 Device 006: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 004 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 005 Device 002: ID 1532:001f Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
liutszho@liutszho-desktop:~$ lsmod
Module                  Size  Used by
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
arc4                   12543  2 
rtl8192cu              66659  0 
rtlwifi                69015  1 rtl8192cu
rtl8192c_common        47075  1 rtl8192cu
mac80211              526519  3 rtlwifi,rtl8192c_common,rtl8192cu
joydev                 17097  0 
cfg80211              436177  2 mac80211,rtlwifi
snd_hda_codec_hdmi     36185  1 
radeon                870822  3 
kvm_amd                50336  0 
kvm                   376505  1 kvm_amd
snd_hda_codec_realtek    63791  1 
ttm                    71289  1 radeon
drm_kms_helper         47545  1 radeon
snd_seq_midi           13132  0 
ppdev                  12817  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_intel          38307  6 
drm                   228750  5 ttm,drm_kms_helper,radeon
parport_pc             27504  1 
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
k10temp                12958  0 
snd_rawmidi            25114  1 snd_seq_midi
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
i2c_algo_bit           13197  1 radeon
mac_hid                13037  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
psmouse                81038  0 
serio_raw              13031  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
sp5100_tco             13447  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
i2c_piix4              13066  0 
microcode              18286  0 
snd                    56485  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
soundcore              12600  1 snd
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
pata_acpi              12886  0 
pata_jmicron           12662  0 
pata_atiixp            13058  0 
r8169                  61531  0 
ahci                   25507  2 
libahci                26108  1 ahci
liutszho@liutszho-desktop:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"Larry Lisu"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 10:9A:DD:86:56:9B   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

liutszho@liutszho-desktop:~$ rfkill list
3: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Thanks!

---

### Post by liutszho on 2013-05-14
Went back to 12.04 for now. Hope there is a solution.


> **liutszho said:**
> Recently came from Ubuntu 12.04 where my wifi card Asus PCE-N53 was working fine.

Now after installing 13.04 it no longer works.

Before, I had to install by doing "make" and "sudo make install" and that worked.

However, I am now getting this error in 13.04:

```
make -C /home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
mkdir: cannot create directory ‘/etc/Wireless’: File exists
make[1]: Entering directory `/home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install: cannot stat ‘rt5592sta.ko’: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
make: *** [install] Error 2
```


Here is my terminal outputs for my system info etc:

```
liutszho@liutszho-desktop:~$ uname -a
Linux liutszho-desktop 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:36:13 UTC 2013 i686 athlon i686 GNU/Linux
liutszho@liutszho-desktop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
    Subsystem: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
    Kernel driver in use: pcieport
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604]
    Kernel driver in use: pcieport
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
    Kernel driver in use: pcieport
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
    Kernel driver in use: pcieport
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40)
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 42)
    Kernel driver in use: piix4_smbus
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
    Kernel driver in use: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Jetway Information Co., Ltd. Device [16f3:888f]
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Kernel driver in use: ohci_hcd
00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
    Kernel driver in use: pcieport
00:15.1 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
    Kernel driver in use: pcieport
00:15.2 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
    Kernel driver in use: pcieport
00:15.3 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3]
    Kernel driver in use: pcieport
00:16.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:16.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Cayman PRO [Radeon HD 6950] [1002:6719]
    Subsystem: XFX Pine Group Inc. Device [1682:3127]
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series] [1002:aa80]
    Subsystem: XFX Pine Group Inc. Device [1682:aa80]
    Kernel driver in use: snd_hda_intel
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Ralink corp. Device [1814:5592]
    Subsystem: ASUSTeK Computer Inc. Device [1043:851a]
04:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
    Kernel driver in use: xhci_hcd
06:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
    Subsystem: JMicron Technology Corp. Device [197b:2363]
    Kernel driver in use: pata_jmicron
liutszho@liutszho-desktop:~$ lsusb
Bus 002 Device 006: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 004 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 005 Device 002: ID 1532:001f Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
liutszho@liutszho-desktop:~$ lsmod
Module                  Size  Used by
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
arc4                   12543  2 
rtl8192cu              66659  0 
rtlwifi                69015  1 rtl8192cu
rtl8192c_common        47075  1 rtl8192cu
mac80211              526519  3 rtlwifi,rtl8192c_common,rtl8192cu
joydev                 17097  0 
cfg80211              436177  2 mac80211,rtlwifi
snd_hda_codec_hdmi     36185  1 
radeon                870822  3 
kvm_amd                50336  0 
kvm                   376505  1 kvm_amd
snd_hda_codec_realtek    63791  1 
ttm                    71289  1 radeon
drm_kms_helper         47545  1 radeon
snd_seq_midi           13132  0 
ppdev                  12817  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_intel          38307  6 
drm                   228750  5 ttm,drm_kms_helper,radeon
parport_pc             27504  1 
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
k10temp                12958  0 
snd_rawmidi            25114  1 snd_seq_midi
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
i2c_algo_bit           13197  1 radeon
mac_hid                13037  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
psmouse                81038  0 
serio_raw              13031  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
sp5100_tco             13447  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
i2c_piix4              13066  0 
microcode              18286  0 
snd                    56485  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
soundcore              12600  1 snd
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
pata_acpi              12886  0 
pata_jmicron           12662  0 
pata_atiixp            13058  0 
r8169                  61531  0 
ahci                   25507  2 
libahci                26108  1 ahci
liutszho@liutszho-desktop:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"Larry Lisu"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 10:9A:DD:86:56:9B   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

liutszho@liutszho-desktop:~$ rfkill list
3: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Thanks!

---

### Post by splinter701 on 2013-06-14
I'm having the same isssue. I also get that error when trying to 'make install'.
I hope someone knows something about this.

---

