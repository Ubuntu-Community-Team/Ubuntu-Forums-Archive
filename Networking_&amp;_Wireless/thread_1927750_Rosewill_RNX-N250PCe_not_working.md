---
title: "Rosewill RNX-N250PCe not working"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by codythetech on 2012-02-18
I can't get my wireless network card to work, i've tried a few different things and i just can't get it. Please help me. 
lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8178 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```ifconfig just shows eth0 and lo
```
iwconfig lo        no wireless extensions.

eth0      no wireless extensions
```.

lsmod:
```
Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_via      33207  1 
ppdev                   6375  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nvidia              10832442  32 
rt2860sta             903536  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
i2c_piix4               9639  0 
psmouse                65040  0 
serio_raw               4918  0 
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              45423  0 
edac_mce_amd            9278  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
ahci                   38350  2 
r8169                  39714  0 
pata_atiixp             4209  0 
mii                     5237  1 r8169
```sudo lshw -C network

```
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:d800(size=256) memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:19:66:cc:5d:00
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.26 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e800(size=256) memory:fbfff000-fbffffff(prefetchable) memory:fbff8000-fbffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)
```lsb_release -d
```
Description:    Ubuntu 10.04.4 LTS
```uname -mr
```
2.6.32-38-generic x86_64
```sudo /etc/init.d/networking restart
```
[sudo] password for xbmc: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
```

---

### Post by praseodym on 2012-02-18
Well, there are two Realtek-devices shown (LAN and WLAN). Which one are you talking about? Additionally, there is a Ralink driver loaded (rt2860sta). Did you install it?

Please show

```
lspci -nnk | grep -iA2 net
```
Does one of these work?

---

### Post by codythetech on 2012-02-19
Sorry, I want my wireless to work. The wired is built in to my motherboard and works just fine.

lspci -nnk | grep -iA2 net
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8178] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Kernel driver in use: r8169
    Kernel modules: r8169
```

---

### Post by codythetech on 2012-02-19
and yes, i installed that driver by mistake. i was following a guide i saw to fix wireless that i thought was my card.

on the box, it states that the chipset is rtl8192ce

---

### Post by praseodym on 2012-02-19
For this device you need this driver:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/27/36/2844083-rtl8192ce_dkms_2.6.0006.0321.tar.gz
sudo tar xvf 2844083-rtl8192ce_dkms_2.6.0006.0321.tar.gz -C /usr/src

sudo dkms add -m rtl8192ce -v 2.6.0006.0321
sudo dkms build -m rtl8192ce -v 2.6.0006.0321
sudo dkms install -m rtl8192ce -v 2.6.0006.0321 
```
Blacklist the wrong Ralink driver:

```
echo "blacklist rt2860sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot. You should copy/paste these lines one by another.

---

### Post by codythetech on 2012-02-19
and it worked! thank you very much! you're a life saver!

---

