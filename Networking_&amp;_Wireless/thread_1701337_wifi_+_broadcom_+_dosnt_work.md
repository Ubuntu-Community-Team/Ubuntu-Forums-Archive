---
title: "wifi + broadcom + dosnt work"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by exige- on 2011-03-06
so i have this weak laptop a Lenovo IdeaPad S10-3s.
with ubuntu 10.10 nootbook 32bit
 
i have been having issues with wifi not working.
tried following 3 other posts here didnt work.
and a few tutorials found via google.
 
wifi is turned on in bios. the light is on and all.
 
ifconfig wlan0 up -> no such device
 
and i found that in system -> additional drivers. its the wrong driver. and downloaded the other but it still dosnt show up. kinda dont know what to do since i am a newb :(

---

### Post by exige- on 2011-03-06
Here is more information on my system.

lspci: 
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57790 Gigabit Ethernet PCIe (rev 01)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

lspci -nn | grep 'Wireless Brand':
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57790 Gigabit Ethernet PCIe [14e4:1694] (rev 01)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)


ifconfig:
eth0      Link encap:Ethernet  HWaddr f0:de:f1:13:32:a1  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe13:32a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3205659 (3.2 MB)  TX bytes:450943 (450.9 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:26:82:c5:e5:a9  
          inet6 addr: fe80::226:82ff:fec5:e5a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1:avahi Link encap:Ethernet  HWaddr 00:26:82:c5:e5:a9  
          inet addr:169.254.11.91  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:8 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwconfig wlan0:
wlan0     No such device

lsmod:
Module                  Size  Used by
ndiswrapper           184207  0 
rfcomm                 33811  4 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
snd_hda_codec_conexant    30003  1 
joydev                  8767  0 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
i915                  295435  5 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168060  5 i915,drm_kms_helper
lib80211_crypt_tkip     7736  0 
acer_wmi               13929  0 
wl                   1959533  0 
led_class               2633  1 acer_wmi
btusb                  10969  2 
uvcvideo               55847  0 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
intel_agp              26566  2 i915
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
videodev               43098  1 uvcvideo
serio_raw               4022  0 
v4l1_compat            13359  2 uvcvideo,videodev
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
soundcore                880  1 snd
lib80211                5058  2 lib80211_crypt_tkip,wl
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40204  0 
ahci                   19198  2 
tg3                   123310  0 
libahci                21728  1 ahci

lsmod | grep "wlan_module_name"
dont know i get nothing with this might be because i dont know wlan module name ;>

dmesg:
this gives me a huge list and cant see all of it so i left it out.

lshw -C network:
  *-network               
       description: Ethernet interface
       product: NetLink BCM57790 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: f0:de:f1:13:32:a1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb v2.07 ip=10.0.0.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 memory:f0100000-f010ffff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:c5:e5:a9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0200000-f0203fff

iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:70:36:25:40
                    ESSID:"TDC-9CAC"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:1/5  Signal level:-84 dBm  Noise level:-93 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

iwlist scan wlan0:
iwlist: unknown command `wlan0' (check 'iwlist --help').

lsb_release -d:
Description:    Ubuntu 10.10

uname -mr:
2.6.35-27-generic i686

/etc/init.d/networking restart:
 * Reconfiguring network interfaces...                                                                                                                There is already a pid file /var/run/dhclient.eth0.pid with pid 1520
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/f0:de:f1:13:32:a1
Sending on   LPF/eth0/f0:de:f1:13:32:a1
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 1680
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:26:82:c5:e5:a9
Sending on   LPF/eth1/00:26:82:c5:e5:a9
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/f0:de:f1:13:32:a1
Sending on   LPF/eth0/f0:de:f1:13:32:a1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPOFFER of 10.0.0.4 from 10.0.0.1
DHCPREQUEST of 10.0.0.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.4 from 10.0.0.1
bound to 10.0.0.4 -- renewal in 122961 seconds.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
wlan1: ERROR while getting interface flags: No such device
wlan1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan1.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:26:82:c5:e5:a9
Sending on   LPF/eth1/00:26:82:c5:e5:a9
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by bkratz on 2011-03-06
Going out for awhile, but will check back later, but all your commands for wlan0 really should be eth1, that is the name of your wireless device. Also the signal to noise ratio is pretty bad, you may want to temporarily move closer to the A/P and remove encryption until you get going.

---

### Post by exige- on 2011-03-06
> **bkratz said:**
> Going out for awhile, but will check back later, but all your commands for wlan0 really should be eth1, that is the name of your wireless device. Also the signal to noise ratio is pretty bad, you may want to temporarily move closer to the A/P and remove encryption until you get going.
 
i turned off wireless router when i did this and was running with normal cable.
 
dunno about eth1 vs wlan0. just all guides etc says wlan0.
how do i remove encryption?

---

### Post by kevdog on 2011-03-06
In your case if you look closely at the output (rather than just cutting and pasting), you'll see your wireless adapter is assigned eth1 and is using the wl0 driver or kernel module.  Don't worry about eth1 vs wlan0.  Yes I know most of the tutorials say wlan0.  Way back in Feisty you could easily change assignments between eth1 and wlan0 however I don't recall how to do it anymore since the method has changed to something way more complex.  Anyway just use eth1.  It really doesn't matter.

---

