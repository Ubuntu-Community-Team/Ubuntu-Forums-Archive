---
title: "Ethernet not connecting on startup"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by qbektrix on 2012-03-12
I am using ubuntu 10.04 as live USB. For some reason, when I start the OS, the ethernet is not connecting. The ethernet light is also not blinking. The only solution is that I have manually replug the cable a couple of times. Then it detects. I tried on knoppix, but this issue was not happening there.

Any solution to my problem?

---

### Post by praseodym on 2012-03-12
What hardware is that? Please show

> lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces

---

### Post by Iowan on 2012-03-12
Network Manager is set to "Connect Automatically"?

---

### Post by qbektrix on 2012-03-14
thank you for the responds. I also want to add that, When i login, i see a wifi icon instead if a ethernet icon. Could that be the issue?

> **Iowan said:**
> Network Manager is set to "Connect Automatically"?
My network manager is 0.8. I could not find the option for connect automatically. Pls guide me how to do it.

> **praseodym said:**
> What hardware is that? Please show
I ran the commands after connecting to the network. Do i need to run it before it gets connected also?
[INDENT]ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Kernel driver in use: r8169
	Kernel modules: r8169
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_crypt               11331  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
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
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
xhci                   37160  0 
serio_raw               3978  0 
squashfs               20744  1 
aufs                  149050  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
nouveau               467048  0 
ohci1394               26950  0 
ttm                    49847  1 nouveau
usbhid                 36110  0 
r8169                  34140  0 
hid                    67288  1 usbhid
ieee1394               81181  1 ohci1394
mii                     4381  1 r8169
ahci                   32680  0 
drm_kms_helper         29329  1 nouveau
pata_jmicron            1843  0 
usb_storage            40033  1 
drm                   163747  3 nouveau,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
ubuntu@ubuntu:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback[/INDENT]

---

### Post by praseodym on 2012-03-14
Change the driver according to this posting:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

Choose "r8168 mittels dkms"

---

