---
title: "how to connect the wireless network in ubuntu 10.04?"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by ashishs9210a on 2011-09-13
Please tell me how i can connect to ubuntu 10.04 to wireless network(wi-fi).with step by step

---

### Post by praseodym on 2011-09-13
Hi.

[LIST=1]
[*]Richt-klick on the network-manager-applet top right in your panel) and choose "Edit connection"

[*]Choose Wireless

[*]Type in the ESSID of your network you want to connect to and add the wireless key (password)

[*]Choose in "Security" the appropriate encryption mode of your network (most: WPA & WPA2 Personal)
[/LIST]

If it doesnt work, open a terminal (Applications-Accessories) and type in (or copy/paste) the following commands one by one:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
```
and post the outputs here in

---

### Post by ashishs9210a on 2011-09-20
ashish@ashish-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
ashish@ashish-laptop:~$ lsusb
Bus 002 Device 003: ID 04f2:b1aa Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:21b4 Broadcom Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ashish@ashish-laptop:~$ lsmod
Module                  Size  Used by
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
binfmt_misc             6587  1 
bnep                    9436  2 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_intelhdmi    11622  1 
btusb                  10957  2 
snd_hda_codec_realtek   203408  0 
i915                  287458  3 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_intel          22005  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29329  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57310  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54180  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
drm                   162409  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32200  2 
r8169                  34108  0 
mii                     4381  1 r8169
ashish@ashish-laptop:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ashish@ashish-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

please tell me how i can connect to ubuntu 10.4and i am install the wifi rader driver but still it not connect to the wifi net.there is another problem
Broadcom STA Wireless Driver not installed in my laptop.
how i can instal it and acess the internet through wifi.

---

### Post by praseodym on 2011-09-20
With cable connection: Go to System->Settings->Hardware drivers and install the Broadcom-STA.

Without cable connection: Insert the installation CD/DVD, add it to your software sources and install the packages

[LIST]
[*]dkms

[*]patch

[*]fakeroot

[*]bcmwl-kernel-source
[/LIST]
Close the package manager and type:

```
sudo depmod -a
```
After that you should be able to activate the driver, too.

---

