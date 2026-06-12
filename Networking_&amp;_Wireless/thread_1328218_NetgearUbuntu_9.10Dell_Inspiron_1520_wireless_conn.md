---
title: "Netgear/Ubuntu 9.10/Dell Inspiron 1520 wireless connects and then fails"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by boz86 on 2009-11-16
Good morning.

Laptop connects to the wireless network, sometimes after two or three tries. Will work fine for a few minutes, then drops the connection. The icon will show the network still connected with strong signal, but won't connect until I disconnect first and then reconnect. Wired ethernet works perfectly.

Copying some of this from a post in General Help.

I have updated the router (Netgear WGR614v6, U.S.) to the latest firmware off their website.

The wireless settings:

Wireless: SSID set, Mode infrastructure, BSSID empty, MAC address empty, MTU automatic

Wireless Security: Security WPA and WPA 2 Personal, Password entered

IPv4 Settings: Automatic (DHCP), DHCP client ID empty, routes all empty

IPv6 Settings: Method Ignore.

***Per the posting guidelines:***
1. Dell Inspiron 1520 Laptop
2.
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
$ 
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
3.03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
3.ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:a6:e6:1f  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fea6:e61f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7279836 (7.2 MB)  TX bytes:1543528 (1.5 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1d:60:b3:97:02  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:feb3:9702/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:72
          TX packets:41 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2985 (2.9 KB)  TX bytes:8113 (8.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:a6:e6:1f  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fea6:e61f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7279836 (7.2 MB)  TX bytes:1543528 (1.5 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1d:60:b3:97:02  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:feb3:9702/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:72
          TX packets:41 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2985 (2.9 KB)  TX bytes:8113 (8.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
eth0      no wireless extensions.

pan0      no wireless extensions.

5. lsmod:
Module                  Size  Used by
michael_mic             2204  8 
arc4                    1660  4 
cbc                     3516  381 
aes_i586                8124  382 
aes_generic            27484  1 aes_i586
ecb                     2524  5 
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
bnep                   12060  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
joydev                 10272  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
dell_wmi                2564  0 
snd_seq_oss            28576  0 
dell_laptop             8128  0 
uvcvideo               59080  0 
b44                    28684  0 
snd_seq_midi            6432  0 
psmouse                56180  0 
sdhci_pci               7100  0 
ssb                    35300  1 b44
snd_rawmidi            22208  1 snd_seq_midi
videodev               36736  1 uvcvideo
dcdbas                  7292  1 dell_laptop
btusb                  11856  2 
sdhci                  17472  1 sdhci_pci
mii                     5212  1 b44
iptable_filter          3100  0 
dm_crypt               12928  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
v4l1_compat            14496  2 uvcvideo,videodev
nvidia               9586440  40 
serio_raw               5280  0 
led_class               4096  1 sdhci
lp                      8964  0 
lib80211_crypt_tkip     8636  0 
ip_tables              11692  1 iptable_filter
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wl                   1272936  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
x_tables               16544  1 ip_tables
lib80211                6432  2 lib80211_crypt_tkip,wl
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
parport                35340  2 ppdev,lp
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp
6.  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1d:60:b3:97:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.6 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a6:e6:1f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.9 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff
7.lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

8. Ubuntu 9.10
9. Kernel 2.6.31-14-generic i686
10. sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                           Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth1=eth1.

---

### Post by ibbill on 2009-11-23
So no solution as of yet (rats)

have 2-1520 laptops that had to roll back to 9.04. Odd that a Dell product was not taken into consideration with the 9.10 OS.

Oh well 9.04 runs well.

Bill

---

### Post by boz86 on 2009-11-24
> **ibbill said:**
> So no solution as of yet (rats)

have 2-1520 laptops that had to roll back to 9.04. Odd that a Dell product was not taken into consideration with the 9.10 OS.

Oh well 9.04 runs well.

Bill
thread after thread in the Network and Wireless section about this. Also at least two bug reports, I subscribed to both of those to see if/when they show a fix.

Seems to be a WPA conflict in 9.10. Mines does work if WPA turned off, but I don't like doing that.

---

### Post by ibbill on 2009-11-24
Boz thanks for the info. will try and find the thread with the problem thanks again.

---

