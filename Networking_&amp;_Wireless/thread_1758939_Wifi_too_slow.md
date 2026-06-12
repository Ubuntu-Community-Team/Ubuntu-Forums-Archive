---
title: "Wifi too slow"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by Pille456 on 2011-05-15
Hi,

I've a "little" problem with my notebook and wlan. First of all, the native ubuntu driver and the proprietary both seem to work correctly. But both seem to work too slow and too unstable according to another notebook in the same network.
I've a 54Mbit/sek network here at home and the other (windows) notebook can send and receive local files with about 1.5mb/sek, which isn't the wlans maximum, but all in all good.
By the way: Wlans maximum speed should be a third of the theoretical maximum, shouldnt it? So I can expect something around 54mbit/s/8 = 6.75mb/sek => 2.25mb/sek?
Next I noticed, that I've too many connection losses. Especially when the notebook runs on battery, it seems to lose the connection every 5min. Also moving around the notebook while being on battery seems too crash the connection all the time. Even if I come closer to the router, the connection speed decreases. 

But first of all, here some console output using the proprietary driver:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:3  Signal level:187  Noise level:173
          Rx invalid nwid:0  invalid crypt:2  invalid misc:0

lsmod
Module                  Size  Used by
michael_mic            12612  8 
arc4                   12529  4 
hidp                   22572  1 
hid                    91020  1 hidp
easy_slow_down_manager    13161  0 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
joydev                 17606  0 
binfmt_misc            17565  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
rfcomm                 47694  8 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  21 hidp,rfcomm,bnep
i915                  514985  3 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
uvcvideo               72195  0 
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         42136  1 i915
lib80211_crypt_tkip    17387  0 
videodev               82052  1 uvcvideo
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
drm                   227495  4 i915,drm_kms_helper
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17078  1 videodev
btusb                  18600  4 
bluetooth              72448  10 hidp,rfcomm,sco,bnep,l2cap,btusb
wl                   2568244  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13400  1 i915
xhci_hcd               77643  0 
soundcore              12680  1 snd
lib80211               14991  2 lib80211_crypt_tkip,wl
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
serio_raw              13166  0 
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
libahci                26642  1 ahci
r8169                  48022  0

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

uname -a Linux Pille-Laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```So first strange thing is, that my wlan-card is named eth1. This is confusing, but okay. Also stuff like Bit Rate, ESSDI etc. are missing, but I still can set "iwconfig eth1 rate 54M" and so on. Also it say, that there is no associated access-point, but I'm currently using my notebook to write this thread... o.O
I already tried to set some parameters by hand like "iwconfig eth1 rate 54M" and "iwconfig eth1 power off", but nothing helped.
Anyone an idea whats going on here?

Should I maybe try to install the windows driver or would that be the same as the proprietary already is?

Greetings
Pille456

---

