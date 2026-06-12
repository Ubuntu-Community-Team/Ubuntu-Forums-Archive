---
title: "internet via broadband is slow"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by tiranuom on 2011-09-17
i reinstalled ubuntu 11.04 yesterday. and now im experiencing a very slow Internet speed. it doesn't go beyond 20kB. before reinstall i had about 140kB. i can go upto that much of speed on my windows installation.

please help me to improve my Internet speed.

thanks.

---

### Post by wildmanne39 on 2011-09-18
Hi, let's give it a try please run these commands in  a terminal and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by tiranuom on 2011-09-18
for 
cat /etc/lsb-release; uname -a 
i got 
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

```actually im still downloading the updates(68MB is to go out of 223MB):D

for 
sudo lshw -C network
i got 
```

  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0c:f1:6d:57:c5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:feaff000-feafffff ioport:d080(size=64)

```for 
lspci -nn | grep -e 0280 -e 0200
i got
```

02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 81)

```for 
lsusbi got 
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1c4f:0003 SiGma Micro HID controller
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1c9e:9605  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```for 
iwconfig
i got 
```

lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.


```for 
rfkill list all
i got nothing 

for
lsmod
i got
```

Module                  Size  Used by
ppp_deflate            12838  0 
zlib_deflate           26594  1 ppp_deflate
bsd_comp               12777  0 
ppp_async              17308  1 
crc_ccitt              12595  1 ppp_async
binfmt_misc            13213  1 
snd_es1938             23590  2 
gameport               15027  2 snd_es1938
snd_pcm                80244  1 snd_es1938
nouveau               621970  2 
snd_page_alloc         14073  1 snd_pcm
snd_opl3_lib           18760  1 snd_es1938
snd_hwdep              13274  1 snd_opl3_lib
snd_mpu401_uart        13865  1 snd_es1938
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
ttm                    65184  1 nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         40745  1 nouveau
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
option                 21045  2 
snd_timer              28659  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         14110  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
usb_wwan               19711  1 option
drm                   180037  4 nouveau,ttm,drm_kms_helper
usbserial              37116  7 option,usb_wwan
snd                    55295  13 snd_es1938,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 nouveau
parport_pc             32111  1 
soundcore              12600  1 snd
video                  18951  1 nouveau
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
uas                    17676  0 
floppy                 60032  0 
e100                   40108  0 

```for 
dmesg | grep wlan0
i got nothing and 

for 
sudo iwlist scan
i got 
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

```thanks

---

### Post by wildmanne39 on 2011-09-18
Hi, ok none of that information helped so let's have the results of these commands please:
```
nm-tool
```
```
ifconfig
```
so the connection you are having the trouble with is your wired connection correct?
Thank you

---

### Post by jtsmith90 on 2012-01-21
Heya, Im having the same problem But I'm on 11.10 may i please have some help to. Mine is with both wired and wireless. can connect to a ftp with full speed

Thanks in advance Josh

cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Jedi-Consular 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

```sudo lshw -C network
```
yoda@Jedi-Consular:~$ sudo lshw -C network
[sudo] password for yoda: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:a9:ef:1a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 34
       serial: bc:77:37:8a:f4:c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=17.168.5.1 build 33993 ip=192.168.1.176 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:c4500000-c4501fff
```lspci -nn | grep -e 0280 -e 0200
```
yoda@Jedi-Consular:~$ lspci -nn | grep -e 0280 -e 0200
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008b] (rev 34)
19:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)

```lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 
Bus 002 Device 004: ID 8086:0189 Intel Corp. 
Bus 002 Device 011: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical

```iwconfig
```
o        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Welfarnet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:CF:30:CE:18:1D   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:615  Invalid misc:38   Missed beacon:0

```rfkill list all
```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```lsmod```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
yoda@Jedi-Consular:~$ lsmod
Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
bnep                   17923  2 
rfcomm                 38408  8 
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_accel               21632  0 
lis3lv02d              19280  1 hp_accel
iwlagn                273944  0 
input_polldev          13648  1 lis3lv02d
psmouse                73673  0 
mac80211              272785  1 iwlagn
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
btusb                  18160  2 
rts_pstor             353227  0 
cfg80211              172392  2 iwlagn,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
bluetooth             148839  23 bnep,rfcomm,btusb
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
radeon                925020  0 
ttm                    65224  1 radeon
i915                  505108  2 
ahci                   21634  2 
libahci                25727  1 ahci
drm_kms_helper         32889  2 radeon,i915
xhci_hcd               72915  0 
r8169                  43104  0 
drm                   192226  5 radeon,ttm,i915,drm_kms_helper
i2c_algo_bit           13199  2 radeon,i915
wmi                    18744  1 hp_wmi
video                  18908  1 i915

```dmesg | grep wlan0
```
[   11.650696] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.958863] wlan0: authenticate with 20:cf:30:ce:18:1d (try 1)
[   13.961571] wlan0: authenticated
[   13.973121] wlan0: associate with 20:cf:30:ce:18:1d (try 1)
[   13.977982] wlan0: RX AssocResp from 20:cf:30:ce:18:1d (capab=0x411 status=0 aid=5)
[   13.977990] wlan0: associated
[   13.982165] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.079373] wlan0: no IPv6 routers present
[   81.790928] wlan0: deauthenticating from 20:cf:30:ce:18:1d by local choice (reason=3)
[  158.489323] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  160.775235] wlan0: authenticate with 20:cf:30:ce:18:1d (try 1)
[  160.777993] wlan0: authenticated
[  160.778392] wlan0: associate with 20:cf:30:ce:18:1d (try 1)
[  160.781681] wlan0: RX AssocResp from 20:cf:30:ce:18:1d (capab=0x411 status=0 aid=5)
[  160.781690] wlan0: associated
[  160.784794] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  175.895061] wlan0: no IPv6 routers present
[ 5538.031556] wlan0: deauthenticating from 20:cf:30:ce:18:1d by local choice (reason=3)
[ 5549.075386] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5551.335868] wlan0: authenticate with 20:cf:30:ce:18:1d (try 1)
[ 5551.338677] wlan0: authenticated
[ 5551.339071] wlan0: associate with 20:cf:30:ce:18:1d (try 1)
[ 5551.342352] wlan0: RX AssocResp from 20:cf:30:ce:18:1d (capab=0x411 status=0 aid=8)
[ 5551.342362] wlan0: associated
[ 5551.345880] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5561.757126] wlan0: no IPv6 routers present
[17968.452951] wlan0: authenticate with 20:cf:30:ce:18:1d (try 1)
[17968.455864] wlan0: authenticated
[17968.456268] wlan0: associate with 20:cf:30:ce:18:1d (try 1)
[17968.459600] wlan0: RX ReassocResp from 20:cf:30:ce:18:1d (capab=0x411 status=0 aid=5)
[17968.459609] wlan0: associated

```sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 20:CF:30:CE:18:1D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Welfarnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bfcf978840
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000957656C6661726E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD890050F204104A00011010440001021041000100103B00010310470010653F8B9DAF80A0CD8B18B345CE39078C102100074153555354656B1023000F576972656C65737320526F75746572102400063132333435361042000234351054000800060050F2040001101100144153555320576972656C65737320526F75746572100800020084103C000101
                    IE: Unknown: DD090010180208F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:25:9C:31:96:30
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005b8a5ffd15
                    Extra: Last beacon: 984ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B0001031047001063BB96A590730F42D2EB5C99FF78ED5E102100104C696E6B73797320627920436973636F102300075752543631304E1024000876322E30302E30301042000234321054000800060050F2040001101100075752543631304E100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081500000000000000000000000000000000000000

yoda@Jedi-Consular:~$ 

```

nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        2C:27:D7:A9:EF:1A

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Welfarnet 1] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        BC:77:37:8A:F4:C1

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NETGEAR:         Infra, 00:22:3F:90:0D:09, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    linksys:         Infra, 00:25:9C:31:96:30, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    *Welfarnet:      Infra, 20:CF:30:CE:18:1D, Freq 2437 MHz, Rate 54 Mb/s, Strength 71 WPA2

  IPv4 Settings:
    Address:         192.168.1.176
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
```

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:a9:ef:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:480781 (480.7 KB)  TX bytes:30211 (30.2 KB)
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4207 (4.2 KB)  TX bytes:4207 (4.2 KB)

wlan0     Link encap:Ethernet  HWaddr bc:77:37:8a:f4:c1  
          inet addr:192.168.1.176  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be77:37ff:fe8a:f4c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:458343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:446116414 (446.1 MB)  TX bytes:21336375 (21.3 MB)
```

Thanks Josh

---

### Post by wildmanne39 on 2012-01-21
Hi, try this to get your wireless working, run the commands one at a time and do not restart your computer after you run the commands, if it works we will need to make it permanent.

Unplug your wired connection before running these commands so the wireless will take over.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
Thanks

---

