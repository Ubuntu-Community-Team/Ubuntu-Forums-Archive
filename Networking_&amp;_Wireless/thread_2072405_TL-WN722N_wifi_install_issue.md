---
title: "TL-WN722N wifi install issue"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by wolfsburg18 on 2012-10-17
I am going to try and follow the format in regards of what to post when requesting help and I will detail what steps I have taken at the end.

1 ) Machine Brand and Model (PC/Laptop):
```
Dell Optiplex 780 Desktop
```
2 ) Wireless Brand, Model and Wireless Chipset:
```
Wireless Brand: TP-Link
Model: TL-WN722N
Wireless Chipset: Atheros AR9271 or Atheros 5416 depending on which documentation you read.
Wireless USB Device
```
```

$lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]

```

```

$lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2011 Dell Computer Corp. 
Bus 004 Device 002: ID 413c:1005 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bc2:5031 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0cf3:9271 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
3 ) check interface:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:42:22:a4  
          inet addr:10.168.201.93  Bcast:10.168.201.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe42:22a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8956922 (8.9 MB)  TX bytes:3713724 (3.7 MB)
          Memory:febe0000-fec00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:812 (812.0 B)  TX bytes:812 (812.0 B)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

$ iwconfig wlan0
wlan0     No such device

```

4 ) Check for modules:
```

$ lsmod
Module                  Size  Used by
nls_utf8                1421  1 
udf                    86165  1 
crc_itu_t               1715  1 udf
cryptd                  8116  0 
aes_x86_64              7912  496 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
dm_crypt               13043  0 
snd_hda_codec_analog    78702  1 
ndiswrapper           276857  0 
joydev                 11104  0 
usb_storage            50633  1 
snd_hda_intel          25805  3 
snd_hda_codec          85791  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6375  0 
parport_pc             29958  1 
usbhid                 41116  0 
hid                    83888  1 usbhid
snd                    71283  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                2177  0 
dcdbas                  6886  0 
fglrx                2353486  32 
psmouse                65040  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
vgastate                9857  1 vga16fb
ahci                   38350  3 
intel_agp              29319  0 
e1000e                136301  0 
bfarme002@bfarme002-desktop:~/Downloads/TL-WN422G$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]

```
5 ) Kernel boot messages
```

[   17.262693]   alloc irq_desc for 34 on node -1
[   17.262696]   alloc kstat_irqs on node -1
[   17.262704] fglrx_pci 0000:01:00.0: irq 34 for MSI/MSI-X
[   17.263134] [fglrx] Firegl kernel thread PID: 1725
[   17.263316] [fglrx] IRQ 34 Enabled
[   17.680766] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[   17.681169] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.111918] [fglrx] Gart USWC size:936 M.
[   18.111920] [fglrx] Gart cacheable size:371 M.
[   18.111924] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   18.111926] [fglrx] Reserved FB block: Unshared offset:fd0b000, size:2f1000 
[   18.111928] [fglrx] Reserved FB block: Unshared offset:fffc000, size:4000 
[   19.220229] usb-storage: device scan complete
[   20.340673] CPU0 attaching NULL sched-domain.
[   20.340677] CPU1 attaching NULL sched-domain.
[   20.380718] CPU0 attaching sched-domain:
[   20.380721]  domain 0: span 0-1 level MC
[   20.380723]   groups: 0 1
[   20.380728] CPU1 attaching sched-domain:
[   20.380729]  domain 0: span 0-1 level MC
[   20.380731]   groups: 1 0
[   24.222730] scsi 6:0:0:0: Direct-Access     Seagate  FreeAgent GoFlex  211 PQ: 0 ANSI: 0
[   24.223042] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   24.224952] sd 6:0:0:0: [sdb] 1465149167 512-byte logical blocks: (750 GB/698 GiB)
[   24.225825] sd 6:0:0:0: [sdb] Write Protect is off
[   24.225828] sd 6:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[   24.225829] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   24.227187] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   24.227191]  sdb: sdb1
[   24.251580] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   24.251584] sd 6:0:0:0: [sdb] Attached SCSI disk
[   28.030019] eth0: no IPv6 routers present
[   32.681103] Intel AES-NI instructions are not detected.
[   32.743865] padlock: VIA PadLock not detected.
[   61.201460] UDF-fs: Partition marked readonly; forcing readonly mount
[   61.255420] UDF-fs INFO UDF: Mounting volume 'MARVELS_THE_AVENGERS', timestamp 2012/07/11 22:11 (1e98)
[  117.229975] hrtimer: interrupt took 13060 ns
[  131.800603] CE: hpet3 increasing min_delta_ns to 15000 nsec
[  131.800609] CE: hpet3 increasing min_delta_ns to 22500 nsec
[  396.655140] CE: hpet2 increasing min_delta_ns to 15000 nsec
[  396.655147] CE: hpet2 increasing min_delta_ns to 22500 nsec
[ 4216.444330] usb 1-2: USB disconnect, address 2
[ 4220.840659] usb 1-2: new high speed USB device using ehci_hcd and address 5
[ 4221.011644] usb 1-2: configuration #1 chosen from 1 choice
[ 4221.150038] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[ 4221.322725] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 4221.322730] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netathuw'
[ 4221.322807] ndiswrapper (load_wrap_driver:121): couldn't load driver 'netathuw'

```
6 ) Network configuration
```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM-3 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:42:22:a4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.4-3 ip=10.168.201.93 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:32 memory:febe0000-febfffff memory:febd9000-febd9fff ioport:ece0(size=32)

```
7 ) Scan for networks:
```

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```
8 ) Ubuntu Version: 
```

$ lsb_release -d
Description:	Ubuntu 10.04.4 LTS

```
9 ) Kernel/architecture (including 32 vs. 64 bit): 
```

$ uname -mr
2.6.32-43-generic x86_64

```
10 ) Restarting the network:
```

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                  Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

What have I done?
I have followed the information at the link using both the 722 firmware and the 422G firmware
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=TP-Link_TL-WN722N](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=TP-Link_TL-WN722N)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)

If I have missed something I appologize now, I have been working on this for several hours including a trip to the store specifically to purchase this unit which I believed was supported. 

Thanks,

---

### Post by chili555 on 2012-10-17
> ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BUnless you can find a 64-bit XP .inf file, I'd suggest you ditch ndiswrapper:```
sudo ndiswrapper -e netathuw
```Then I'd download the file I've attached to your desktop. Right-click it and select 'Extract Here.' Now open a terminal and do: ```
sudo cp Desktop/htc_9271.fw  /lib/firmware
sudo modprobe ath9k_htc
iwconfig
```Now do you have a wlan0? We may need to do a bit of clean-up once we get it working.

EDIT: > Ubuntu 10.04.4 LTSI hope you have ath9_htc. Fingers crossed. Are you willing to upgrade to 12.04?

---

### Post by wolfsburg18 on 2012-10-18
Chili555,

Thanks for the detailed response, I thought I had installed the 64 driver and tried several drivers before I posted.

I have gone ahead and uninstalled the netathuw driver with ndiswrapper.
```

sudo ndiswrapper -r netathuw

```

While I did not have the ath9k_thc package/driver installed I was able to find it and am currently in the process of installing the package.
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

I will update this once I have finished installing the package and completed the steps documented.

---

### Post by wolfsburg18 on 2012-10-18
Update

I did not have the ath9k_thc driver installed but once I got that installed I was still getting this error
```

$sudo modprobe ath9k_htc
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
ERROR: Module not found

```

I did some reading and found there could be a conflict with other drivers I had installed in an attempt to get this working.  To resolve this I downloaded the 
compat-wireless-2.6.31.1 package and used its unload process to remove what I understand was conflicts

I executed the following commands, excluded the output to shorten this up.
[http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_2.6.39_stable_releases](http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_2.6.39_stable_releases)
in case others follow this I unzipped the package, then went into the directory.
```

$tar -xjvf compat-wireless-2.6.tar.bz2
$cd compat-wireless-2010-05-23/
$sudo make
$sudo make install
$sudo make unload

```

I stopped at that point since what looked to be a wireless driver I had previously tried was removed.

I went back to the steps recommended here
```

$ sudo modprobe ath9k_htc
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

Still working on the final steps to understand how to connect but so far, looks like the device is now recognized and it is up and running.

Thanks!

---

### Post by chili555 on 2012-10-18
> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.Let's see if we can fix this. First, we'll examine the files to see if they need to be amended or eliminated:```
cat /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist
```

---

### Post by wolfsburg18 on 2012-10-18
```

$ cat /etc/modprobe.d/ndiswrapper 
alias usb:v0846p9030d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip* ndiswrapper

$ cat /etc/modprobe.d/blacklist
blacklist bcm43xx

```

on a side note how do I configure the wireless and connect?

---

### Post by chili555 on 2012-10-18
You can safely remove these files:```
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /etc/modprobe.d/blacklist
```Let's see what clues we get here:```
sudo iwlist wlan0 scan
dmesg | grep -e wlan -e ath9
```

---

### Post by wolfsburg18 on 2012-10-18
```

$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:F2:00:BE:40
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"FMoNetGear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000271dac184
                    Extra: Last beacon: 980ms ago
                    IE: Unknown: 000A464D6F4E657447656172
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B000103104700106484D8CB1D090966E5BC0D94EED90ED61021000D4E4554474541522C20496E632E10230009574E5233353030763210240009574E523335303076321042000230311054000800060050F204000110110009574E52333530307632100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081100000000000000000000000000000000000000
          Cell 02 - Address: 00:1F:33:C4:E5:E3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Scooby-Doo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dd88143177
                    Extra: Last beacon: 960ms ago
                    IE: Unknown: 000A53636F6F62792D446F6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD730050F204104A0001101044000102103B00010310470010C294BD19355E918C3A635A4F9EC42F99102100074E45544745415210230007574E523335303010240007574E52333530301042000A313233343536373839301054000800060050F204000110110007574E5233353030100800020086
          Cell 03 - Address: 90:84:0D:DC:46:29
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Apple Network dc4629"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002897ad24160
                    Extra: Last beacon: 470ms ago
                    IE: Unknown: 00144170706C65204E6574776F726B20646334363239
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301720320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010690840DDC4629
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 04 - Address: 64:D9:89:C4:88:A1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"Vendor_Guest"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ae42bce1a
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 000C56656E646F725F4775657374
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0501004E0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 851E00008F000F00FF0359006577617031352D666C7230622E696E0001000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 05 - Address: 64:D9:89:C4:8D:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Egypt007"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ad24db8d8
                    Extra: Last beacon: 530ms ago
                    IE: Unknown: 000847354F7945707374
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B050700460000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D1606000F00000000000000000000000000000000000000
                    IE: Unknown: 851E01008F000F00FF0359006577617031322D666C7230312D696E0007000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 06 - Address: 00:26:F3:87:C8:78
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"FMoDory"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ada3bd140
                    Extra: Last beacon: 250ms ago
                    IE: Unknown: 0007464D6F446F7279
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8800026F387C878103C000101
                    IE: Unknown: 0505000100F401
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D160A000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020037127A
                    IE: Unknown: DD07000C4300000000
          Cell 07 - Address: 64:D9:89:C4:98:60
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"G5OyEpst"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ae433cac2
                    Extra: Last beacon: 190ms ago
                    IE: Unknown: 000847354F7945707374
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0500001D0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359006577617030312D726F632E696E76720000000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 08 - Address: 64:D9:89:C4:98:61
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"Vendor_Guest"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ae434af34
                    Extra: Last beacon: 190ms ago
                    IE: Unknown: 000C56656E646F725F4775657374
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0500001D0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E05008F000F00FF0359006577617030312D726F632E696E76720000000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 09 - Address: 00:1D:6A:B8:18:BB
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Daphne"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d5a22ba143
                    Extra: Last beacon: 30ms ago
                    IE: Unknown: 0006446170686E65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000E127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706444520010D10

``````

$ dmesg | grep -e wlan -e ath9
[   15.395467] usb 1-2: ath9k_htc: Transferred FW: ar9271.fw, size: 51280
[   15.660843] ath9k_htc 1-2:1.0: ath9k_htc: HTC initialized with 33 credits
[   16.053237] Registered led device: ath9k-phy0::radio
[   16.053252] Registered led device: ath9k-phy0::assoc
[   16.053264] Registered led device: ath9k-phy0::tx
[   16.053277] Registered led device: ath9k-phy0::rx
[   16.053279] usb 1-2: ath9k_htc: USB layer initialized
[   16.053300] usbcore: registered new interface driver ath9k_htc
[   16.412120] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.824740] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.878936] ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

---

### Post by chili555 on 2012-10-18
Looks pretty solid! Can you click the Network Manager icon and select your network? Does it try to connect? Does it ask for your encryption key? Please see attached.

---

### Post by wolfsburg18 on 2012-10-18
I have wireless network option but it says "not managed".

I did some checking and found the following
```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

```

Correct me if I am wrong but it is my understanding that network-manager won't manage the connection if it is listed there so I removed the wlan0 lines from the file.

```

$ sudo vi /etc/network/interfaces

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

Restarted the network-manager
```

$sudo service network-manager restart

```

That resolved it, I can now connect to the network.

---

### Post by chili555 on 2012-10-18
> Correct me if I am wrong but it is my understanding that network-manager won't manage the connection if it is listed there so I removed the wlan0 lines from the file.Correct.> I can now connect to the network. Awesome! Please use thread tools at the top to mark Solved; the searchers will appreciate it.

---

### Post by Lisiano on 2012-10-18
I'd like to point out that the AR9271 (ath9k_htc) chipset is supported out of the box starting the 3.0 kernel line (So starting Ubuntu 12.04 I think). There are other nifty features in the newer kernels (Like the ability to create soft APs, not Ad-Hoc, actual APs)

If possible I'd recommend you update to 12.04 if you are using only LTS.

Oh and, I have the exact same adapter.

---

### Post by rsq on 2012-10-21
> **Lisiano said:**
> I'd like to point out that the AR9271 (ath9k_htc) chipset is supported out of the box starting the 3.0 kernel line (So starting Ubuntu 12.04 I think). There are other nifty features in the newer kernels (Like the ability to create soft APs, not Ad-Hoc, actual APs)

If possible I'd recommend you update to 12.04 if you are using only LTS.

Oh and, I have the exact same adapter.

Hi. Thanks for writing this. I'm considering picking up the TP-Link WN722N usb dongle as well, but can you confirm that it works out-of-the-box in master mode (to create a hotspot from an ethernet connection) on 12.10?

---

### Post by Lisiano on 2012-10-21
> **rsq said:**
> Hi. Thanks for writing this. I'm considering picking up the TP-Link WN722N usb dongle as well, but can you confirm that it works out-of-the-box in master mode (to create a hotspot from an ethernet connection) on 12.10?Yes and no. To create a full fledged AP we need to use an external app called hostapd, but otherwise, it works out of the box.
Proof:
```
lisiano@Lisiano-Ubuntu:~$ iwconfig 
br0       no wireless extensions.

vboxnet0  no wireless extensions.

mon.wlan0  IEEE 802.11bgn  Mode:Monitor  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

lo        no wireless extensions.

**wlan0**     IEEE 802.11bgn  **Mode:Master**  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lisiano@Lisiano-Ubuntu:~$
```
[img]http://ubuntuforums.org/attachment.php?attachmentid=225864&stc=1&d=1350846119[/img]

---

### Post by rsq on 2012-10-21
> **Lisiano said:**
> Yes and no. To create a full fledged AP we need to use an external app called hostapd, but otherwise, it works out of the box.
Proof:
```
lisiano@Lisiano-Ubuntu:~$ iwconfig 
br0       no wireless extensions.

vboxnet0  no wireless extensions.

mon.wlan0  IEEE 802.11bgn  Mode:Monitor  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

lo        no wireless extensions.

**wlan0**     IEEE 802.11bgn  **Mode:Master**  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lisiano@Lisiano-Ubuntu:~$
```[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225864&stc=1&d=1350846119[/IMG]

*Perfect*. I will put in my order for the TP-Link wireless usb tonight. Thanks.

---

### Post by uusr1 on 2013-01-08
> **Lisiano said:**
> I'd like to point out that the AR9271 (ath9k_htc) chipset is supported out of the box starting the 3.0 kernel line (So starting Ubuntu 12.04 I think). There are other nifty features in the newer kernels (Like the ability to create soft APs, not Ad-Hoc, actual APs)

If possible I'd recommend you update to 12.04 if you are using only LTS.

Oh and, I have the exact same adapter.

Hello Lisiano and forum,

I have the same usb adaptor (TP-Link TL-WN722N) and am currently running Ubuntu 12.04 LTS on VirtualBox 4.2.6 on my Mac OS X 10.8.2 as the host. I also have Ubuntu 12.04 LTS installed on another virtual machine (VMware Fusion 5) on the same computer. The wifi USB adaptor will work on Ubuntu in VMware, but not in VirtualBox. 

I was wondering if any of you were are able to get this usb adaptor (TP-Link TL-WN722N) working with VirtualBox and if you would happen to know a fix for getting TP-Link TL-WN722N working in Ubuntu in VirtualBox? If all goes well I would like to switch to VirtualBox virtual machine.

I know this to be a problem with VirtualBox and not in VMware after doing searches in google.

Thanks

---

