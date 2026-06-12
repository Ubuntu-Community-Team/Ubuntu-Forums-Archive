---
title: "Connect wirelessly on live cd but not hard drive install???"
date: 2012-04-07
forum: Networking &amp; Wireless
---

### Post by joemartin on 2012-04-07
my wireless card is a RTL8191 SEvA Wireless LAN Controller..fresh, pangolin install...

help!  anyone know why i can connect on live cd wirelessly but the hard drive install does not have wireless enabled and is not recognizing connections. thanks.

---

### Post by praseodym on 2012-04-07
Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```
Checked the BIOS settings? Maybe resetting it?

---

### Post by joemartin on 2012-04-07
joe@joe-Lenovo-B575:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel driver in use: rtl8192se
joe@joe-Lenovo-B575:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b272 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 1c7a:0603 LighTuning Technology Inc. 
joe@joe-Lenovo-B575:~$ lsmod
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
joydev                 17693  0 
acer_wmi               28418  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
rts5139               351143  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
rtl8192se              93999  0 
psmouse                87603  0 
rtlwifi               118718  1 rtl8192se
serio_raw              13211  0 
mac80211              506816  2 rtl8192se,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211
k10temp                13166  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_hda_codec_conexant    62128  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  1 
ideapad_laptop         18234  0 
fglrx                3263886  97 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  18 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19596  0 
soundcore              15091  1 snd
wmi                    19256  1 acer_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
joe@joe-Lenovo-B575:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

joe@joe-Lenovo-B575:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
joe@joe-Lenovo-B575:~$ sudo iwlist scan

---

### Post by joemartin on 2012-04-07
Thanks for your help praseodym.

---

### Post by joemartin on 2012-04-07
joe@joe-Lenovo-B575:~$ sudo iwlist scan
[sudo] password for joe: 
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2012-04-07
Blacklist this module:

> echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/blacklist-acer_wmi.conf
and reboot.

---

