---
title: "Ubuntu 9.10 - How to configure the sound"
date: 2010-04-07
forum: Multimedia Software
---

### Post by Alberto Leal on 2010-04-07
Hello All,

I've just installed Ubuntu 9.10 in my computer and as I can see my sound's driver is there. But, I'm hearing nothing. I've tried mp3, video, and so on. It doesn't work!

Do you guys have any clue?

Thanks  a lot!

Following some information:

albertoleal@albertoleal-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

albertoleal@albertoleal-desktop:~$ lsmod
Module                  Size  Used by
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
snd_hda_codec_via      28988  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ppdev                   6688  0 
lp                      8964  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
parport_pc             31940  1 
parport                35340  3 ppdev,lp,parport_pc
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
atl2                   25716  0 
psmouse                56180  0 
serio_raw               5280  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52544  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
floppy                 54916  0 
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

---

### Post by thesource01 on 2010-04-07
Hi

Have you tried Alsamixer

Type alsamixer in terminal and increase the volume up then it should work.

Thanks

---

### Post by lidex on 2010-04-08
Go here for generic sound issues in karmic:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

