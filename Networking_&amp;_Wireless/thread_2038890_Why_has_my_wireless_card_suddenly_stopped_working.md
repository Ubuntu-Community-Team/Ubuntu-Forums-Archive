---
title: "Why has my wireless card suddenly stopped working?"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by Wischyre on 2012-08-07
Right now, I'm in the corner of the room with an Ethernet cable plugged into my laptop. I recently installed Ubuntu 12.04 (64 bit) on my laptop, removing Windows. Everything worked fine for a day or two, until I updated and my wireless card suddenly stopped working after a restart. I should also mention that this card is the same wireless card that came with my laptop. I haven't made any hardware modifications to this laptop since I got it.

I'm using a Ralink RT 5390. I've searched around, and I can't seem to find anyone with the same problem.

I'd really appriceate some help. I don't really have much of an idea of where to start. I can provide additional information at request.

Thanks in advance.

---

### Post by praseodym on 2012-08-07
Please show the terminal outputs of

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by Wischyre on 2012-08-07
> **praseodym said:**
> Please show the terminal outputs of

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

```

~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1657]
	Kernel driver in use: r8169
--
0d:00.0 Network controller [0280]: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip] [1814:539f]
	Subsystem: Hewlett-Packard Company Pavilion DM1Z-3000 PCIe wireless card [103c:1637]
	Kernel driver in use: rt2800pci

```

```

~$ lsmod
Module                  Size  Used by
rt2500usb              27294  0 
rt2x00usb              20762  1 rt2500usb
rt61pci                32257  0 
crc_itu_t              12707  1 rt61pci
btusb                  18288  2 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
bluetooth             180104  23 btusb,rfcomm,bnep
binfmt_misc            17540  1 
ext2                   73795  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
fglrx                3263886  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                87692  0 
serio_raw              13211  0 
hid_logitech_dj        18594  0 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  2 rt61pci,rt2800pci
rt2x00lib              51144  6 rt2500usb,rt2x00usb,rt61pci,rt2800pci,rt2800lib,rt2x00pci
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              506816  4 rt2x00usb,rt2800lib,rt2x00pci,rt2x00lib
rts_pstor             445196  0 
cfg80211              205544  2 rt2x00lib,mac80211
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
eeprom_93cx6           12725  2 rt61pci,rt2800pci
mei                    41616  0 
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_crypt               23125  2 
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
i915                  472897  2 
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
r8169                  62099  0 
i2c_algo_bit           13423  1 i915
wmi                    19256  1 hp_wmi
video                  19596  1 i915

```

```

~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"linksys_SES_2882"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:EE:A9:DF   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:42   Missed beacon:0

eth0      no wireless extensions.

```

```

~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by praseodym on 2012-08-07
Wow, a lot of drivers loaded. Prvent the wrong ones from being loaded in future:

> echo -e "blacklist rt2500pci\nblacklist rt61pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
and reboot.

---

### Post by Wischyre on 2012-08-07
> **praseodym said:**
> Wow, a lot of drivers loaded. Prvent the wrong ones from being loaded in future:


and reboot.

After doing this and rebooting, the network failed to load on startup again(with the Ethernet cable still plugged in).


After waiting several minutes and running the following two commands several times:

```

sudo /etc/init.d/networking start
```

and

```

sudo start networkig 
```

it finally established a connection through the Ethernet cable.

Nothing seems to have changed.

---

### Post by praseodym on 2012-08-07
Try it without cable. Alternatively, try this driver (or with "dkms" as described below):

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)

---

