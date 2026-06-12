---
title: "Wireless Device Not Ready (firmware missing)"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by askarlupka on 2011-09-04
Before attempting to help me, please realize that I am completely new. I figured out only three days ago what a terminal window was and how to open one. You have been warned.

I'm running ubuntu through windows on my dell laptop. I have a linksys router for home use. I can establish a connection from the main internet source to the laptop, and from the main internet source through the router then to the computer. These are both wired connections. I however, cannot get a wireless connection. 

In windows it connects, so the router is not malfunctioning. But its does have a passcode because its a wpa2 security, does that have anything to do with it? 

I keep attempting to follow other threads and tutorial but they never seem to work. I tried to connect it through the router so that the additional drivers would figure out what driver it needed but that didn't work out either. Help!

---

### Post by praseodym on 2011-09-04
Hello,

can you post the following terminal outputs (put them via copy/paste into it):

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by askarlupka on 2011-09-04
> **praseodym said:**
> Hello,

can you post the following terminal outputs (put them via copy/paste into it):

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
sudo iwlist scan
```



 lspci -nnk | grep -iA2 net


04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Dell Device [1028:02be]
    Kernel driver in use: tg3




lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6417 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lsmod

Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
rfcomm                 47694  8 
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_idt      71137  1 
btusb                  18600  2 
bluetooth              72448  9 rfcomm,sco,bnep,l2cap,btusb
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
b43                   318638  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
i915                  514985  3 
mac80211              294370  1 b43
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42136  1 i915
dell_wmi               12681  0 
r852                   18246  0 
sm_common              16817  1 r852
uvcvideo               72195  0 
sparse_keymap          13898  1 dell_wmi
nand                   55112  2 r852,sm_common
dell_laptop            13827  0 
nand_ids               12723  1 nand
nand_ecc               13230  1 nand
videodev               82052  1 uvcvideo
drm                   227495  4 i915,drm_kms_helper
dcdbas                 14438  1 dell_laptop
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    27900  2 sm_common,nand
cfg80211              178528  2 b43,mac80211
psmouse                73535  0 
soundcore              12680  1 snd
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
tg3                   141750  0 
firewire_ohci          40370  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
firewire_core          62646  1 firewire_ohci
ssb                    51945  1 b43
crc_itu_t              12707  1 firewire_core
ahci                   25951  1 
libahci                26642  1 ahci






rfkill list

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr:off
          Power Management:off




sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

---

### Post by wildmanne39 on 2011-09-04
Hi, welcome to the forum, if you have a wired connection run these two commands please:
```
sudo apt-get update && sudo apt-get upgrade
```
after it completes run this command
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
then disconnect your wired connection and restart your computer if this fixes your problem please use thread tools at the top of the page and mark thread solved if not post back and we will go from there.
Thank you

---

### Post by nm_geo on 2011-09-04
Removed - Already answered

---

### Post by northd_tech on 2011-09-04
> **askarlupka said:**
> 
lsmod

Module                  Size  Used by
b43                   318638  0 
mac80211              294370  1 b43
[COLOR=Red][B]dell_wmi               12681  0 
dell_laptop            13827  0 [/B][/COLOR]
cfg80211              178528  2 b43,mac80211

rfkill list

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

sudo iwlist scan
wlan0     Interface doesn't support scanning : Network is down
There is a chance one or both of those Dell modules I highlighted [COLOR=Red]**in red **[/COLOR][COLOR=Black]above is causing wireless difficulties- I'll need to search the forum here for some info on that.

It might also help to see the output of this terminal command:

[/COLOR]```
dmesg | egrep 'b43|irmware|wl'
```

---

### Post by wildmanne39 on 2011-09-04
Hi northd_tech I was just wondering do you have your private messaging disabled?

---

### Post by garvinrick4 on 2011-09-04
In synaptics type b43 in search window these are the two for your card by wildmanne39 if anymore installed remove
and reboot with wired removed. Just in case.

---

### Post by northd_tech on 2011-09-04
> **wildmanne39 said:**
> Hi northd_tech I was just wondering do you have your private messaging disabled?
No it should be working- I saw your PM last night about CDB but I received a long distance phone call from my little brother (who just moved to Alaska for college this week), so I needed to talk to him for quite a while last night and email him some things.

---

### Post by wildmanne39 on 2011-09-04
Hi, ok I thought maybe it was turned off there is a setting to turn it off.

---

### Post by wildmanne39 on 2011-09-04
Hi one other thing if it does not work post the results of this command please:
```
cat /etc/lsb-release; uname -a
```
Thank you

---

### Post by denisk on 2012-05-28
> **wildmanne39 said:**
> Hi, welcome to the forum, if you have a wired connection run these two commands please:
```
sudo apt-get update && sudo apt-get upgrade
```after it completes run this command
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```then disconnect your wired connection and restart your computer if this fixes your problem please use thread tools at the top of the page and mark thread solved if not post back and we will go from there.
Thank you

Had the same problem with Lubuntu 12.04 and old Dell Studio, and this fixed it. Thanks!

---

