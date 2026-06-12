---
title: "cannot get wireless connection"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by kevin882 on 2011-10-25
Hello,I am running ubuntu studio on a dual boot dell precision t3400.Iam using separate hard drives one for  win xp 32bit and the other for ubuntu studio 11.04 32 bit.I am using a actiontec M1000 with a 2wire wireless dongle.The first install worked automatically but I had to reinstall Ubuntu Studio and now I cannot connect at all.I don't get the list of wireless spots with my connection to choose and the network icon in the right hand corner has a red X in it.

---

### Post by praseodym on 2011-10-25
Hello,

please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by kevin882 on 2011-10-25
Here's the results:



kevin@ubuntu:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
    Subsystem: Dell Precision T3400 [1028:0214]
    Kernel driver in use: tg3
kevin@ubuntu:~$ lsusb
Bus 008 Device 005: ID 5543:0042 UC-Logic Technology Corp. Genius PenSketch 12x9 Tablet
Bus 008 Device 004: ID 413c:2006 Dell Computer Corp. 
Bus 008 Device 003: ID 413c:1004 Dell Computer Corp. 
Bus 008 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 011: ID 19b6:4096 Infotech Logistic, LLC 
Bus 001 Device 008: ID 8086:0510 Intel Corp. Digital Movie Creator
Bus 001 Device 007: ID 03f0:0405 Hewlett-Packard ScanJet 3400cse
Bus 001 Device 006: ID 03f0:8811 Hewlett-Packard 
Bus 001 Device 005: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 0ace:1215 ZyDAS ZD1211B 802.11g
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kevin@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
snd_hda_codec_analog    75442  1 
arc4                   12473  2 
sil164                 13416  0 
lm90                   19452  0 
snd_hda_intel          24140  3 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nouveau               621970  2 
snd_timer              28659  2 snd_pcm,snd_seq
zd1211rw               52419  0 
mac80211              257001  1 zd1211rw
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
ttm                    65184  1 nouveau
hid_uclogic            12677  0 
x38_edac               12960  0 
drm_kms_helper         40745  1 nouveau
drm                   180037  5 sil164,nouveau,ttm,drm_kms_helper
joydev                 17322  0 
lp                     13349  0 
ses                    17137  0 
soundcore              12600  1 snd
ppdev                  12849  0 
dcdbas                 14054  0 
cfg80211              156212  2 zd1211rw,mac80211
enclosure              14656  1 ses
usbhid                 41704  0 
hid                    77084  2 hid_uclogic,usbhid
usblp                  17827  0 
serio_raw              12990  0 
edac_core              42881  2 x38_edac
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
parport_pc             32111  1 
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
parport                36746  3 lp,ppdev,parport_pc
usb_storage            43946  2 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
tg3                   131476  0 
kevin@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
kevin@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
kevin@ubuntu:~$ sudo iwlist scan
[sudo] password for kevin: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:15:05:C7:35:44
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=78/100  Signal level=78/100  
                    Encryption key:on
                    ESSID:"myqwest5297"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000272c70d9f1
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000B6D79717765737435323937
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 40:4A:03:C3:AD:5B
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=10/100  Signal level=10/100  
                    Encryption key:on
                    ESSID:"Kajlabs2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000615824b58d
                    Extra: Last beacon: 496ms ago
                    IE: Unknown: 00084B616A6C61627332
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010555555550000C0A80001404A03C3AD5B102100055A7958454C1023000F5A7958454C2057464144657669636510240007504B353030305A1042000830303030303030311054000800060050F20400011011000A504B353030305A20415010080002008C
          Cell 03 - Address: 00:22:2D:A8:85:F0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/100  Signal level=6/100  
                    Encryption key:on
                    ESSID:"8xx Laurel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001434fed4e8a
                    Extra: Last beacon: 364ms ago
                    IE: Unknown: 000A387878204C617572656C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010042127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000400000000000000000000000000000000000000

kevin@ubuntu:~$ 

Is this what you need ?
THX

---

### Post by praseodym on 2011-10-25
Is the package "linux-firmware" installed? Ubuntu-Studio doesnt use the network-manager per default anymore (did you install it?) because of its permanent scanning. This disturbs the "real time" kernel. Please show:

```
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by kevin882 on 2011-10-25
Yes the firmware for Linux kernel package is installed

Here are the results of the code:

[FONT=monospace]kevin@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet static
    address 192.168.79.1
    netmask 255.255.255.0
    network 192.168.79.0
    broadcast 192.168.79.255
    gateway 192.168.79.1
    # wireless-* options are implemented by the wireless-tools package
    wireless-mode managed
    wireless-essid xxxxxxxxxxx
    wireless-key1 xxxxxxxxxx
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.79.1
    dns-search kebin@home
kevin@ubuntu:~$ cat /etc/resolv.conf
search kebin@home
nameserver 192.168.79.1
kevin@ubuntu:~$ 

[/FONT]

---

### Post by kevin882 on 2011-10-28
I re installed it and I did not try to configure the wireless I left it alone.started the OS and it found my wireless on its own.

---

### Post by praseodym on 2011-10-28
You added the router IP address 192.168.79.1 (see /etc/resolv.conf) as static IP address of your PC (see /etc/network/interfaces)

---

