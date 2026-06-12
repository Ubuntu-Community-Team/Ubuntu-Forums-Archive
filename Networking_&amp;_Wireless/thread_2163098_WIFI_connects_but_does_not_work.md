---
title: "WIFI connects but does not work"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by riiicoolaaa on 2013-07-17
Hi,

I have Ubuntu 12.04 on a Dell Precision M 4700.
When I connect the computer to the internet via a wire, everything works fine.
However, when I try to connect to the wifi, it says it's connected, but I cannot go on the web which is annoying.

Any idea?

Cheers,
N

---

### Post by praseodym on 2013-07-17
Please open a terminal with CTRL+ALT+T and show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
cat /etc/resolv.conf
route -n
```

---

### Post by riiicoolaaa on 2013-07-17
Here you are:

```
waldechise@waldechise-Precision-M4700:~$ uname -a
Linux waldechise-Precision-M4700 3.2.0-49-generic #75-Ubuntu SMP Tue Jun 18 17:39:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
waldechise@waldechise-Precision-M4700:~$ lspci -nnk |grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
            Subsystem: Dell Device [1028:053e]
            Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 35)
            Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1121]
            Kernel driver in use: iwlwifi
waldechise@waldechise-Precision-M4700:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp.
waldechise@waldechise-Precision-M4700:~$ lsmod
Module                  Size  Used by
vesafb                 13844  1
rfcomm                 47604  12
bnep                   18281  2
snd_hda_codec_hdmi     32474  0
arc4                   12529  2
snd_hda_codec_idt      70795  1
dell_wmi               12681  0
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0
snd_hda_intel          33719  3
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
fglrx                5277616  135
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30748  1 snd_seq_midi
dell_laptop            18119  0
dcdbas                 14490  1 dell_laptop
btusb                  18332  2
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             180153  23 rfcomm,bnep,btusb
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
psmouse                97485  0
serio_raw              13211  0
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32866  0
wmi                    19256  1 dell_wmi
video                  19651  0
iwlwifi               401148  0
mac80211              506862  1 iwlwifi
mac_hid                13253  0
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205774  2 iwlwifi,mac80211
mei                    41616  0
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0
parport                46562  3 ppdev,parport_pc,lp
sdhci_pci              18826  0
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
e1000e                156873  0
waldechise@waldechise-Precision-M4700:~$ iwconfig
lo        no wireless extensions.
 
wlan0     IEEE 802.11abgn  ESSID:"FBX_DUPONTP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 82:12:29:F4:31:18   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:40   Missed beacon:0
 
eth0      no wireless extensions.
 
waldechise@waldechise-Precision-M4700:~$ rfkill list
0: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no
1: dell-wifi: Wireless LAN
            Soft blocked: no
            Hard blocked: no
2: dell-bluetooth: Bluetooth
            Soft blocked: no
            Hard blocked: no
3: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
waldechise@waldechise-Precision-M4700:~$ sudo iwlist scan
[sudo] password for waldechise:
lo        Interface doesn't support scanning.
 
wlan0     Scan completed :
          Cell 01 - Address: 82:12:29:F4:31:18
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"FBX_DUPONTP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000eefbc9168
                    Extra: Last beacon: 16636ms ago
                    IE: Unknown: 000B4642585F4455504F4E5450
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000700000000000000000000000000000000000000
 
eth0      Interface doesn't support scanning.
 
waldechise@waldechise-Precision-M4700:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
waldechise@waldechise-Precision-M4700:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

---

### Post by praseodym on 2013-07-17
Deactivate the N-mode of the driver (bug):

```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```
I strongly recommend changing the encryption mode from WEP to WPA2-AES (CCMP) in your router interface. Check the manual for that.

---

### Post by riiicoolaaa on 2013-07-17
Many thanks! It worked fine!

The change in the encryption mode is independent from the changes you made me do?

Cheers,
N

---

### Post by praseodym on 2013-07-17
Yes, its just for security reasons:

[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)

---

