---
title: "D-LINK DWA-123 slow wireless connection"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2012-02-20
I have D-LINK DWA-123 wireless USB stick. It seems that the driver used is rt2800usb:
```
enedene@laptop:~$ lsmod
Module                  Size  Used by
iwlagn                273980  0 
btusb                  18160  2 
snd_hrtimer            12648  1 
rfcomm                 38408  12 
bnep                   17923  2 
bluetooth             148839  23 btusb,bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
dm_crypt               22565  1 
nvidia              10390874  32 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  3 
snd_hda_codec          91859  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
iwl3945                73360  0 
arc4                   12473  4 
rt2800usb              22222  0 
rt2800lib              48909  1 rt2800usb
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
iwl_legacy             71499  1 iwl3945
stkwebcam              23296  0 
crc_ccitt              12595  1 rt2800lib
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48146  3 rt2800usb,rt2800lib,rt2x00usb
snd                    55902  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               85626  1 stkwebcam
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
joydev                 17393  0 
r592                   17808  0 
memstick               15857  1 r592
mac80211              393421  6 iwlagn,iwl3945,rt2800lib,iwl_legacy,rt2x00usb,rt2x00lib
cfg80211              172427  5 iwlagn,iwl3945,iwl_legacy,rt2x00lib,mac80211
tpm_infineon           13200  0 
psmouse                73673  0 
serio_raw              12990  0 
asus_laptop            19050  0 
sparse_keymap          13658  1 asus_laptop
tpm_tis                14002  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35854  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
video                  18908  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  43104  0

```
The connection is very slow, up to 100kB/s. Is there a way to fix this? 
```
uname -a
Linux laptop 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux
```
I've just tried installing new kernel:
```
uname -a
Linux linux 3.3.0-030300rc4-generic #201202181935 SMP Sun Feb 19 00:44:42 UTC 2012 i686 i686 i386 GNU/Linux
```
The problem stays the same.

---

### Post by gordintoronto on 2012-02-20
How are you measuring the connection speed? Are there other computers on your network which run faster?

What does lsusb produce? Are you sure you're plugged into a USB 2.0 port?

---

### Post by praseodym on 2012-02-20
There is an Intel card also inside (TM) ;-)

Try this UDEV-rule:

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

Change twice "b43" with "iwlagn" without quotas.

Edit: Additionally there is another one, named "iwl3945". What card is that?

```
lspci -nnk | grep -iA2 net
lsusb
```

please.

---

### Post by ene_dene on 2012-02-20
> **gordintoronto said:**
> How are you measuring the connection speed? 
Speedtest, download of a big file, slow surfing speed.
> Are there other computers on your network which run faster?
Affirmative. Cable and wireless both, I have 8Mbit connection.

> What does lsusb produce? Are you sure you're plugged into a USB 2.0 port?
Yes, I've tried it on a new desktop computer too.
```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e1:0501 Syntek Semiconductor Co., Ltd DC-1125 Webcam
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 001 Device 006: ID 2001:3c17 D-Link Corp.
```

[QUOTE=praseodym]There is an Intel card also inside (TM) ...[/QUOTE]
Yes, and that one is also limited to about 100kB/s. But I've tried this card on my desktop, without any wireless cards as well, and I get the same result.

Btw, the problem is not with wireless router as I have another laptop with full 54Mbit speeds also.

---

### Post by gordintoronto on 2012-02-21
> **ene_dene said:**
> 
```
lsmod
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e1:0501 Syntek Semiconductor Co., Ltd DC-1125 Webcam
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
```


I don't see a wireless adapter here. Did you unplug it?

lsmod??? Looks like lsusb output.

---

### Post by ene_dene on 2012-02-22
> **gordintoronto said:**
> I don't see a wireless adapter here. Did you unplug it?

lsmod??? Looks like lsusb output.
yes it's lsusb, my mistake, you've asked for it in your first post. lsmod was in my first post. I didn't unplug it. Here it is one more time:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05e1:0501 Syntek Semiconductor Co., Ltd DC-1125 Webcam
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
**Bus 001 Device 006: ID 2001:3c17 D-Link Corp.** 
```

---

### Post by ene_dene on 2012-02-22
> **praseodym said:**
> 
```
lspci -nnk | grep -iA2 net
lsusb
```

please.
```

lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
	Subsystem: ASUSTeK Computer Inc. A6J-Q008 [1043:11f5]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

```

---

### Post by praseodym on 2012-02-22
The stick could be a Realtek or Atheros chipset. Please show

> lsmod
with stick

---

### Post by gordintoronto on 2012-02-22
It's an RT2800, based on 2001:3c17 in the lsusb. But you appear to also have a built-in Intel wireless adapter?

---

### Post by ene_dene on 2012-02-23
> **praseodym said:**
> The stick could be a Realtek or Atheros chipset. Please show


with stick
Look at mine 1st post.
[QUOTE=gordintoronto]It's an RT2800, based on 2001:3c17 in the lsusb. But you appear to also have a built-in Intel wireless adapter?[/QUOTE]
Yes, and as I've said, I've tried the USB stick on a computer without any wireless adapters and I experience the same problem of slow internet connection.

---

### Post by JohnH on 2012-08-24
I can confirm this on my machine. I have two different D-Link usb wireless sticks and they both are slow and stall since 12.04 install. There was never a problem on my 11.10 box. 

There are serious issues with the kernel I suspect. I tried ndswrapper as well but it killed the wireless althogether despite black listing the driver.

It is a very annoying problem.

John

---

