---
title: "Lost wireless driver!"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by RazeRules on 2012-06-23
Hi,
I'm an Ubuntu newbie but I couldn't wait to get some experience to install Aircrack-ng. I was in the stage of patching drivers for my wireless adapter using this guide [http://www.aircrack-ng.org/doku.php?id=iwlagn](http://www.aircrack-ng.org/doku.php?id=iwlagn) when I lost my driver:
```
cd ~
 tar xjf compat-wireless-2.6.tar.bz2
 cd compat-wireless-2009-*
 wget http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
 patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
 wget http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
 patch -p1 < mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
 make -j4
 make unload [as root!]
 make install [as root!]
 echo options iwlagn swcrypto=1 >> /etc/modprobe.d/options [as root!]
 make load [as root!]
```
I've spent 2 days searching the forum for similar issues and I tried a lot of stuff such as ndiswrapper to use the windows driver which turns out to be "invalid", also I tried madwifi mofo but I couldn't enable it.

Any ideas will be very appreciated, Thanks in advance.

Here's the wireless ticket information as required by the forum rules:

**1 ) Machine Brand and Model (PC/Laptop):**
Lenovo ThinkPad R61 (8933B51)

**2 ) Wireless Brand, Model and Wireless Chipset:**
$ lspci
```
raze@Raze-Station-U:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

```
$ lsusb
```
raze@Raze-Station-U:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 17ef:1004 Lenovo Integrated Webcam
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller

```
$ lspci -nn | grep 'Wireless Brand'
```
returns nothing.
```

**3 ) check interface:**
$ ifconfig
```
raze@Raze-Station-U:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d8:5f:33  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:37ff:fed8:5f33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6217983 (6.2 MB)  TX bytes:1385157 (1.3 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480434 (480.4 KB)  TX bytes:480434 (480.4 KB)

```
$ iwconfig
```
raze@Raze-Station-U:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
$ iwconfig wlan0
```
raze@Raze-Station-U:~$ iwconfig wlan0
wlan0     No such device

```

**4 ) Check for modules:**
$ lsmod
```
raze@Raze-Station-U:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
snd_hda_codec_conexant    52516  1 
parport_pc             32114  0 
ppdev                  12849  0 
pcmcia                 39791  0 
binfmt_misc            17292  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
thinkpad_acpi          73942  0 
r592                   17808  0 
psmouse                72919  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mtd                    35584  2 sm_common,nand
memstick               15857  1 r592
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nvram                  14029  1 thinkpad_acpi
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
nand_ecc               13070  1 nand
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
tpm_tis                18308  0 
i915                  414663  3 
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
tg3                   141369  0 

```
$ lsmod | grep "wlan_module_name"
```
returns nothing.
```

**5 ) Kernel boot messages**
$ dmesg | grep "wlan_module_name"
```
returns nothing
```

**6 ) Network configuration**
$ sudo lshw -C network
```
raze@Raze-Station-U:~$ sudo lshw -C network
[sudo] password for raze: 
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:df6fe000-df6fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:37:d8:5f:33
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb v2.11 ip=192.168.1.8 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fe000000-fe00ffff

```

**7 ) Scan for networks:**
$ iwlist scan
```
raze@Raze-Station-U:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```
$ iwlist scan wlan0
```
raze@Raze-Station-U:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
```

**8 ) Ubuntu Version:**
$ lsb_release -d
```
raze@Raze-Station-U:~$ lsb_release -d
Description:	Ubuntu 12.04 LTS

```

**9 ) Kernel/architecture (including 32 vs. 64 bit):**
$ uname -mr
```
raze@Raze-Station-U:~$ uname -mr
3.2.0-25-generic-pae i686

```

**10 ) Restarting the network:**
$ sudo /etc/init.d/networking restart
```
raze@Raze-Station-U:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
```

---

### Post by chili555 on 2012-06-23
> cd ~
 tar xjf compat-wireless-2.6.tar.bz2
 cd compat-wireless-2009-*
 wget [http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch)
 patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
 wget [http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch](http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch)
 patch -p1 < mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
 make -j4
 make unload [as root!]
 make install [as root!]
 echo options iwlagn swcrypto=1 >> /etc/modprobe.d/options [as root!]
 make load [as root!]When you went through this process, did you encounter any errors? What? Where?

The module is called iwlwifi in 12.04, not iwlagn. We need to see how far you got before we can proceed further.

DISCLAIMER: I know nothing about aircrack and won't support it. I can and will get your driver working.

---

### Post by CharlesA on 2012-06-23
We don't support aircrack here.

---

