---
title: "Can't find Linux wireless card for Centrino Wireless-N 100"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by Colby3316 on 2011-10-06
I need the Linux driver for Centrino Wireless-N 100.  Help?

---

### Post by poolet on 2011-10-06
hello, open up a terminal and type the following:: 

```
lsmod
```

```
lshw - C network 
```

```
ifconfig 
```

and paste the output here!!!

---

### Post by Colby3316 on 2011-10-06
> **poolet said:**
> hello, open up a terminal and type the following:: 

```
lsmod
``````
lshw - C network 
``````
ifconfig 
```and paste the output here!!!
```
root@Super-LINUX:~# lsmod
Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
dm_crypt               22993  0 
parport_pc             36959  0 
ppdev                  17113  0 
nvidia              10709116  0 
pci_stub               12622  1 
vboxpci                23190  0 
vboxnetadp             13382  0 
vboxnetflt             23435  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
vboxdrv               286726  3 vboxpci,vboxnetadp,vboxnetflt
arc4                   12529  2 
iwlagn                333716  0 
iwlcore               167502  1 iwlagn
snd_hda_intel          33176  4 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
psmouse                73535  0 
mac80211              294370  2 iwlagn,iwlcore
serio_raw              13166  0 
joydev                 17606  0 
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              178528  3 iwlagn,iwlcore,mac80211
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
i915                  515121  2 
usbhid                 46956  0 
hid                    91020  1 usbhid
drm_kms_helper         42136  1 i915
drm                   227534  3 i915,drm_kms_helper
ahci                   25951  1 
libahci                26642  1 ahci
r8169                  48022  0 
xhci_hcd               77643  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
root@Super-LINUX:~# lshw - C netowork
Hardware Lister (lshw) - B.02.15
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.15)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -c CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
        -numeric        output numeric IDs (for PCI, USB, etc.)

root@Super-LINUX:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:30:9f:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42640 (42.6 KB)  TX bytes:42640 (42.6 KB)

wlan0     Link encap:Ethernet  HWaddr 78:92:9c:04:1a:24  
          inet6 addr: fe80::7a92:9cff:fe04:1a24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169196622 (169.1 MB)  TX bytes:6919000 (6.9 MB)

root@Super-LINUX:~# 

```

---

### Post by jawilljr on 2011-10-06
Please post the output of:

```
uname -r
```

Why am I asking this? Because according to [Intel Linux Wireless](http://intellinuxwireless.org/) you need kernel version 2.6.37 or greater for your card to work.

Jerry

---

### Post by wildmanne39 on 2011-10-06
Hi, according to lsmod you have the driver installed, let's make sure it is correct for your card, please post the results of:
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by Colby3316 on 2011-10-06
> **wildmanne39 said:**
> Hi, according to lsmod you have the driver installed, let's make sure it is correct for your card, please post the results of:
```
lspci -nnk | grep -iA2 net
```Thank you
```
oot@Super-LINUX:~# lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Micro-Star International Co., Ltd. Device [1462:108d]
        Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 100 [8086:08ae]
        Subsystem: Intel Corporation Centrino Wireless-N 100 BGN [8086:1005]
        Kernel driver in use: iwlagn

```

---

### Post by Colby3316 on 2011-10-06
> **jawilljr said:**
> Please post the output of:

```
uname -r
```Why am I asking this? Because according to [Intel Linux Wireless]("http://intellinuxwireless.org/") you need kernel version 2.6.37 or greater for your card to work.

Jerry
```
root@Super-LINUX:~# uname -r
2.6.38-11-generic

```

---

### Post by wildmanne39 on 2011-10-06
Hi, please post the results of these commands:
```
dmesg | egrep 'iwl|firm|wlan0'
```
```
rfkill list all
```
```
ndiswrapper -l
```
```
sudo iwlist scan
```
```
iwconfig
```
```
nm-tool
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Colby3316 on 2011-10-06
> **wildmanne39 said:**
> Hi, please post the results of these commands:
```
dmesg | egrep 'iwl|firm|wlan0'
``````
rfkill list all
``````
ndiswrapper -l
``````
sudo iwlist scan
``````
iwconfig
``````
nm-tool
```here by clicking on new reply and click # and paste the information between the brackets.
Thank you
```
root@Super-LINUX:~# dmesg | egrep 'iwl|firm|wlan0'
[   22.914612] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   22.914620] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   22.914754] iwlagn 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   22.914773] iwlagn 0000:04:00.0: setting latency timer to 64
[   22.914843] iwlagn 0000:04:00.0: Detected Intel(R) Centrino(R) Wireless-N 100 BGN, REV=0x6C
[   22.936533] iwlagn 0000:04:00.0: device EEPROM VER=0x166, CALIB=0x6
[   22.936542] iwlagn 0000:04:00.0: Device SKU: 0X9
[   22.936549] iwlagn 0000:04:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   22.936580] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   22.936713] iwlagn 0000:04:00.0: irq 55 for MSI/MSI-X
[   23.008445] iwlagn 0000:04:00.0: loaded firmware version 39.31.5.1 build 32895
[   23.046245] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   24.119125] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  203.162822] wlan0: authenticate with 00:25:3c:3d:80:d1 (try 1)
[  203.165044] wlan0: authenticated
[  203.165121] wlan0: associate with 00:25:3c:3d:80:d1 (try 1)
[  203.167172] wlan0: RX AssocResp from 00:25:3c:3d:80:d1 (capab=0x431 status=0 aid=1)
[  203.167181] wlan0: associated
[  203.170363] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  214.038785] wlan0: no IPv6 routers present
root@Super-LINUX:~# rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
root@Super-LINUX:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:C4:03:04:E1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"2WIRE196"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a670c3f84b
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 00083257495245313936
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 2E:24:81:DC:75:F4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 330ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
          Cell 03 - Address: 00:25:3C:3D:80:D1
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"Colby's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005dd8e02d2a
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 000F436F6C62792773204E6574776F726B
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 0706555320010B1B
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
          Cell 04 - Address: 00:23:51:C4:2C:29
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"2WIRE370"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000579c0c2d181
                    Extra: Last beacon: 490ms ago
                    IE: Unknown: 00083257495245333730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

root@Super-LINUX:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Colby's Network"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:25:3C:3D:80:D1   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:385   Missed beacon:0

root@Super-LINUX:~# nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        6C:62:6D:30:9F:66

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Colby's Network] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        78:92:9C:04:1A:24

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    2WIRE370:        Infra, 00:23:51:C4:2C:29, Freq 2427 MHz, Rate 54 Mb/s, Strength 35 WEP
    2WIRE597:        Infra, 98:2C:BE:9E:E1:29, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    *Colby's Network:Infra, 00:25:3C:3D:80:D1, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    hpsetup:         Ad-Hoc, 2E:24:81:DC:75:F4, Freq 2437 MHz, Rate 11 Mb/s, Strength 54
    2WIRE394:        Infra, 00:26:50:AE:2A:01, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WEP
    2WIRE517:        Infra, 00:1A:C4:05:72:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 38 WEP
    2WIRE196:        Infra, 00:1A:C4:03:04:E1, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WEP
    Kincade:         Infra, 00:24:B2:22:DC:A0, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2

  IPv4 Settings:
    Address:         192.168.1.76
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


root@Super-LINUX:~# 

```

I don't have ndiswrapper and I tried installing but it didn't work.

---

### Post by wildmanne39 on 2011-10-06
Hi, we do not want ndiswrapper, I was just checking to make sure it is not installed.

What network are you trying to connect too?
Thank you

---

### Post by Colby3316 on 2011-10-07
> **wildmanne39 said:**
> Hi, we do not want ndiswrapper, I was just checking to make sure it is not installed.

What network are you trying to connect too?
Thank you
What?  OK when I run airmon-ng i just get Interface       Chipset         Driver
and it just sits there.  I got it to work when i did the think up at the top and then it stopped working again.

---

### Post by wildmanne39 on 2011-10-07
Hi, what is airmon-ng?
Thank you

---

### Post by cariboo on 2011-10-07
We don't support this type of activity here. Thread closed.

---

