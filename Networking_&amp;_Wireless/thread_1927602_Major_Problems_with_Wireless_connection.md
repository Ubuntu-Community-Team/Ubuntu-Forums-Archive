---
title: "Major Problems with Wireless connection"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by 3v3rgr33n on 2012-02-18
Hi
 
Im using Natty Narwhal, Im experiencing some problems wit the wireless connection. The last time i used my PC was last year, Nov and the wireless was fine. I jst got my PC back and its not connecting to all wireless networks. When i tried using Windows, The very same network had a very strong signal and wasnt giving me hassles. 
 
On Ubuntu, it keeps asking for my credentials to connect to the network, even after typing them correctly it jst continues to do the same thing until its disconnects me. Im using a samsung RV510 notebook, dual booting Ubuntu 11.04 and Windows 7.
 
Please help!!

---

### Post by carl4926 on 2012-02-18
Is this the same Ubuntu installation that you were using last year when it was working?

Try deleting all wireless access point entries in your wireless connections
And start again.

What device is it?
```
lspci -nnk | grep -iA2 net
```

---

### Post by josephmills on 2012-02-18
> **3v3rgr33n said:**
> Hi
 
Im using Natty Narwhal, Im experiencing some problems wit the wireless connection. The last time i used my PC was last year, Nov and the wireless was fine. I jst got my PC back and its not connecting to all wireless networks. When i tried using Windows, The very same network had a very strong signal and wasnt giving me hassles. 
 
On Ubuntu, it keeps asking for my credentials to connect to the network, even after typing them correctly it jst continues to do the same thing until its disconnects me. Im using a samsung RV510 notebook, dual booting Ubuntu 11.04 and Windows 7.
 
Please help!!

Hello there evergreen I went to a college called evergreen in oly. 
 lets try this boot ubuntu and open a terminal```
lspci -nn && lsmod && lsusb && rfkill list all && uname -a 
``` then paste that all here. thanks

---

### Post by 3v3rgr33n on 2012-02-19
> **josephmills said:**
> 
lets try this boot ubuntu and open a terminal```
lspci -nn && lsmod && lsusb && rfkill list all && uname -a 
``` then paste that all here. thanks
 
This is what i got
```
[FONT=LiberationSerif]
[LEFT]00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub
[8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated
Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics
Controller [8086:2a43] (rev 09)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4
[8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5
[8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6
[8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2
[8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
[8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1
[8086:2940] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5
[8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6
[8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1
[8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2
[8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3
[8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1
[8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller
[8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930]
(rev 03)
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet
Controller [11ab:4354]
06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN
Controller [14e4:4727] (rev 01)
Module Size Used by
nls_iso8859_1 12617 1
nls_cp437 12751 1
vfat 17335 1
fat 55505 1 vfat
sha256_generic 20911 2
cryptd 19801 0
aes_i586 16956 207
aes_generic 38023 1 aes_i586
parport_pc 32111 0
ppdev 12849 0
dm_crypt 22463 1
snd_hda_codec_realtek 255820 1
rfcomm 38125 8
binfmt_misc 13213 1
snd_hda_intel 24140 2
arc4 12473 2
snd_hda_codec 90901 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13274 1 snd_hda_codec
sco 17779 2
bnep 17785 2
snd_pcm 80244 2 snd_hda_intel,snd_hda_codec
l2cap 48656 16 rfcomm,bnep
snd_seq_midi 13132 0
snd_rawmidi 25269 1 snd_seq_midi
brcm80211 690428 0
uvcvideo 66851 0
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event
mac80211 257001 1 brcm80211
btusb 18160 2
snd_timer 28659 2 snd_pcm,snd_seq
psmouse 73312 0
bluetooth 65565 9 rfcomm,sco,bnep,l2cap,btusb
videodev 75143 1 uvcvideo
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq
joydev 17322 0
cfg80211 156212 2 brcm80211,mac80211
serio_raw 12990 0
snd 55295 13
snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,s
nd_timer,snd_seq_device
soundcore 12600 1 snd
snd_page_alloc 14073 2 snd_hda_intel,snd_pcm
lp 13349 0
parport 36746 3 parport_pc,ppdev,lp
usb_storage 43946 1
usbhid 41704 0
hid 77084 1 usbhid
uas 17676 0
i915 450944 3
ahci 21591 2
drm_kms_helper 40745 1 i915
sky2 49172 0
drm 180037 4 i915,drm_kms_helper
libahci 25548 1 ahci
i2c_algo_bit 13184 1 i915
video 18951 1 i915
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 040b:2013 Weltrend Semiconductor
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a5c:219c Broadcom Corp.
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0/HT203
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0ac8:c33f Z-Star Microelectronics Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
Linux 5R33N 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386[/LEFT]
GNU/Linux
[/FONT]
```

---

### Post by 3v3rgr33n on 2012-02-20
:D I found out what the problem was... The wireless Drivers were removed. I installed them and everything is fine..

I can connect only to the intranet, the problem is that firefox doesnt give me that pop-up window which allows me to enter my login details for the wireless. plz help!

---

### Post by mahawksid on 2012-02-20
Is your Bluetooth working?
Cause i too have Broadcom`s BCM-4313 adapter. And i am not able to connect to bluetooth.

---

### Post by 3v3rgr33n on 2012-02-20
> **mahawksid said:**
> Is your Bluetooth working?
i am not able to connect to bluetooth.

YeP!! its A-Okay

---

