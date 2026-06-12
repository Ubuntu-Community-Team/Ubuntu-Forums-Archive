---
title: "can't scan for wireless network"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by hilaryprinzen on 2011-09-27
I just installed ubuntu 11.04 and since then my wireless internet connection will randomly disconnect after no activity on my computer. I don't have an issue with this, but just yesterday it shut off and won't reconnect. i have wireless enabled on my laptop, but no networks show up that i can connect to (i know i'm in range of about 5). the internet still works with the ethernet cable. any suggestions on how to get my wireless to respond? i'm completely lost on this one. thanks

---

### Post by praseodym on 2011-09-27
Hi,

please show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by hilaryprinzen on 2011-09-28
hilary@hilary-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:145c]
	Kernel modules: brcm80211
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:144c]
	Kernel driver in use: r8169
hilary@hilary-laptop:~$ lsusb
Bus 002 Device 003: ID 0408:03b2 Quanta Computer, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hilary@hilary-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          28209  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  451068  8 
snd_seq_midi           13132  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
psmouse                59039  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  1 uvcvideo
drm                   184164  4 i915,drm_kms_helper
serio_raw              12990  0 
intel_ips              17769  0 
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               21632  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
lis3lv02d              19285  1 hp_accel
input_polldev          13735  1 lis3lv02d
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
r8169                  46630  0 
libahci                25548  1 ahci
hilary@hilary-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

hilary@hilary-laptop:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
hilary@hilary-laptop:~$ sudo iwlist scan
[sudo] password for hilary: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2011-09-28
Ok,

blacklist the following driver:

```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and activate the Broadcom-STA-driver via "Additional drivers". You need a cable connection for that.

---

### Post by hilaryprinzen on 2011-09-28
it worked! thank you so much for helping!

---

