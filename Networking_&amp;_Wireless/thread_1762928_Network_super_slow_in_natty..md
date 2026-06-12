---
title: "Network super slow in natty."
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by mwacky on 2011-05-19
Not too long after my upgrade to 11.04 my internet began to crawl.  Worked fine prior to that, but now I have to run Win 7 since I can get 7800 kb/s on speedtest.net it just like normal, and ubuntu used to.  Right now my updates from Ubuntu are at 20-30 K/sec, not even worth an update unless there is something for network.  Please help I don't want to run windows on this pc. 

```
lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Clam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:CE:8E:BB   
          Bit Rate=65 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:950   Missed beacon:0


ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:4a:92:5a:1d:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2736 (2.7 KB)  TX bytes:2736 (2.7 KB)

wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:40:91:95  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4e0f:6eff:fe40:9195/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5574246 (5.5 MB)  TX bytes:905622 (905.6 KB)



```


I'm forgetting the other helpful commands...

My file transfer to a windows share on my network is running about 21 KB/S, should be much better than that.


PC:
HP G42 Laptop
AMD Vision 
Natty 11.04 64bit

---

### Post by zzarko on 2011-05-20
I don't have an answer to your problem (sorry), but I have a similar one. After upgrading from 10.10 to 11.04, transfer speed from samba shares on other machine dropped from 7-8MB/s to ~600KB/s, and I still haven't found solution to this.

EDIT: Using Nautilus's Go/Network, I can get ~6MB/s

---

### Post by mwacky on 2011-05-21
Here's my proper outputs:'

HP Laptop G42
AMD Vision Graphics/Processor
Natty 11.04

```

                                                                         [ 

mwacker@Cleveland:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
mwacker@Cleveland:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b1aa Chicony Electronics Co., Ltd Webcam-101
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

mwacker@Cleveland:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:4a:92:5a:1d:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24288 (24.2 KB)  TX bytes:24288 (24.2 KB)

wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:40:91:95  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4e0f:6eff:fe40:9195/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1180577 (1.1 MB)  TX bytes:205069 (205.0 KB)

mwacker@Cleveland:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Clam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:CE:8E:BB   
          Bit Rate=52 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:331   Missed beacon:0

mwacker@Cleveland:~$ lsmod
Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
vesafb                 13761  1 
snd_hda_codec_hdmi     28103  1 
binfmt_misc            17565  1 
snd_hda_codec_realtek   336693  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
ath9k                 118238  0 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
mac80211              294370  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
fglrx                2739144  51 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13851  1 ath9k
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
uvcvideo               72195  0 
hp_wmi                 13706  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
sparse_keymap          13898  1 hp_wmi
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178528  3 ath9k,mac80211,ath
psmouse                73535  0 
sp5100_tco             13744  0 
soundcore              12680  1 snd
edac_core              53845  0 
shpchp                 37297  0 
serio_raw              13166  0 
k10temp                13119  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13303  0 
edac_mce_amd           23464  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
uas                    17996  0 
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 





mwacker@Cleveland:~$ sudo lshw -C network
[sudo] password for mwacker: 
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 4c:0f:6e:40:91:95
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0100000-d010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 3c:4a:92:5a:1d:50
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d002ffff
 
mwacker@Cleveland:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 1C:AF:F7:CE:8E:BB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Clam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000619a13fd80
                    Extra: Last beacon: 51810ms ago
                    IE: Unknown: 0004436C616D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010000000000000100000001CAFF7CE8EBB10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363031104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363031100800020086103C000103104900140024E26002000101600000020001600100020001

mwacker@Cleveland:~$ lsb_release -d
Description:	Ubuntu 11.04

mwacker@Cleveland:~$ uname -mr
2.6.38-8-generic x86_64

mwacker@Cleveland:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

```

Thanks for any direction here.

---

### Post by Vardy on 2011-05-21
Not sure if this is helpful  but worth a mention... I had been experiencing the same problem since upgrade to Natty. Turned out my ADSL filter (the one going to my main phone) was stuffed - I realised when I removed the phone from the socket and it just went back to normal. The computer is not even on the same phoneline but the dodgy filter was still affecting data transfer. Funny sort of a coincidence methinks

Just saying...

Cheers
Andrew

---

### Post by headvampyre@hotmail.co.uk on 2011-05-21
Hmm. Does your router support IPv6?

I've noticed this used to cause a lot of issues for me :/

Also, if I remember properly, Ubuntu had a lot of issues with IPv6 aswell.

---

### Post by headvampyre@hotmail.co.uk on 2011-05-21
[http://ubuntuforums.org/showthread.php?p=1564888](http://ubuntuforums.org/showthread.php?p=1564888)

Read this - try blacklisting the IPv6 module and see if thgat makes any difference.

---

### Post by zzarko on 2011-05-22
I tried blacklisting ipv6, but the speed remained the same... Also, there is no high CPU usage nor high I/O usage during transfer (htop,iotop). I made a setup with samba on the server side about two years ago. I also tried NFS, but it was causing me some problems with file/directory rights (as I remember, I'm not sure), and I opted for samba instead. Maybe I should try NFS again.

EDIT: There is a bug report about this, it turns out that people are having problems with cifs since 9.10:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/471512)

---

