---
title: "Can't find ATI driver"
date: 2012-03-24
forum: Multimedia Software
---

### Post by generic41209 on 2012-03-24
Hi, I am unable to find a driver for my graphics card. When I look in the [AMD website]("http://support.amd.com/us/gpudownload/Pages/index.aspx") only Windows drivers show up. I am using Ubuntu 10.04 Lucid, 2.6.32-40-generic.

I have tried installing all drivers listed in the Ubuntu Software Center (main, universe, restricted, multiverse) when I search for "AMD ATI"; both proprietary and free.

When I open "Hardware Drivers" there is no driver listed.

I am unable to set visual effects (of course) - which is the main thing I am after here, I want to play with Docky.

```
g@d:~$ lspci -vnn | grep VGA
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9640]
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
g@d:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
kvm_amd                37070  0 
kvm                   287055  1 kvm_amd
snd_hda_codec_via      33207  1 
snd_hda_intel          25805  1 
snd_hda_codec          85791  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_virtuoso           13452  2 
snd_oxygen_lib         34694  1 snd_virtuoso
snd_mpu401_uart         6857  1 snd_oxygen_lib
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_oxygen_lib
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gspca_spca561          10031  0 
gspca_main             25031  1 gspca_spca561
videodev               40614  1 gspca_main
snd                    71283  20 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_virtuoso,snd_oxygen_lib,snd_mpu401_uart,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
v4l1_compat            15495  1 videodev
i2c_piix4               9639  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vga16fb                12757  1 
r8192ce_pci           487374  0 
v4l2_compat_ioctl32    11892  1 videodev
vgastate                9857  1 vga16fb
joydev                 11104  0 
shpchp                 33679  0 
serio_raw               4918  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
usb_storage            50633  1 
atl1e                  70358  0 
pata_atiixp             4209  0 
ahci                   38350  2 
```

---

### Post by generic41209 on 2012-03-25
Bump

---

### Post by Yellow Pasque on 2012-03-25
To better identify the card, run:
```
sudo update-pciids
lspci | grep VGA
```

---

### Post by generic41209 on 2012-03-25
Thanks, that gave more info, Still cannot find drivers though.

```
g@d:~$ sudo update-pciids
[sudo] password for g: 
Downloaded daily snapshot dated     2012-02-27 03:15:01
g@d:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6550D]
```

---

### Post by Yellow Pasque on 2012-03-25
See: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

---

### Post by generic41209 on 2012-03-26
tyty, just what I needed.

---

