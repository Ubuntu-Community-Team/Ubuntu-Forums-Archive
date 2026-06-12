---
title: "Wireless network connected but doesn't work"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by Luxxor on 2013-04-06
I just installed Ubuntu on my PC. I can normally connect my wireless network to the computer, and it shows up in the top bar; two of three stripes. However, Firefox fails to load pages, and the software centre is unable to download software, even though it does succeed in browsing through and searching for applications. I tried to use my phone as a wireless hotspot, and when I connected the computer to that network, I didn't experience these problems any more. Another peculiarity is that when the installation of the OS was finished it was able to install the available updates.

PC: HP Pavilion Slimline (desktop) with Windows 7.

---

### Post by praseodym on 2013-04-06
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -r
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Edit: Can you connect via cable?

---

### Post by Luxxor on 2013-04-06
I typed in the commands and these are the outputs:

uname -r
```

3.5.0-26-generic

```

lspci -nnk | grep -iA2 net
```

02:00.0 Ethernet controller [0200]: Realtek SemiconductorCo., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136](rev 02)
            Subsystem:Hewlett-Packard Company Device [103c:2a9d]
            Kerneldriver in use: r8169

```

lsusb
```

Bus 001 Device 002: ID 0b05:1723 ASUSTek Computer, Inc.WL-167G v2 802.11g Adapter [Ralink RT2571W]
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. MultiFlash Reader
Bus 003 Device 002: ID 0461:4de2 Primax Electronics, Ltd
Bus 003 Device 003: ID 04ca:0050 Lite-On Technology Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub

```

lsmod
```

Module                 Size  Used by
bnep                   18141  2
rfcomm                46620  0
bluetooth            209249  10 bnep,rfcomm
arc4                  12530  2
parport_pc            32689  0
ppdev                 17074  0
rt73usb               31297  0
snd_hda_codec_hdmi     32049 1
crc_itu_t             12708  1 rt73usb
rt2x00usb             20665  1 rt73usb
snd_hda_codec_realtek   78147  1
rt2x00lib             54939  2 rt73usb,rt2x00usb
snd_hda_intel         33492  15
snd_hda_codec        134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
radeon               895730  10
coretemp              13401  0
snd_hwdep             17699  1 snd_hda_codec
mac80211             540032  2 rt2x00usb,rt2x00lib
snd_pcm               96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi          13325  0
snd_rawmidi           30513  1 snd_seq_midi
snd_seq_midi_event    14900  1 snd_seq_midi
cfg80211             206797  2 rt2x00lib,mac80211
snd_seq               61555  2 snd_seq_midi,snd_seq_midi_event
gpio_ich              13384  0
snd_timer             29426  2 snd_pcm,snd_seq
snd_seq_device        14498  3snd_seq_midi,snd_rawmidi,snd_seq
kvm                  414071  0
ttm                   83596  1 radeon
drm_kms_helper        49113  1 radeon
snd                   78921  40snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                  288721  12 radeon,ttm,drm_kms_helper
joydev                17458  0
soundcore             15048  1 snd
psmouse               95595  0
lpc_ich               17062  0
snd_page_alloc        18485  2 snd_hda_intel,snd_pcm
serio_raw             13216  0
i2c_algo_bit          13414  1 radeon
microcode             22804  0
mac_hid               13206  0
ext2                  72881  1
lp                    17760  0
parport               46346  3 parport_pc,ppdev,lp
hid_generic           12541  0
usbhid                46987  0
hid                  100411  2 hid_generic,usbhid
usb_storage            48834 0
r8169                 61651  0
 
iwconfig
eth0      no wirelessextensions.
 
lo        no wirelessextensions.
 
wlan0     IEEE802.11bg  ESSID:"SouerNet"  
         Mode:Managed  Frequency:2.427GHz  Access Point: 00:24:FE:A7:3D:0B   
          Bit Rate=54Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7  RTS thr:off   Fragment thr:off
          PowerManagement:on
          LinkQuality=54/70  Signal level=-56 dBm  
          Rx invalidnwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessiveretries:0  Invalid misc:632   Missed beacon:0

```

rfkill list
```

0: phy0: Wireless LAN
            Softblocked: no
            Hardblocked: no

```

When I connect the computer with my router with a cable, the connection doesn't seem to be recognized by the OS. I don't know if that problem is related to the initial one, though. It could be the wire that's broken.

---

### Post by praseodym on 2013-04-06
```
          PowerManagement:on
```
Deactivate the PM:
```

sudo iwconfig wlan0 power off
```
Maybe there is a MAC-address filter activated which blocks the LAN connection? Check the settings in your router interface.

---

### Post by Luxxor on 2013-04-06
It works now. Firefox loads pages and the software centre can download applications. Thank you very much for the help.

---

