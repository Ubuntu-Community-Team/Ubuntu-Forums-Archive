---
title: "Wifi disable"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by serkanqw on 2011-09-08
Dear All, 
My problem is following; Wifi switch at my Acer aspire one AOA150/ZG5 is not working. How can I make it work? 
Best regards, 
Serkan

---

### Post by praseodym on 2011-09-08
Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by serkanqw on 2011-09-08
serkanqw@serkanqw-AOA150:~$ rfkill listlspci -nnk | grep -iA2 net
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
serkanqw@serkanqw-AOA150:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c50a Logitech, Inc. Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
serkanqw@serkanqw-AOA150:~$ lsmod
Module                  Size  Used by
usbhid                 41704  0 
hid                    77084  1 usbhid
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
i915                  451033  3 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
ath5k                 144534  0 
snd_seq_midi           13132  0 
ath                    19141  1 ath5k
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 ath5k
drm_kms_helper         40745  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm                   184164  4 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  3 ath5k,ath,mac80211
acerhdf                14217  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  42534  0 
serkanqw@serkanqw-AOA150:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by praseodym on 2011-09-08
Please show one by one:

```
rfkill list
lspci -nnk | grep -iA2 net
```

> Tx-Power=off means there is a button/switch key combination, etc.

---

### Post by serkanqw on 2011-09-08
serkanqw@serkanqw-AOA150:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
serkanqw@serkanqw-AOA150:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:015b]
    Kernel driver in use: r8169
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e008]
    Kernel driver in use: ath5k

---

### Post by praseodym on 2011-09-08
Check:

```
sudo rfkill unblock all
sudo service network-manager restart
```
controls:

```
iwconfig
rfkill list
```

---

### Post by serkanqw on 2011-09-08
serkanqw@serkanqw-AOA150:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
serkanqw@serkanqw-AOA150:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by praseodym on 2011-09-08
Try to do the following one by one:

[LIST]
[*]hold the button pressed while booting

[*]press the button several times while booting

[*]reset your BIOS to default settings
[/LIST]

---

### Post by serkanqw on 2011-09-08
Dear Praseodym
Thank you for your reply. 

hold the button pressed while booting is just work fine.

Wi-fi is now working.

serkanqw@serkanqw-AOA150:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Best regards,
Serkan

---

### Post by praseodym on 2011-09-08
Does it work now without pressing the button while booting?

---

### Post by serkanqw on 2011-09-08
I hold button from booting till ubuntu starts.

---

