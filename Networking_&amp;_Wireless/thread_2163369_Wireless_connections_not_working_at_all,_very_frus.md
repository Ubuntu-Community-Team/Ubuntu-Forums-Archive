---
title: "Wireless connections not working at all, very frustrated."
date: 2013-07-18
forum: Networking &amp; Wireless
---

### Post by hotelmason on 2013-07-18
Hello,

I an currently using a Inspiron 1545 Dell laptop. I have tried everything I could to get it working, as in using Windows Wireless drivers, using the methods provided in ubuntuforums.com/showthread.php?t=1966633, and looked up a tutorial for Windows wireless. Please help me, as I want to use Ubuntu wirelessly. Thank you.

---

### Post by praseodym on 2013-07-18
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

### Post by hotelmason on 2013-07-18
uname:
Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
lspci -nnk | grep -iA2 net:
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: sky2
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel modules: ssb
lsusb:
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lsmod:
Module                  Size  Used by
parport_pc             32867  0 
ppdev                  17114  0 
rfcomm                 47562  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
i915                  530857  3 
drm_kms_helper         49259  1 i915
drm                   290344  4 i915,drm_kms_helper
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
gpio_ich               13384  0 
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
snd_hda_codec_idt      70774  1 
coretemp               13642  0 
snd_hda_intel          34117  3 
snd_hda_codec         135141  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
microcode              23030  0 
joydev                 17694  0 
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
i2c_algo_bit           13565  1 i915
wmi                    19257  1 dell_wmi
mac_hid                13254  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
video                  19598  1 i915
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
psmouse               102075  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
lpc_ich                17145  0 
hid_logitech_dj        18768  0 
hid_generic            12541  0 
usbhid                 47259  1 hid_logitech_dj
hid                   100815  3 hid_logitech_dj,hid_generic,usbhid
sky2                   59074  0 
ums_realtek            18257  0 
uas                    18073  0 
usb_storage            49288  1 ums_realtek
iwconfig:
eth0      no wireless extensions.


lo        no wireless extensions.
rfkill list:
Does nothing

Also: the only way to access the internet is by a ethernet cable.

---

### Post by praseodym on 2013-07-18
You only need to install the missing firmware for this card:

```
sudo apt-get install firmware-b43-lpphy-installer 
```
Reboot

---

### Post by hotelmason on 2013-07-18
Ok, I have done this and it still will not list wireless networks for connection. I also have a pending Additional driver that will not activate (Broadcom STA).

---

### Post by praseodym on 2013-07-18
Broadcom STA is not nessecary. Check:
[B]
sudo modprobe b43[/B]

---

### Post by hotelmason on 2013-07-18
It does not do anything.

---

### Post by praseodym on 2013-07-18
Check
```

iwconfig
rfkill list
lsmod
iwlist chan
sudo iwlist scan
dmesg | grep b43
```

---

### Post by hotelmason on 2013-07-18
Update:resolved

---

