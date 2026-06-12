---
title: "Cant connect wifi (Centrino Wireless-1000)"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by Aerozy on 2013-01-08
I'm a really noob, in this linux world, but i want to try it.

The problem I am having is with my Toshiba Satellite L655-S5117 - Laptop. Windows 7 works fine. My distro flawless except wireless wont work. Can detects a wireless card, but can't use it(connect). Here are the specs.


sudo lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

```

rfkill list all:

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

dmesg | grep iwl

```
[   12.992199] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.992203] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   12.992362] iwlwifi 0000:02:00.0: >pci_resource_len = 0x00002000
[   12.992365] iwlwifi 0000:02:00.0: >pci_resource_base = ffffc90011098000
[   12.992367] iwlwifi 0000:02:00.0: >HW Revision ID = 0x0
[   12.992635] iwlwifi 0000:02:00.0: >irq 43 for MSI/MSI-X
[   13.050293] iwlwifi 0000:02:00.0: >loaded firmware version 39.31.5.1 build 35138
[   13.050463] iwlwifi 0000:02:00.0: >CONFIG_IWLWIFI_DEBUG disabled
[   13.050466] iwlwifi 0000:02:00.0: >CONFIG_IWLWIFI_DEBUGFS enabled
[   13.050468] iwlwifi 0000:02:00.0: >CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   13.050470] iwlwifi 0000:02:00.0: >CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   13.050472] iwlwifi 0000:02:00.0: >CONFIG_IWLWIFI_P2P disabled
[   13.050476] iwlwifi 0000:02:00.0: >Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   13.050618] iwlwifi 0000:02:00.0: >L1 Enabled; Disabling L0S
[   13.072387] iwlwifi 0000:02:00.0: >device EEPROM VER=0x15d, CALIB=0x6
[   13.072391] iwlwifi 0000:02:00.0: >Device SKU: 0x50
[   13.072393] iwlwifi 0000:02:00.0: >Valid Tx ant: 0x1, Valid Rx ant: 0x3
[   13.072405] iwlwifi 0000:02:00.0: >Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.330375] ieee80211 phy0: >Selected rate control algorithm 'iwl-agn-rs'
[   19.769697] iwlwifi 0000:02:00.0: >L1 Enabled; Disabling L0S
[   19.835056] iwlwifi 0000:02:00.0: >L1 Enabled; Disabling L0S
[ 1129.794475] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 1138.762458] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 1142.055067] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 1313.888013] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 1322.857063] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 1326.156980] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 1335.126037] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 1689.453271] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 1704.092062] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2025.557833] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2028.856120] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2032.154410] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2035.440763] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2040.140594] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2043.435011] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2350.305854] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2353.588211] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2356.882531] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2365.843052] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2369.145384] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2794.531937] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 2803.500457] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 3128.971327] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 3137.947816] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 3141.238205] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 3150.214687] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 3463.390861] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues
[ 3478.029529] iwlwifi 0000:02:00.0: >fail to flush all tx fifo queues

```

---

### Post by Bucky Ball on 2013-01-08
Welcome to the forums.

Now, the output of

```

sudo lshw -C network
```Thanks. Your problem could relate to wireless N. Have you tried disabling it?

---

### Post by Aerozy on 2013-01-08
sudo lshw -C network

```
PCI (sysfs)  
  *-network               
       descripción: Interfaz inalámbrica
       producto: Centrino Wireless-N 1000
       fabricante: Intel Corporation
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: wlan0
       versión: 00
       serie: 00:26:c7:ad:89:ec
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=iwlwifi driverversion=3.5.0-17-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       recursos: irq:43 memoria:d4400000-d4401fff
  *-network
       descripción: Ethernet interface
       producto: AR8152 v1.1 Fast Ethernet
       fabricante: Atheros Communications Inc.
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: eth0
       versión: c1
       serie: 60:eb:69:71:96:7b
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       recursos: irq:45 memoria:d3400000-d343ffff ioport:2000(size=128)
  *-network
       descripción: Interfaz inalámbrica
       id físico: 3
       información del bus: usb@1:1.2
       nombre lógico: wlan1
       serie: 74:ea:3a:87:fe:63
       capacidades: ethernet physical wireless
       configuración: broadcast=yes driver=rt2800usb driverversion=3.5.0-17-generic firmware=0.29 ip=192.168.1.71 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by Us3r Unfriendly on 2013-01-08
Please can you give us the output of:   lsmod   and   lspci -k

---

### Post by Aerozy on 2013-01-08
lsmod

```
Module                  Size  Used by
btrfs                 761721  0 
zlib_deflate           26914  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    74821  0 
qnx4                   13317  0 
hfsplus                84442  0 
hfs                    54553  0 
minix                  36058  0 
ntfs                   97304  0 
msdos                  17332  0 
jfs                   181093  0 
xfs                   837979  0 
reiserfs              246392  0 
ext2                   72880  0 
nls_iso8859_1          12713  0 
dm_crypt               23011  1 
bnep                   18140  2 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
arc4                   12529  4 
rt2800usb              22661  0 
rt2800lib              58685  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
snd_hda_codec_conexant    57842  1 
rt2x00usb              20618  1 rt2800usb
snd_hda_intel          33491  5 
iwlwifi               386826  0 
joydev                 17457  0 
snd_hda_codec         134212  2 snd_hda_codec_conexant,snd_hda_intel
rt2x00lib              54891  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              539908  4 rt2800lib,rt2x00usb,iwlwifi,rt2x00lib
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               76749  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
videobuf2_core         32851  1 uvcvideo
snd_timer              29425  2 snd_pcm,snd_seq
videodev              120309  2 uvcvideo,videobuf2_core
cfg80211              206566  3 iwlwifi,rt2x00lib,mac80211
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
coretemp               13400  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
psmouse                95552  0 
snd                    78734  18 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15047  1 snd
microcode              22803  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
toshiba_acpi           18726  0 
intel_ips              18049  0 
serio_raw              13215  0 
mei                    40690  0 
mac_hid                13205  0 
lpc_ich                17061  0 
sparse_keymap          13890  1 toshiba_acpi
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
ums_realtek            17949  0 
uas                    17844  0 
usb_storage            48838  1 ums_realtek
wmi                    19070  1 toshiba_acpi
i915                  520519  8 
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
video                  19335  1 i915
atl1c                  41101  0
``` 

lspci -k

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel modules: lpc_ich
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: intel ips
	Kernel modules: intel_ips
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
03:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Toshiba America Info Systems Device fd50
	Kernel driver in use: atl1c
	Kernel modules: atl1c
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Toshiba America Info Systems Device fd50
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Toshiba America Info Systems Device fd50
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Toshiba America Info Systems Device fd50
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Toshiba America Info Systems Device fd50
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Toshiba America Info Systems Device fd50
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Toshiba America Info Systems Device fd50

```

---

### Post by Bucky Ball on 2013-01-08
Hmm. What release are you using?

---

### Post by Us3r Unfriendly on 2013-01-08
You have 2 drivers running at the same time...might be conflicting with eachother possibly.  Looks like you need the  "iwlwifi" module.  Have you tried removing the other?

sudo modprobe -r rt2800usb

Then removing the other and inserting it back in?

sudo modprobe -r iwlwifi

sudo modprobe iwlwifi

then try again to connect using network manager

---

### Post by chili555 on 2013-01-08
Is rt2800pci loading because of a declaration in /etc/modules?```
gksudo gedit /etc/modules
```If rt2800pci or any other rt2x00s are in there, remove them. Proofread, save and close gedit.

Now in a terminal, do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```If this helps you connect, we can write one file and make it permanent.

---

### Post by Aerozy on 2013-01-08
> **Us3r Unfriendly said:**
> You have 2 drivers running at the same time...might be conflicting with eachother possibly.  Looks like you need the  "iwlwifi" module.  Have you tried removing the other?

sudo modprobe -r rt2800usb

Then removing the other and inserting it back in?

sudo modprobe -r iwlwifi

sudo modprobe iwlwifi

then try again to connect using network manager

I guess i'm running 2 drivers because im using a wireless usb adapter, the only way to connect right now.

> Is rt2800pci loading because of a declaration in /etc/modules?

Im not sure, maybe is the driver of wireless usb adapter. 
I'll restart the laptop to use gedit. I'll post the result 2-3 min.

---

### Post by chili555 on 2013-01-08
I suggest you remove the USB and then try these commands:```
sudo modprobe -r rt2800usb
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```Then tell us if you are able to connect with the internal device only.

---

### Post by Aerozy on 2013-01-08
> **chili555 said:**
> I suggest you remove the USB and then try these commands:```
sudo modprobe -r rt2800usb
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```Then tell us if you are able to connect with the internal device only.

Woow, it works now!. Now I can connect without USB.

Is this is required every reboot?
What are the CONSEQUENCES of disabling 11n?

---

### Post by chili555 on 2013-01-08
The consequence is that you won't be able to get N speeds. Hopefully, you are not streaming Blu-Ray over your network to a laptop.

It will not be required on every boot if you write one file:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```A new empty file will open. Type in one line:```
options 11n_disable=1 bt_coex_active=N
```Proofread, save and close gedit.

Please use thread tools to mark Solved.

---

### Post by praseodym on 2013-01-08
Now you can make it permanent:
```

echo "options iwlwifi 11n_disable=1 bt_coex_active=N" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

Edit: Seconds too slow ;-)

---

### Post by Aerozy on 2013-01-08
> **chili555 said:**
> The consequence is that you won't be able to get N speeds. Hopefully, you are not streaming Blu-Ray over your network to a laptop.

It will not be required on every boot if you write one file:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```A new empty file will open. Type in one line:```
options 11n_disable=1 bt_coex_active=N
```Proofread, save and close gedit.

Please use thread tools to mark Solved.

> **praseodym said:**
> Now you can make it permanent:
```

echo "options iwlwifi 11n_disable=1 bt_coex_active=N" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

Edit: Seconds too slow ;-)

Thank you guys, i really apreciate your help.
Solved!

---

### Post by xastey on 2013-02-08
> **Us3r Unfriendly said:**
> You have 2 drivers running at the same time...might be conflicting with eachother possibly.  Looks like you need the  "iwlwifi" module.  Have you tried removing the other?

sudo modprobe -r rt2800usb

Then removing the other and inserting it back in?

sudo modprobe -r iwlwifi

sudo modprobe iwlwifi

then try again to connect using network manager

Thank you very much, this fixed my Toshiba P855 I just purchased, had to adapt which driver I removed but worked. THANKS

---

