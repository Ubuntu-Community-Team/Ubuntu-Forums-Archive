---
title: "dell inspiron 3520 wireless problem"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by Sgnob on 2012-11-25
](*,)](*,)](*,)Hi guys, I got a new laptop and installed Ubuntu 12.10 64bit.. every thing seemed to install smoothly but my wireless driver.. This is what I have going on. Thanks in advance 
Sgnob


sgnob@sgnob-Inspiron-3520:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux sgnob-Inspiron-3520 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
sgnob@sgnob-Inspiron-3520:~$ lspci -nnk | grep -iA2 net
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0555]
    Kernel driver in use: r8169
sgnob@sgnob-Inspiron-3520:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 004: ID 064e:8129 Suyin Corp. 
sgnob@sgnob-Inspiron-3520:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

sgnob@sgnob-Inspiron-3520:~$ rfkill list all
sgnob@sgnob-Inspiron-3520:~$ lsmod
Module                  Size  Used by
rfcomm                 46619  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_cirrus    23806  1 
joydev                 17457  0 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
cryptd                 20403  1 ghash_clmulni_intel
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            17369  0 
dcdbas                 14438  1 dell_laptop
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
microcode              22803  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19070  1 dell_wmi
psmouse                95552  0 
serio_raw              13215  0 
mac_hid                13205  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
i915                  520629  3 
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
mei                    40690  0 
videobuf2_memops       13368  1 videobuf2_vmalloc
drm_kms_helper         46784  1 i915
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lpc_ich                17061  0 
drm                   275528  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
video                  19335  1 i915
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
ses                    17363  0 
enclosure              15165  1 ses
uas                    17844  0 
usb_storage            48838  0 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
r8169                  61650  0 


Please let me know if I forgot anything..

---

### Post by chili555 on 2012-11-25
Here you go!  [http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923](http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923)

Notice your device is exactly the same: 14e4:4365 and you already run 64-bit. You should be all set.

---

### Post by Sgnob on 2012-11-25
Thank you very much! WIfi is up and running. 

Sgnob

---

### Post by chili555 on 2012-11-25
Very glad it's working. Please use thread tools at the top to mark Solved.

---

