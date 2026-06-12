---
title: "Wireless connection stopped working! please help"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by StayFrosty127 on 2011-09-02
I've had ubuntu for a couple of months and everything was perfect. But then, randomly, my computer would not connect to the internet unless I use an Ethernet cable. Can someone help me fix this? 

Computer: Toshiba Satellite L305-S5947
Wireless Card: AR5001 Wireless Network Adapter (made from Atheros)
Wireless Card Kernel Modules: ath5k




*And if you can, make it as simple as possible to understand*

---

### Post by nm_geo on 2011-09-02
Hi Welcome to the forum.

Can you open a terminal?  What version/flavor of ubuntu?

copy and paste in terminal the following commands.

```
lsmod
```

```
lspci -nn 
```

Paste result in thread please.

---

### Post by StayFrosty127 on 2011-09-02
lsmod: 
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
arc4                    1165  2 
binfmt_misc             6599  1 
joydev                  8735  0 
snd_hda_intel          22107  4 
i915                  290938  3 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
drm_kms_helper         30200  1 i915
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm                   168054  4 i915,drm_kms_helper
ath5k                 130051  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231541  1 ath5k
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                     8153  1 ath5k
uvcvideo               55847  0 
cfg80211              144470  3 ath5k,mac80211,ath
snd                    49006  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  2 i915
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
soundcore                880  1 snd
psmouse                59033  0 
serio_raw               4022  0 
led_class               2633  1 ath5k
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  0 
r8169                  36489  0 
ahci                   19013  0 
mii                     4425  1 r8169
libahci                21667  3 ahci

---

### Post by StayFrosty127 on 2011-09-02
lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

---

### Post by StayFrosty127 on 2011-09-02
And i have ubuntu 10.10

---

### Post by wildmanne39 on 2011-09-02
Hi, post the results of these commands please:
```
sudo lshw -C network 
```
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
dmesg | grep ath
```
Thank you

---

### Post by nm_geo on 2011-09-02
[B]
You have the correct wireless driver and chipset. [/B]

---

### Post by StayFrosty127 on 2011-09-02
The first two codes:
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:c0:0a:75
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:92:4f:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:94600000-9460ffff
keanu@keanu-Satellite-L305:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1E:33:C0:0A:75

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             71.250.0.12


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:24:D2:92:4F:A4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by StayFrosty127 on 2011-09-02
Third code:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by StayFrosty127 on 2011-09-03
What does the dividing line in the other codes mean?

Fourth Code:
Usage:    rfkill [options] command
Options:
    --version    show version (0.4)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

---

### Post by wildmanne39 on 2011-09-03
Hi, this is an exact quote from the manual pages for grep.
> Alternation
       Two  regular  expressions  may  be  joined by the infix operator |; the
       resulting  regular  expression  matches  any  string  matching   either
       alternate expression.



Also please run this command again it did not come out right, just copy and paste the command into the terminal.
```
rfkill list all
```
Thank you

---

