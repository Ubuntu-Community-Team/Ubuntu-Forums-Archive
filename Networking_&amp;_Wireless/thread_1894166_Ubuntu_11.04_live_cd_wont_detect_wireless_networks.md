---
title: "Ubuntu 11.04 live cd wont detect wireless networks?"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by animefreak873 on 2011-12-11
Hello i have a HP pavilion dv6 
specs:
8GB of ram
64bit
quad core
640gb hardrive

any way i burned a live cd and booted it up and tried ubuntu.Before i set my partition or install ubuntu i check if the wifi works on the live cd so when i install it can be sure wifi works.Any way i click thw wifi icon and all it says is set vpn and enable networking (networking is already checked).I have no idea what to do.Thanks! 

BTW im sure i have a 64 bit live cd.

---

### Post by praseodym on 2011-12-12
Hi,

please show the outputs of:
```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
sudo iwlist scan
lsmod
```

---

### Post by animefreak873 on 2011-12-12
> **praseodym said:**
> Hi,

please show the outputs of:
```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
sudo iwlist scan
lsmod
```

ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:1805]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
    Subsystem: Hewlett-Packard Company Device [103c:1636]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ubuntu@ubuntu:~$ rfkill list
ubuntu@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
usb_storage            53538  1 
uas                    17996  0 
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
binfmt_misc            17565  1 
snd_hda_codec_idt      71137  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17606  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
snd_timer              29602  2 snd_pcm,snd_seq
rts_pstor             440614  0 
videodev               82052  1 uvcvideo
hp_wmi                 13706  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17078  1 videodev
hp_accel               21880  0 
psmouse                73535  0 
lis3lv02d              19893  1 hp_accel
i2c_piix4              13303  0 
input_polldev          14007  1 lis3lv02d
snd                    67382  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                13119  0 
soundcore              12680  1 snd
sparse_keymap          13898  1 hp_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
xhci_hcd               77643  0 
serio_raw              13166  0 
squashfs               36692  1 
aufs                  181143  4284 
nls_utf8               12557  1 
isofs                  40283  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
ahci                   25951  1 
r8169                  48022  0 
libahci                26642  1 ahci
pata_atiixp            13165  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
video                  19438  0 
dm_raid45              77827  0 
xor                    12890  1 dm_raid45
btrfs                 550402  0 
zlib_deflate           27074  1 btrfs
libcrc32c

---

### Post by praseodym on 2011-12-13
The driver needs to be installed by hand:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/3473742/Ralink_5390sta-2.5.0.3_dkms.tar.gz
sudo tar xvf Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3 
```
Check after a reboot:

```
uname -a
iwconfig
lsmod
rfkill list
sudo iwlist scan
```

---

