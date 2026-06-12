---
title: "Can't Access Websites through Wireless.  Can through Ethernet."
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by ProgressionMurph on 2010-12-02
Hello Everyone!  I've encountered some trouble.  A little background information first before explaining the problem:
              I am in the process of setting up a home server, creating a website, and making it available to the World Wide Web for anyone to access.  I installed Maverick Meerkat Server Edition AMD64 and due to my lack of command line knowledge I decided to sudo apt-get install ubuntu-desktop as a way to have a GUI desktop.  Whilst I probably installed more than needed thats the route I decided to take.  During the installation of MMSE (Maverick Meerkat Server Edition) AMD64 I connected my laptop to my router via an Ethernet cord, which is why I had the ability to install the ubuntu-desktop package, and during the installation my network settings were already detected.  Now when I try to connect to the Internet via WIFI I'm unable to load any web pages.  However, when I reconnect my computer to the router with a Ethernet cord I'm able to load web pages again.

    So now that you are brought up to speed I'll post some data that may be of use (all the previous commands were entered while simultaneously being connected to the Internet by Ethernet and wireless.

**Wireless Brand, Model and Wireless Chipset: **
$ lspci
$ lsusb
$ lspci -nn | grep 'Wireless Brand' 
```
alex@soapbox:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
18:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
38:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
38:03.1 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
38:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
38:03.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
38:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
alex@soapbox:~$
alex@soapbox:~$ 
alex@soapbox:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2550 AuthenTec, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0ac8:1101 Z-Star Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
alex@soapbox:~$
alex@soapbox:~$ 
alex@soapbox:~$ lspci -nn | grep 'Wireless Brand' 
alex@soapbox:~$ 
```[B]
check interface:
[/B]$ ifconfig
$ iwconfig```
alex@soapbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:42:fd:58:41  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: 2002:460f:919f:1234:217:42ff:fefd:5841/64 Scope:Global
          inet6 addr: fe80::217:42ff:fefd:5841/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24119744 (24.1 MB)  TX bytes:2620435 (2.6 MB)
          Interrupt:20 Memory:f2700000-f2720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:617706 (617.7 KB)  TX bytes:617706 (617.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:6a:0d:76  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fe6a:d76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3657086 (3.6 MB)  TX bytes:678118 (678.1 KB)

alex@soapbox:~$ 
alex@soapbox:~$
alex@soapbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ClovisNation"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:75:A1:74:B0   
          Bit Rate=300 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

alex@soapbox:~$ 
```[B]Check for modules:
[/B]$ lsmod```
alex@soapbox:~$ lsmod
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7952  1 
parport_pc             30086  0 
ppdev                   6644  0 
arc4                    1497  2 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   299524  1 
ath9k                 101666  0 
joydev                 11139  0 
ath9k_common            6874  1 ath9k
ath9k_hw              314699  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
snd_hda_intel          26019  4 
mac80211              265872  2 ath9k,ath9k_common
i915                  331512  3 
snd_hda_codec         100855  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6482  1 snd_hda_codec
snd_pcm                88118  4 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
drm_kms_helper         32836  1 i915
drm                   205201  4 i915,drm_kms_helper
snd_rawmidi            21775  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57032  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               62347  0 
snd_timer              23518  2 snd_pcm,snd_seq
pcmcia                 40944  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit            6208  1 i915
yenta_socket           24279  0 
videodev               49327  1 uvcvideo
pcmcia_rsrc            10357  1 yenta_socket
v4l1_compat            15519  2 uvcvideo,videodev
cfg80211              170293  4 ath9k,ath9k_common,ath,mac80211
snd                    63620  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    11009  1 videodev
psmouse                62080  0 
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  22144  1 i915
soundcore               1240  1 snd
intel_agp              32144  2 i915
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
serio_raw               4942  0 
output                  2527  1 video
lp                     10169  0 
parport                36936  3 parport_pc,ppdev,lp
fujitsu_laptop         12807  0 
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  3 ath9k,fujitsu_laptop,sdhci
ahci                   21857  0 
firewire_ohci          24679  0 
firewire_core          54167  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
e1000e                151787  0 
libahci                26199  3 ahci
alex@soapbox:~$
alex@soapbox:~$  
alex@soapbox:~$ lsmod | grep "wlan_module_name"
alex@soapbox:~$ 
```[B]Kernel boot messages:
[/B]$ dmesg
Output fills the terminal and begins to disappear as more kernel boot messages appear.

[B]Network configuration:
[/B]$ sudo lshw -C network```
alex@soapbox:~$ sudo lshw -C network
[sudo] password for alex: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:17:42:fd:58:41
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=1.8-3 ip=192.168.2.9 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:43 memory:f2700000-f271ffff memory:f2725000-f2725fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:63:6a:0d:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-23-server firmware=N/A ip=192.168.2.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:f2500000-f250ffff
alex@soapbox:~$
```[B]Scan for networks:
[/B]$ iwlist scan```
alex@soapbox:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:75:A1:74:B0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"ClovisNation"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ec88b6f13d
                    Extra: Last beacon: 99990ms ago
                    IE: Unknown: 000C436C6F7669734E6174696F6E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE110FFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
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
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C33EE110FFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DD9F0050F204104A0001101044000102103B000103104700102880288028801880A880002275A174B01021001242656C6B696E20436F72706F726174696F6E1023001642656C6B696E20576972656C65737320526F75746572102400034635441042000C3131313131313131313131311054000800060050F20400011011001642656C6B696E20576972656C65737320526F75746572100800020084103C000101

alex@soapbox:~$ 
```[B]Ubuntu Version: 
[/B]$ lsb_release -d```
alex@soapbox:~$ lsb_release -d
Description:    Ubuntu 10.10
alex@soapbox:~$ 
```[B]Kernel/architecture (including 32 vs. 64 bit):
[/B]$ uname -mr```
alex@soapbox:~$ uname -mr
2.6.35-23-server x86_64
alex@soapbox:~$ 
```[B]Restarting the network:
[/B]$ sudo /etc/init.d/networking restart```
alex@soapbox:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1495
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:17:42:fd:58:41
Sending on   LPF/eth0/00:17:42:fd:58:41
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
Ignoring unknown interface wlan0=wlan0.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:17:42:fd:58:41
Sending on   LPF/eth0/00:17:42:fd:58:41
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.2.9 from 192.168.2.1
DHCPREQUEST of 192.168.2.9 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.9 from 192.168.2.1
bound to 192.168.2.9 -- renewal in 132225004 seconds.
ssh stop/waiting
ssh start/running, process 16646
                                                                         [ OK ]
alex@soapbox:~$ 
```I hope I was able to provide you with all the information you need to guide me in right direction!

Thanks a bunch,
Alex

***This is now solved.  I restarted my computer and now it works***

---

