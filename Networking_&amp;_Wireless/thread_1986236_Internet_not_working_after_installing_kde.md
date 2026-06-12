---
title: "Internet not working after installing kde"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by pattonjm on 2012-05-24
Hello, 
I installed kde today, and and was playing around with it, while connected to a vpn, and when it crashed. I had to hard reboot my computer, and ever since then the Internet stopped working. I uninstalled kde and have tried the Internet on gnome 3 and unity, and but no go. It shows that the wifi is connected, but it doesn't let me connect to anything. I'm running ubuntu 12.04. Any help would be appreciated.

---

### Post by praseodym on 2012-05-24
Hi,

please show the terminal (CTRL+ALT+T) outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
lsmod
```

---

### Post by pattonjm on 2012-05-24
> **praseodym said:**
> Hi,

please show the terminal (CTRL+ALT+T) outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
lsmod
```

Here's the info:

uname -a

```
 Aspire-7741 3.2.0-24-generic #37-Ubuntu SMP x86-64 GNU/Linux

```lspci -nnk | grep -iA2 net

```
 
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)[INDENT]Subsystem: Acer Incorporated [ALI] Aspire 7740G [1025:033d]
Kernel driver in use: tg3
[/INDENT]05:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)[INDENT]Subsystem: Foxconn International, Inc. Device [105b:e034]
Kernel driver in use: ath9k
[/INDENT]
```lsusb

```
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 004: ID 04f2:b1d8 Chicony Electronics Co., Ltd 

```iwconfig

```

wlan0     IEEE 802.11bgn  ESSID:"************"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: ************  
          Bit Rate=121.5 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:113   Missed beacon:0

```rfkill list

```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lsmod

```

Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
ip6table_filter        12815  0 
ip6_tables             27864  1 ip6table_filter
iptable_filter         12810  0 
ip_tables              27473  1 iptable_filter
x_tables               29846  4 ip6table_filter,ip6_tables,iptable_filter,ip_tables
vesafb                 13844  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
binfmt_misc            17540  1 
snd_hwdep              13668  1 snd_hda_codec
fglrx                3263966  107 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
uvcvideo               72627  0 
snd_rawmidi            30748  1 snd_seq_midi
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 132390  0 
videodev               98259  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17128  1 videodev
brcmsmac              570859  0 
joydev                 17693  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           14053  1 ath9k
mac80211              506816  2 ath9k,brcmsmac
ath9k_hw              411112  2 ath9k,ath9k_common
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
brcmutil               15139  1 brcmsmac
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
crc8                   12893  1 brcmsmac
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  4 ath9k,brcmsmac,mac80211,ath
cordic                 12535  1 brcmsmac
video                  19596  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
intel_ips              18089  0 
mei                    41616  0 
mac_hid                13253  0 
psmouse                87692  0 
serio_raw              13211  0 
wmi                    19256  1 acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
uas                    18027  0 
usb_storage            49198  1 
tg3                   152032  0 

```Sorry for the length of the last one, wasn't sure what you wanted there.

Thanks for responding so quick, hope this helps.

One additional note: I can reach my router through my linux box, it just won't let me do anything on the internet itself.

---

### Post by pattonjm on 2012-05-24
Never mind, I figured out what was wrong.  For some reason Ubuntu wasn't talking with the DHCP service.  After restarting the networking on my computer, if fixed the problem.  Thanks for the help!

---

### Post by praseodym on 2012-05-25
:guitar:Great, it works. But, there was another (wrong) wireless module loaded for a Broadcom chipset:

```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```and reboot.

---

