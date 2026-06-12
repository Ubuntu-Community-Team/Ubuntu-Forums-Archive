---
title: "Losing wireless connection after updates"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by capateke on 2013-02-13
I am using 12.04 LTS on a Toshiba Satellite laptop. I have installed the driver for the RealTek wireless card successfully, but every time I install system updates with Update Manager I lose the wireless connection and have to re-install the driver. Why is this happening and is there anything I can do to remedy this problem?

---

### Post by praseodym on 2013-02-13
Which driver did you install? Please show:
```

lspci -nnk | grep -iA2 net
uname -a
lsmod
```

---

### Post by capateke on 2013-02-26
Sorry for delay:I have been away. The kernel driver for the network controller is rtl8723e.
capateke@capateke-SATELLITE-L850D-12P:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
	Kernel driver in use: rtl8723e
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fb37]
	Kernel driver in use: r8169
capateke@capateke-SATELLITE-L850D-12P:~$ uname -a
Linux capateke-SATELLITE-L850D-12P 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
capateke@capateke-SATELLITE-L850D-12P:~$ lsmod
Module                  Size  Used by
dm_crypt               23125  1 
bnep                   18281  2 
parport_pc             32866  0 
rfcomm                 47604  12 
ppdev                  17113  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_hda_codec_realtek   224173  1 
arc4                   12529  2 
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_hdmi     32474  1 
joydev                 17693  0 
rtl8723e              175439  0 
snd_seq_midi           13324  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtlwifi               118798  1 rtl8723e
btusb                  18332  2 
snd_rawmidi            30748  1 snd_seq_midi
bluetooth             180153  23 bnep,rfcomm,btusb
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              17764  1 snd_hda_codec
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              506862  2 rtl8723e,rtlwifi
cfg80211              205774  2 rtlwifi,mac80211
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97485  0 
serio_raw              13211  0 
sparse_keymap          13890  0 
lp                     17799  0 
mac_hid                13253  0 
parport                46562  3 parport_pc,ppdev,lp
i2c_piix4              13301  0 
toshiba_bluetooth      12807  0 
k10temp                13166  0 
snd_timer              29990  2 snd_seq,snd_pcm
fglrx                3264017  125 
snd                    79041  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
vesafb                 13844  1 
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 
ums_realtek            18248  0 
wmi                    19256  0 
video                  19651  0 
usb_storage            49198  1 ums_realtek
capateke@capateke-SATELLITE-L850D-12P:~$

---

### Post by praseodym on 2013-02-26
You need to compile again after a kernel upgrade

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

