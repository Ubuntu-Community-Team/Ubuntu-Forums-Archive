---
title: "Thinkpad X220 Intel 6205 wifi stability issue"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by plucesiar on 2012-01-12
Just got around to installing the newest Ubuntu 11.10 (via wubi), been having wifi connection issues with my Thinkpad X220 which uses the Intel Centrino 6205 wifi card.  I looked through the 2 threads ([http://ubuntuforums.org/showthread.php?t=1739047]("http://ubuntuforums.org/showthread.php?t=1739047") and [http://ubuntuforums.org/showthread.php?t=1752571]("http://ubuntuforums.org/showthread.php?t=1752571")) for help with this issue.  According to the posts there, I installed compat-wireless, but because I'm completely new to Ubuntu I might have butchered the installation process.  Right now, my wifi sometimes drops repeatedly everytime after reset (by using rmmod iwlagn and modprobe) so I'm wondering if I could get some help with the following diagnostics:

--------------------------------------------------

**Laptop model:**

```
Lenovo Thinkpad X220
```

**Ubuntu version:**

```
11.10
```

**Kernel/architecture:**

```
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```


**Wireless Brand, Model and Wireless Chipset:**

```
Intel Centrino Advanced-N 6205 (Wireless switch present and enabled... Windows runs it fine.)
```

**lspci:**
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
```


**ifconfig:**

```

eth0      Link encap:Ethernet  HWaddr f0:de:f1:72:c5:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:330021 (330.0 KB)  TX bytes:330021 (330.0 KB)

wlan0     Link encap:Ethernet  HWaddr a0:88:b4:9e:06:90  
          inet addr:18.189.123.188  Bcast:18.189.127.255  Mask:255.255.224.0
          inet6 addr: fe80::a288:b4ff:fe9e:690/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:565 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:295613 (295.6 KB)  TX bytes:101111 (101.1 KB)

```


**iwconfig:**

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Hidden Network"  
          Mode:Managed  Frequency:5.32 GHz  Access Point: 00:21:D8:49:AC:CB   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:112  Invalid misc:5   Missed beacon:0

```

**lsmod:**

```

Module                  Size  Used by
iwlagn                314213  0 
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75303  0 
qnx4                   17677  0 
hfsplus                88963  0 
hfs                    54782  0 
minix                  36322  0 
ntfs                  101885  0 
vfat                   17585  0 
msdos                  17332  0 
fat                    61475  2 vfat,msdos
jfs                   186662  0 
xfs                   831526  0 
reiserfs              248828  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
thinkpad_acpi          81819  0 
nvram                  14413  1 thinkpad_acpi
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
tpm_tis                18546  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              310872  1 iwlagn
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
mei                    41480  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
usbhid                 47198  0 
hid                    95463  1 usbhid
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  1 
libahci                26861  1 ahci
e1000e                160535  0 

```


**sudo lshw -C network**

```

  *-network
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:de:f1:72:c5:50
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:f2500000-f251ffff memory:f252b000-f252bfff ioport:5080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a0:88:b4:9e:06:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=17.168.5.2 build 35905 ip=18.189.123.188 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:f2400000-f2401fff

```

**iwlist scan:**

```

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:D8:49:AC:CB
                    Channel:64
                    Frequency:5.32 GHz (Channel 64)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Hidden Network"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000ae20a427213
                    Extra: Last beacon: 62608ms ago
                    IE: Unknown: 000C4D495420534543555245204E
                    IE: Unknown: 0107129824B048606C
                    IE: Unknown: 0B050400088D5B
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1640070500000000000000000000000000000000000000
                    IE: Unknown: 9606004096000B00
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401


```



**make (using compat-wireless-2012-01-09):**

```

make -C /lib/modules/3.0.0-12-generic/build M=/home/user_su/Desktop/compat-wireless-2012-01-09 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o
/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c: In function ‘iwl_trans_rx_alloc’:
/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:91:2: error: implicit declaration of function ‘dma_zalloc_coherent’ [-Werror=implicit-function-declaration]
/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:91:10: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:97:15: warning: assignment makes pointer from integer without a cast [enabled by default]
cc1: some warnings being treated as errors

make[4]: *** [/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o] Error 1
make[3]: *** [/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi] Error 2
make[2]: *** [/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/user_su/Desktop/compat-wireless-2012-01-09] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2

```


**sudo make install:**

```

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/wl1251/wl1251.ko
kernel/drivers/net/wireless/wl12xx/wl12xx.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Your old ethernet subsystem modules are left intact:

kernel/drivers/net/atlx/atl1.ko
kernel/drivers/net/atlx/atl2.ko
kernel/drivers/net/atl1e/atl1e.ko
kernel/drivers/net/atl1c/atl1c.ko

Your old bluetooth subsystem modules were left intact:

kernel/drivers/bluetooth/ath3k.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko

make -C /lib/modules/3.0.0-12-generic/build M=/home/user_su/Desktop/compat-wireless-2012-01-09 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o
/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c: In function ‘iwl_trans_rx_alloc’:
/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:91:2: error: implicit declaration of function ‘dma_zalloc_coherent’ [-Werror=implicit-function-declaration]
/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:91:10: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:97:15: warning: assignment makes pointer from integer without a cast [enabled by default]
cc1: some warnings being treated as errors

make[4]: *** [/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o] Error 1
make[3]: *** [/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless/iwlwifi] Error 2
make[2]: *** [/home/user_su/Desktop/compat-wireless-2012-01-09/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/user_su/Desktop/compat-wireless-2012-01-09] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2


```

[B]
sudo modprobe iwlagn
dmesg | grep iwl:[/B]

```

[   21.078295] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   21.078298] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   21.078353] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.078364] iwlagn 0000:03:00.0: setting latency timer to 64
[   21.078423] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   21.089008] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   21.089011] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   21.089013] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   21.090990] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   21.091086] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[   21.338403] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[   21.341029] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  855.260360] iwlagn 0000:03:00.0: PCI INT A disabled
[  855.300140] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  855.300144] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[  855.300216] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  855.300230] iwlagn 0000:03:00.0: setting latency timer to 64
[  855.300268] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[  855.310903] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[  855.310907] iwlagn 0000:03:00.0: Device SKU: 0Xb
[  855.310910] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[  855.311782] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  855.311877] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[  855.315526] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[  855.315833] ieee80211 phy1: Selected rate control algorithm 'iwl-agn-rs'
[ 1011.680393] iwlagn 0000:03:00.0: PCI INT A disabled
[ 1011.715099] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 1011.715108] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 1011.715220] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1011.715241] iwlagn 0000:03:00.0: setting latency timer to 64
[ 1011.715304] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 1011.726201] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 1011.726207] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 1011.726211] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 1011.726252] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 1011.726383] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 1011.728888] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 1011.729607] ieee80211 phy2: Selected rate control algorithm 'iwl-agn-rs'
[ 1049.551716] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 1433.651048] iwlagn 0000:03:00.0: PCI INT A disabled
[ 1433.684717] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 1433.684721] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 1433.684775] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1433.684788] iwlagn 0000:03:00.0: setting latency timer to 64
[ 1433.684822] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 1433.695389] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 1433.695391] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 1433.695392] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 1433.695413] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 1433.695500] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 1433.698677] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 1433.698978] ieee80211 phy3: Selected rate control algorithm 'iwl-agn-rs'
[ 2082.146672] iwlagn 0000:03:00.0: PCI INT A disabled
[ 2082.180425] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2082.180434] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 2082.180547] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2082.180568] iwlagn 0000:03:00.0: setting latency timer to 64
[ 2082.180630] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 2082.191583] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 2082.191589] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 2082.191593] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 2082.191655] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2082.191789] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 2082.198256] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 2082.198657] ieee80211 phy4: Selected rate control algorithm 'iwl-agn-rs'
[ 2117.491900] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 2292.047607] Modules linked in: iwlagn(-) bnep rfcomm bluetooth parport_pc ppdev lp parport snd_hda_codec_hdmi snd_hda_codec_conexant binfmt_misc joydev arc4 uvcvideo videodev v4l2_compat_ioctl32 thinkpad_acpi nvram snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi tpm_tis psmouse serio_raw mac80211 snd_seq_midi_event snd_seq snd_timer snd_seq_device snd wmi soundcore snd_page_alloc cfg80211 i915 drm_kms_helper drm mei(C) i2c_algo_bit video usbhid hid sdhci_pci sdhci ahci libahci e1000e [last unloaded: iwlagn]
[ 2293.465019] iwlagn 0000:03:00.0: PCI INT A disabled
[ 2293.544213] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2293.544224] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 2293.544366] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2293.544391] iwlagn 0000:03:00.0: setting latency timer to 64
[ 2293.544463] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 2293.555503] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 2293.555510] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 2293.555515] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 2293.555581] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2293.555710] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 2293.562242] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 2293.563663] ieee80211 phy5: Selected rate control algorithm 'iwl-agn-rs'
[ 2345.857335] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 2356.092160] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 10
[ 2362.743041] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 2400.308807] iwlagn 0000:03:00.0: Stopping AGG while state not ON or starting
[ 2442.663811] iwlagn 0000:03:00.0: PCI INT A disabled
[ 2442.696260] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2442.696263] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 2442.696324] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2442.696338] iwlagn 0000:03:00.0: setting latency timer to 64
[ 2442.696370] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 2442.707034] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 2442.707038] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 2442.707040] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 2442.707072] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2442.707165] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 2442.709400] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 2442.709939] ieee80211 phy6: Selected rate control algorithm 'iwl-agn-rs'
[ 2483.739153] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 2784.088345] iwlagn 0000:03:00.0: PCI INT A disabled
[ 2784.123808] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2784.123811] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 2784.123861] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2784.123874] iwlagn 0000:03:00.0: setting latency timer to 64
[ 2784.123904] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 2784.134461] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 2784.134463] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 2784.134464] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 2784.134485] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2784.134572] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 2784.136582] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 2784.138412] ieee80211 phy7: Selected rate control algorithm 'iwl-agn-rs'
[ 2821.656126] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 2836.498663] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 2877.936174] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 9
[ 3088.193066] iwlagn 0000:03:00.0: PCI INT A disabled
[ 3088.235528] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 3088.235531] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 3088.235597] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3088.235611] iwlagn 0000:03:00.0: setting latency timer to 64
[ 3088.235647] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 3088.246220] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 3088.246224] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 3088.246225] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 3088.246254] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 3088.246348] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 3088.248563] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 3088.249425] ieee80211 phy8: Selected rate control algorithm 'iwl-agn-rs'
[ 3135.789633] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 7
[ 3138.918437] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 3167.968763] iwlagn 0000:03:00.0: PCI INT A disabled
[ 3168.003199] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 3168.003209] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 3168.003350] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3168.003375] iwlagn 0000:03:00.0: setting latency timer to 64
[ 3168.003443] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 3168.014489] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 3168.014496] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 3168.014501] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 3168.014568] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 3168.014691] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 3168.020350] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 3168.021536] ieee80211 phy9: Selected rate control algorithm 'iwl-agn-rs'
[ 3236.182275] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 3264.520485] iwlagn 0000:03:00.0: Stopping AGG while state not ON or starting
[ 3273.807979] iwlagn 0000:03:00.0: PCI INT A disabled
[ 3273.853731] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 3273.853742] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 3273.853889] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3273.853913] iwlagn 0000:03:00.0: setting latency timer to 64
[ 3273.853979] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 3273.864989] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 3273.864996] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 3273.865000] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 3273.865067] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 3273.865190] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 3273.868080] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 3273.868481] ieee80211 phy10: Selected rate control algorithm 'iwl-agn-rs'
[ 3320.221505] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 3815.737755] iwlagn 0000:03:00.0: PCI INT A disabled
[ 3815.758867] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 3815.758871] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 3815.759119] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3815.759133] iwlagn 0000:03:00.0: setting latency timer to 64
[ 3815.759172] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 3815.769816] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 3815.769820] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 3815.769822] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 3815.769849] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 3815.769942] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 3815.774087] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 3815.775400] ieee80211 phy11: Selected rate control algorithm 'iwl-agn-rs'
[ 3832.174554] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cc tid = 0
[ 3892.885634] iwlagn 0000:03:00.0: PCI INT A disabled
[ 3892.931760] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 3892.931768] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 3892.931880] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3892.931901] iwlagn 0000:03:00.0: setting latency timer to 64
[ 3892.931964] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[ 3892.942947] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[ 3892.942955] iwlagn 0000:03:00.0: Device SKU: 0Xb
[ 3892.942959] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[ 3892.943017] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 3892.943146] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[ 3892.948749] iwlagn 0000:03:00.0: loaded firmware version 17.168.5.2 build 35905
[ 3892.950132] ieee80211 phy12: Selected rate control algorithm 'iwl-agn-rs'
[ 4093.761267] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cb tid = 0
[ 4103.027397] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 3
[ 4150.033844] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 1
[ 4183.233603] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[ 4245.701211] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:21:d8:49:ac:cb tid = 0
[ 5095.201349] iwlagn 0000:03:00.0: Stopping AGG while state not ON or starting

```



**modinfo iwlagn:**
```

filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-5.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-105-5.ucode
firmware:       iwlwifi-2030-5.ucode
firmware:       iwlwifi-2000-5.ucode
srcversion:     F1AF2D897D96C14B77FE0BA
alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000266bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000066bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000426bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000226bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000026bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004466bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004266bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004066bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004464bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004264bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004064bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004466bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004066bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004426bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004226bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004026bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        mac80211,cfg80211
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (bool)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Disable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)

```



**ll /lib/firmware/iwl* :**

```

-rw-r--r-- 1 root root 335056 2011-08-23 09:22 /lib/firmware/iwlwifi-1000-3.ucode
-rw-r--r-- 1 root root 337520 2011-08-23 09:23 /lib/firmware/iwlwifi-1000-5.ucode
-rw-r--r-- 1 root root 337572 2011-08-23 09:23 /lib/firmware/iwlwifi-100-5.ucode
-rw-r--r-- 1 root root 150100 2011-08-23 09:22 /lib/firmware/iwlwifi-3945-2.ucode
-rw-r--r-- 1 root root 187972 2011-08-23 09:22 /lib/firmware/iwlwifi-4965-2.ucode
-rw-r--r-- 1 root root 345008 2011-08-23 09:22 /lib/firmware/iwlwifi-5000-1.ucode
-rw-r--r-- 1 root root 353240 2011-08-23 09:22 /lib/firmware/iwlwifi-5000-2.ucode
-rw-r--r-- 1 root root 340696 2011-08-23 09:23 /lib/firmware/iwlwifi-5000-5.ucode
-rw-r--r-- 1 root root 337400 2011-08-23 09:22 /lib/firmware/iwlwifi-5150-2.ucode
-rw-r--r-- 1 root root 454608 2011-08-23 09:23 /lib/firmware/iwlwifi-6000-4.ucode
-rw-r--r-- 1 root root 444128 2012-01-11 23:21 /lib/firmware/iwlwifi-6000g2a-5.ucode
-rw-r--r-- 1 root root 460236 2011-08-23 09:23 /lib/firmware/iwlwifi-6000g2b-5.ucode
-rw-r--r-- 1 root root 463692 2011-08-23 09:22 /lib/firmware/iwlwifi-6050-4.ucode
-rw-r--r-- 1 root root 469780 2011-08-23 09:23 /lib/firmware/iwlwifi-6050-5.ucode

```

---

### Post by vacaloca on 2012-01-13
I'm across the river (NU) and also have issues with WPA2 Enterprise. No issues under Windoze, or with other non-enterprise WPA networks in Linux. I've seen various other posters with this same 6205 card, and it definitely looks to be an iwlagn and/or kernel issue. In my case it looks very similar to this:

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/183754](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/183754)

I get it to connect VERY infrequently. I'm on kernel 3.0.0-14. I'm calibrating the battery on my AS4830TG-6450 -- machine is shut off at the moment, but I'll post again w/ my own debug info in the morning, and I'll try compat-wireless eventually, but I won't be back at school 'til next week or so.

---

### Post by plucesiar on 2012-01-13
> **vacaloca said:**
> I'm across the river (NU) and also have issues with WPA2 Enterprise. No issues under Windoze, or with other non-enterprise WPA networks in Linux. I've seen various other posters with this same 6205 card, and it definitely looks to be an iwlagn and/or kernel issue. In my case it looks very similar to this:

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/183754](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/183754)

I get it to connect VERY infrequently. I'm on kernel 3.0.0-14. I'm calibrating the battery on my AS4830TG-6450 -- machine is shut off at the moment, but I'll post again w/ my own debug info in the morning, and I'll try compat-wireless eventually, but I won't be back at school 'til next week or so.


Hey, my issue seems to be exactly as that thread describes... I literally got 20+ identical windows asking for my wifi password when I left my laptop on for a few hours.  Sometimes even when it says I'm connected, I'm really not.  So I had to resort to resetting the wifi or just boot into Windows.

---

### Post by vacaloca on 2012-01-17
> **plucesiar said:**
> Hey, my issue seems to be exactly as that thread describes... I literally got 20+ identical windows asking for my wifi password when I left my laptop on for a few hours.  Sometimes even when it says I'm connected, I'm really not.  So I had to resort to resetting the wifi or just boot into Windows.

I had started to fiddle with compat-wireless, but all it did when I installed it was completely bork my wireless connection, so I uninstalled it and tried the option that worked below.

Interestingly enough, the router that is broadcasting the WPA PEAP secure connection here on campus at NU also broadcasts the guest one, and I had the issue of not being able to connect to both of them until I tried to replace the ucode for the wireless card. The APs at home, elsewhere, and even my 4G connection as a mobile hotspot had no issues connecting, however.

So yes, I think I have a fix for you and possibly all the others people that have Wifi disconnection or connection issues with the Intel Centrino 6205 card (and possibly other variants). It seems that whatever version of the microcode (ucode) that was shipped w/ Ubuntu 11.10 (and possibly earlier versions?) is horribly buggy.

Solution:

Download the microcode for the 6205 (or any other affected card) here:
[http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)

Copy it replacing the original version (usually in /lib/firmware). Make a backup of old version ideally. I would've made a backup, but I copied it on top of the original, haha. 

Next, either reboot computer, or turn off wireless and then:
```

sudo modprobe iwlagn

```
and try reconnecting.

This worked for me, so I'm happy.

Also, I saw mention of turning off power management for other problematic cards via:

```

sudo iwconfig wlan0 power off # turns pwr mgmt off
sudo iwconfig wlan0 power on  # turns pwr mgmt on

```

For me, this setting made no difference.

Since doing the fix, I have been able to connect on the first try everytime, even after rebooting, and posted this reply over the WPA Enterprise connection.

---

As an aside to the original poster, I was actually at MIT today, I'm taking this year's version of this class: [http://www.ll.mit.edu/news/iapradarcourse.html](http://www.ll.mit.edu/news/iapradarcourse.html)
Pretty neat stuff!

---

