---
title: "Video artifacts and Likewise issues"
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Calash on 2010-10-08
Updated my work computer the other day and ran into some various issues.  After some work I was able to get it booting and connected into our network by downloading Likewise-open 6 again.  However it is giving me two add issues.


- Randomly menus will hang while trying to open.  If I move to fast they will leave artifacts on the screen that will not go away.  These will range from box outlines of the menus to text.  They are top layer in the windows and stay for a long time.  I tried searching on it but for the life of me I can not figure out what to even search for.


- I am using Likewise-open6 for my Active directory.  Everything works great except when I open a terminal and login with that account I have the basic shell loaded.  I have to type /bin/bash to get my standard shell.  From that point it works fine.



Edit: For item 1 it shows up in a screen shot.  I have attached it.  The odd image to the top right and the text in the middle left are what I am seeing right now over everything on the screen.

lspci

```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]



```


lsmod
```

Module                  Size  Used by
usb_storage            50372  0 
isofs                  34218  0 
udf                    86514  0 
crc_itu_t               1739  1 udf
binfmt_misc             7984  1 
vboxnetadp              5267  0 
vboxnetflt             14966  1 
vboxdrv              1792824  4 vboxnetadp,vboxnetflt
xt_limit                2204  8 
xt_tcpudp               2627  15 
ipt_LOG                 5394  8 
ipt_MASQUERADE          1919  0 
xt_DSCP                 2269  0 
ipt_REJECT              2440  1 
nf_conntrack_irc        4501  0 
nf_conntrack_ftp        7158  0 
xt_state                1386  6 
parport_pc             30086  0 
ppdev                   6804  0 
iptable_nat             4593  0 
nf_nat                 20067  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13143  9 iptable_nat,nf_nat
nf_conntrack           75238  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
iptable_mangle          1823  0 
iptable_filter          1778  1 
ip_tables              19107  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               24423  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_analog    80317  1 
snd_hda_intel          26019  3 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_infineon            9441  0 
snd                    64117  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
tpm_tis                 9894  0 
tpm                    16013  2 tpm_infineon,tpm_tis
tpm_bios                6426  1 tpm
lp                     10201  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
fglrx                2523725  168 
intel_agp              32080  0 
hp_wmi                  6435  0 
psmouse                62080  0 
parport                37032  3 parport_pc,ppdev,lp
serio_raw               4910  0 
usbhid                 42062  0 
hid                    84678  1 usbhid
floppy                 65299  0 
e1000e                151787  0 
ahci                   21857  0 
libahci                26167  3 ahci

```

Using the latest provided driver.  Already wiped the config and reloaded the driver.

---

### Post by Calash on 2010-10-09
Is there any other info I can provide to help figure out these issues?

---

