---
title: "Broadcom BCM4312"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by endtheembargo on 2013-05-18
Hey friends,

First, I am the noobiest of noobs so I´ll need you to explain things as simply as possible.

I am running ubuntu 12.04 on a dell inspiron mini netbook. I´ve been connecting just fine to the internet until today, after I installed some updates (don´t know what they were). At any rate, what happens is that my computer behaves like it is trying to connect to the wireless internet but in the end times out.

I have tried to reseach this myself online but any problem that other people have had that looks remotely like what I[m dealing with, doesnt have a resolution that i understand.

I am traveling abroad and desperately need to be able to access the internet.

Any ideas on what I should do?

Thanks!!

---

### Post by cortman on 2013-05-18
Please post the output of

```

lspci

```

and

```

lsmod

```

---

### Post by endtheembargo on 2013-05-18
lspci yielded as follows (i had to type all of this in btw!)

00:00.0 Host bridge: Intel corporation N10 family DMI bridge
00:02.0 VGA compatible controller: Intel corporation N10 family integrated graphics controller
00:02.1 display controller: intel corporation N10 family integrated graphic controller
00:1b.0 Audio device: Intel corporation N10/ICH 7 family high definition audio controller (rev 02)
00:1c.1 PCI bridge: intel corporation  N10/ICH 7 family PCI express port 1 ( rev 02)
00:1d.0 USB controller:  intel corporation  N10/ICH 7 family USB UHCI controler # 1 (revo2)

---

### Post by endtheembargo on 2013-05-18
sorry is there specific things youre looking for? i am using a spanish keyboard to try and type in all of this output code and its really frustrating

---

### Post by cortman on 2013-05-18
I'm looking to see what modules are loaded and what hardware is detected. Go ahead and post it in Spanish. It shouldn't make much difference.

---

### Post by endtheembargo on 2013-05-19
Ok, sorry that took me so long here is the outcome

ondinequinn@OndinesComputer:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
ondinequinn@OndinesComputer:~$ 


ondinequinn@OndinesComputer:~$ lsmod
Module                  Size  Used by
michael_mic            12541  0 
arc4                   12474  0 
joydev                 17394  0 
coretemp               13362  0 
snd_hda_codec_realtek    64959  1 
snd_hda_intel          32983  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            17210  0 
compal_laptop          19316  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14099  1 dell_laptop
lib80211_crypt_tkip    17276  0 
bnep                   17791  2 
rfcomm                 38104  0 
parport_pc             32115  0 
bluetooth             189585  10 bnep,rfcomm
ppdev                  12850  0 
i915                  474913  3 
microcode              18396  0 
uvcvideo               72249  0 
drm_kms_helper         47459  1 i915
videobuf2_core         32212  1 uvcvideo
psmouse                91022  0 
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   240232  4 i915,drm_kms_helper
videodev              100265  2 uvcvideo,videobuf2_core
option                 25738  0 
wl                   2906598  0 
serio_raw              13032  0 
videobuf2_vmalloc      12757  1 uvcvideo
usb_wwan               19532  1 option
usbserial              36882  2 option,usb_wwan
videobuf2_memops       13213  1 videobuf2_vmalloc
soundcore              14636  1 snd
cfg80211              181041  1 wl
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lib80211               14041  2 lib80211_crypt_tkip,wl
i2c_algo_bit           13317  1 i915
lpc_ich                16993  0 
binfmt_misc            17293  1 
video                  19117  1 i915
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
usb_storage            39720  0 
ahci                   25621  2 
libahci                26166  1 ahci
r8169                  56853  0 
ondinequinn@OndinesComputer:~$

---

### Post by cortman on 2013-05-19
[Here's]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") a very informative wiki page outlining how to install drivers for this wireless card. As you can see there are a number of options. I would try the b43 option first.

---

