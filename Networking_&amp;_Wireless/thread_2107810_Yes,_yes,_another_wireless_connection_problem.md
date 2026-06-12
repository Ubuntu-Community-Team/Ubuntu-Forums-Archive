---
title: "Yes, yes, another wireless connection problem"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by Tinsnip on 2013-01-22
I'm an absolute noob to Linux.  Long time admirer, first time user.  I just bought a new laptop for school that had Windows 8, which I quickly learned to hate, so I downloaded Ubuntu 12.10 yesterday.  My problem is that Ubuntu doesn't seem to recognize any wireless devices (I live in an apartment building, so it should be detecting several networks).  I know that many other people have had this problem, but it seems to require a case by case solution.  I tried downloading the broadcom STA driver and activate it in "additional drivers," but there's nothing there, I'm not sure if it even downloaded properly.  The internet works fine when I'm wired in, though.  Anyway, my hardware info. is listed below.  If anyone can help walk me through this I would be extremely grateful, as the reason I bought a laptop is to be mobile :).

Oh yeah, the router I'm using is a Linksys E1500 by Cisco


kevin@kevin-HP-Pavilion-g7-Notebook-PC:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
01:00.1 Bluetooth [0d11]: Ralink corp. Device [1814:3298]
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1845]
    Kernel driver in use: r8169
kevin@kevin-HP-Pavilion-g7-Notebook-PC:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 05c8:0348 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
kevin@kevin-HP-Pavilion-g7-Notebook-PC:~$ lsmod
Module                  Size  Used by
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_idt      70210  1 
nls_iso8859_1          12714  1 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
joydev                 17458  0 
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  520621  3 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
hp_accel               25977  0 
soundcore              15048  1 snd
lis3lv02d              19830  1 hp_accel
coretemp               13401  0 
input_polldev          13897  1 lis3lv02d
mei                    40691  0 
i2c_algo_bit           13414  1 i915
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lpc_ich                17062  0 
mac_hid                13206  0 
video                  19336  1 i915
kvm                   414071  0 
wmi                    19071  1 hp_wmi
ghash_clmulni_intel    13221  0 
cryptd                 20404  1 ghash_clmulni_intel
microcode              22804  0 
psmouse                95595  0 
serio_raw              13216  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
r8169                  61651  0 
kevin@kevin-HP-Pavilion-g7-Notebook-PC:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

kevin@kevin-HP-Pavilion-g7-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
kevin@kevin-HP-Pavilion-g7-Notebook-PC:~$ sudo iwlist scan
[sudo] password for kevin: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

---

### Post by ahallubuntu on 2013-01-22
This might get the WiFi working:

[http://ubuntuforums.org/showthread.php?p=12451451](http://ubuntuforums.org/showthread.php?p=12451451)

FYI, although I hope you are able to get all the hardware working on this laptop, it's usually best with Linux to choose hardware ahead of time that is most likely to have good Linux support.  Some hardware is poorly supported in Linux, some is much better supported.

---

### Post by Tinsnip on 2013-01-22
Thanks for the link, it looks like a couple other people have had success with that process.  I suppose I chose the wrong header or image, because now Ubuntu won't even boot up.  All I get is one giant terminal.  A black screen with white text that asks me to log onto my HP Computer, then says "Welcome to Ubuntu" and then I'm locked into that screen, only able to type terminal commands.  I can't help but laugh, so much trouble due to my ignorance - lucky I have a backup computer.  I suppose I'll re-boot from the CD and re-install Ubuntu, then I'll go after it again.

---

