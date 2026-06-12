---
title: "Wlan is not prober working not working"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by sickwick on 2011-10-16
Hello 
I had this problem already after upgrading from 10.10 to 11.04 and solved it with this workaround:
[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397/comments/6](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397/comments/6)

I intended to to the same after the upgrade to 11.10 but when I am trying to activate the old driver in Jockey it tels me [I]Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log

Is there any way to install this driver 
[/I]

---

### Post by wildmanne39 on 2011-10-16
Hi, welcome to the forum! please post the results of:
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
Thank

---

### Post by sickwick on 2011-10-17
lspci -nnk | grep -iA2 net:

10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: tg3
--
30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN [103c:1371]
    Kernel driver in use: wl

lsmod:

Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_analog    75090  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
lib80211_crypt_tkip    17240  0 
wl                   2646601  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
hp_wmi                 13652  0 
pcmcia                 39822  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
radeon                925020  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13658  1 hp_wmi
sp5100_tco             13495  0 
ttm                    65224  1 radeon
yenta_socket           27428  0 
snd                    55902  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 radeon
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   192226  5 radeon,ttm,drm_kms_helper
serio_raw              12990  0 
i2c_piix4              13093  0 
i2c_algo_bit           13199  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
k8temp                 12905  0 
video                  18908  0 
wmi                    18744  1 hp_wmi
lib80211               14570  2 lib80211_crypt_tkip,wl
ati_agp                13242  0 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
pata_atiixp            12967  0 
ahci                   21634  4 
libahci                25727  1 ahci
tg3                   132972  0

---

### Post by wildmanne39 on 2011-10-17
Hi, this should get your wireless working.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Then disconnect your wired connection and restart your computer.
Thank you

---

### Post by sickwick on 2011-10-18
Thanks my wlan works now, great help.

THANK YOU

---

### Post by wildmanne39 on 2011-10-18
Hi sickwick, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

