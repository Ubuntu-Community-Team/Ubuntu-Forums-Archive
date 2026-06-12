---
title: "Wireless not working on ThinkPad X220 / Intel Centrino Wireless-N 1000"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by lucacerone on 2013-02-13
Dear all,
I recently got a ThinkPad X220 on which I installed Ubuntu 12.04 64 bit.

Everything works just fine except for the wireless.
In the Systems Settings menu "Enable Wireless" is grayed out
and I can't enable it, not even pressing FN+F5 (that on my laptop
enables and disables the wireless).

I don't know where to start to diagnose the problem and give you
some more useful information, but I would be very grateful if you could help me solve this issue.

Thanks a lot in advance for your help!
Luca

---

### Post by praseodym on 2013-02-13
Please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by lucacerone on 2013-02-14
Thanks praseodym,
here are the outputs how the commands:

```

uname -a
Linux figaro 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21ce]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
	Kernel driver in use: iwlwifi

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b217 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0bc2:2300 Seagate RSS LLC 

lsmod
Module                  Size  Used by
uas                    18180  0 
usb_storage            49198  1 
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62358  1 
joydev                 17693  0 
rfcomm                 46621  0 
bnep                   18139  2 
bluetooth             185622  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
arc4                   12529  2 
iwlwifi               330041  0 
mac80211              514621  1 iwlwifi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
cfg80211              209821  2 iwlwifi,mac80211
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                97485  0 
serio_raw              13211  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
thinkpad_acpi          81819  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
nvram                  14413  1 thinkpad_acpi
tpm_tis                18804  0 
i915                  477602  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
wmi                    19256  0 
i2c_algo_bit           13423  1 i915
mei                    41616  0 
video                  19596  1 i915
mac_hid                13253  0 
coretemp               13525  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156873  0

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

I honestly don't understand at all the output of these commands.
If you figure out what it means, could you please also tell me what I checked and what the answers need (so I learn something, while fixing the issue).

Thanks a lot again for the help!

---

### Post by praseodym on 2013-02-14
Try

```
sudo rfkill unblock all
```

Check:
```

rfkill list
```

---

### Post by lucacerone on 2013-02-14
Thanks praseodym,
here is the output (I see something has changed to soft blocked, but not
to hard blocked).
```

 sudo rfkill unblock all
 rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

---

### Post by praseodym on 2013-02-14
Please check here:

[http://ubuntuforums.org/showthread.php?t=2111690](http://ubuntuforums.org/showthread.php?t=2111690)

Posting #6

---

### Post by lucacerone on 2013-02-14
Hi praseodym,
unfortunately none of the 3 solutions listed in the post you linked has worked.

The hard block is still set.

---

### Post by praseodym on 2013-02-14
Try to press Fn+F5 continously or permanently durin boot-up. Is it a dualboot-system? If yes, maybe Windows is shutting down the card?

---

### Post by lucacerone on 2013-02-14
The machine has only Ubuntu on it and pressing FN+F5 during
boot (both continuously or permanently) doesn't do anything.

---

### Post by praseodym on 2013-02-14
Check these sites:

[http://thinkwiki.de/Ubuntu_ThinkPad_Extras_PPA](http://thinkwiki.de/Ubuntu_ThinkPad_Extras_PPA)

[http://thinkwiki.de/Ubuntu_tp-Kernel](http://thinkwiki.de/Ubuntu_tp-Kernel)

---

### Post by lucacerone on 2013-02-15
Thanks praseodym.
I installed the linux-headers and images in the repository,
but this didn't solve the issue.

Other ideas?

---

### Post by praseodym on 2013-02-15
Try to unload this module:
```

sudo rmmod thinkpad_acpi
```
If the system crashes, reboot.

---

### Post by lucacerone on 2013-02-15
thanks,
the system hasn't crashed, but nothing happened...

---

### Post by praseodym on 2013-02-15
Now check the solutions from above again, starting with
```

sudo rfkill unblock all
```

---

### Post by lucacerone on 2013-02-18
Unfortunately nothing seems to work...

---

### Post by praseodym on 2013-02-18
Did you check the switch on the left side (front)?

---

### Post by lucacerone on 2013-02-18
..the awkward moment when I feel completely stupid..
of course it was the switch.. (..it took me a while to understand which was
the switch though...)

Sorry to have bothered you, and thanks for the patience!!!

---

