---
title: "Hello Ubuntu World I Have Internet Connection Problems"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by pedroloco on 2013-05-15
im new to this ubuntu world i have converted a my laptop to 13.04  32bit and i cannot connect at all.  i currently have it wired to the router with still no connectivity was hoping to have it connected wirelessly.   it installed on a dell inspiron 6400 core 2 duo  Should i have installed the 64 bit ?  :confused::confused::confused::confused:

---

### Post by matt_symes on 2013-05-15
Thread moved to **Networking and Wireless** subforum.

---

### Post by praseodym on 2013-05-15
Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
rfkill list
```

---

### Post by pedroloco on 2013-05-17
ethernet controller [0200]; Broadcom Corporation bcm4401-bo 100 base -tx [14e4:170c] (rev 02)
subsystem;Del Inspirion 6400 [1028:01af]
firewire (ieee 1394) [0c00]; Ricoh Co ltd R5c832 Ieee 1394 Controller [1180:0832]subsystem: Dell Device [1028:01bd]
kernel driver in use: radeon
network controller [0280] Broadcom Corporation BCM4311 802.11b/g wlan [14e4:4311] (rev 01)
subsystem: Dell Wireless 1390 Wlan Mini Card [1028:0007] 
[COLOR=#000000][FONT=Noteworthy-Light]kernel driver in use : wl[/FONT][/COLOR]

[COLOR=#000000][FONT=Noteworthy-Light]Bus 001 Device 001 Id 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Bus 002 Device 001 Id 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Bus 003 Device 001 Id 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Bus 004 Device 001 Id 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Bus 005 Device 001 Id 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]


[COLOR=#000000][FONT=Noteworthy-Light]parport_pc 27504 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]ppdev     12817     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]bnep     17669    2[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]rfcomm      37420     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]bluetooth      202069    10 bnep, rfcom[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]ssb       69217     1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]wl    3027822     1[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_hda_codec_idt     63896      1[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]and_hda_intel        38307 3[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]coretemp       13131 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_hda_codec            117580 2       snd_hda_codec_idt, and_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]radeon     870822     3[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_hwdep         13272      snd_hda_codec[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]r852       17873     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Snd_pcm          80890       2     snd_hda_codec, snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]kvm[/FONT][/COLOR][COLOR=#000000][FONT=Noteworthy-Light]  [/FONT][/COLOR][COLOR=#000000][FONT=Noteworthy-Light]  376505    0[/FONT][/COLOR][COLOR=#000000][FONT=Noteworthy-Light]r852    17873    0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]radeon      870822     3[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_hwdep      13272    1   snd_hda_codec[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]sm_common   16772   1   r852[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_pcm     80890     2    snd_hda_codec,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]nand         49670     2      r852,sm_common[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_page_alloc      14230    2   snd_pcm,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]nand_ecc           13105  1     nand[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]gpio_ich       13236      0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_seq_midi       13132    0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]nand_bch         13003   1        nand[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lib80211         14040      1       wl[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_seq_midi_evnet    14475    1   snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_rawmidi      25114     1    Snd_SEQ_MIDI[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]bch         17226    1   nand_bch[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]r592           17707     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]psmouse          81038     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]cfg80211         436177    1   wl[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_seq         51280     2   snd_seq_midi_event,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]nand_ids         8547    1       nand[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]microcode         18286       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]dell_wmi         12601       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]mtd           38922        2        nand,sm_common[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_seq_device     14137     3   snd_seq,snd_rawmidi,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]dell_laptop      17161     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_timer         244411       2   snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]memstick       15842      1   r592[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lpc_ich       16925      0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]serio_raw          13031     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]sparse_keymap          13658    1   dell_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]ttm       71289     1  radeon[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]dcdbas       14021      1    dell_laptop[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]mac_hid      13037      0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]drm_kms_helper       47545     1       radeon[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]drm       228750    5     ttm,drm_kms_helper,radeon[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd       56485    15  snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]i2c_algo_bit      13197    1       radeon[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]soundcore     126000      1       snd[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]wmi       18590    1    dell_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]video             188894        0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lp         13299    0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]parport       40753         3    lp,ppdev,parport_pc[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]firewire_ochi        35292     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]firewire_core           61718    1  firewire_ochi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]sdhci_pci           18158       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]sdchi      31824      1      sdhci_pci[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]crc_itu_t          12627       1   firewire_core[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lo     no wireless extentions[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lo      lin encap: local loopback[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        inet addr:127.0.0.1     Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        inet6 addr: ::1/128  Scope: Host[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        Up Loopback Running Mtu:65536    Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        Rx packets:6320  errors:0 dropped: 0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        tx packets:6320  errors:0 dropped: 0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        collision:0 txqueuelen:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        Rx bytes : 508608  (508.6 kb) Tx bytes : 508608  (508.6 kb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]# interfaces(5) file used by ifup(8)  and if down(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]auto lo[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]iface lo inet loopback[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]#Dynamic resolv.conf(5) file for glib resolver (3) generated by resolvconf(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light] [/FONT][/COLOR]

---

### Post by pedroloco on 2013-05-17
ethernet controller [0200]; Broadcom Corporation bcm4401-bo 100 base -tx [14e4:170c] (rev 02)
subsystem;Del Inspirion 6400 [1028:01af]
firewire (ieee 1394) [0c00]; Ricoh Co ltd R5c832 Ieee 1394 Controller [1180:0832]subsystem: Dell Device [1028:01bd]
kernel driver in use: radeon
network controller [0280] Broadcom Corporation BCM4311 802.11b/g wlan [14e4:4311] (rev 01)
subsystem: Dell Wireless 1390 Wlan Mini Card [1028:0007] 
[COLOR=#000000][FONT=Noteworthy-Light]kernel driver in use : wl[/FONT][/COLOR]

[COLOR=#000000][FONT=Noteworthy-Light]Bus 001 Device 001 Id 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Bus 002 Device 001 Id 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Bus 003 Device 001 Id 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Bus 004 Device 001 Id 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Bus 005 Device 001 Id 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]


[COLOR=#000000][FONT=Noteworthy-Light]parport_pc 27504 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]ppdev     12817     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]bnep     17669    2[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]rfcomm      37420     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]bluetooth      202069    10 bnep, rfcom[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]ssb       69217     1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]wl    3027822     1[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_hda_codec_idt     63896      1[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]and_hda_intel        38307 3[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]coretemp       13131 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_hda_codec            117580 2       snd_hda_codec_idt, and_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]radeon     870822     3[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_hwdep         13272      snd_hda_codec[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]r852       17873     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]Snd_pcm          80890       2     snd_hda_codec, snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]kvm[/FONT][/COLOR][COLOR=#000000][FONT=Noteworthy-Light]  [/FONT][/COLOR][COLOR=#000000][FONT=Noteworthy-Light]  376505    0[/FONT][/COLOR][COLOR=#000000][FONT=Noteworthy-Light]r852    17873    0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]radeon      870822     3[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_hwdep      13272    1   snd_hda_codec[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]sm_common   16772   1   r852[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_pcm     80890     2    snd_hda_codec,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]nand         49670     2      r852,sm_common[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_page_alloc      14230    2   snd_pcm,snd_hda_intel[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]nand_ecc           13105  1     nand[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]gpio_ich       13236      0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_seq_midi       13132    0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]nand_bch         13003   1        nand[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lib80211         14040      1       wl[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_seq_midi_evnet    14475    1   snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_rawmidi      25114     1    Snd_SEQ_MIDI[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]bch         17226    1   nand_bch[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]r592           17707     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]psmouse          81038     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]cfg80211         436177    1   wl[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_seq         51280     2   snd_seq_midi_event,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]nand_ids         8547    1       nand[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]microcode         18286       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]dell_wmi         12601       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]mtd           38922        2        nand,sm_common[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_seq_device     14137     3   snd_seq,snd_rawmidi,snd_seq_midi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]dell_laptop      17161     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd_timer         244411       2   snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]memstick       15842      1   r592[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lpc_ich       16925      0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]serio_raw          13031     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]sparse_keymap          13658    1   dell_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]ttm       71289     1  radeon[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]dcdbas       14021      1    dell_laptop[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]mac_hid      13037      0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]drm_kms_helper       47545     1       radeon[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]drm       228750    5     ttm,drm_kms_helper,radeon[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]snd       56485    15  snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]i2c_algo_bit      13197    1       radeon[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]soundcore     126000      1       snd[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]wmi       18590    1    dell_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]video             188894        0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lp         13299    0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]parport       40753         3    lp,ppdev,parport_pc[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]firewire_ochi        35292     0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]firewire_core           61718    1  firewire_ochi[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]sdhci_pci           18158       0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]sdchi      31824      1      sdhci_pci[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]crc_itu_t          12627       1   firewire_core[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lo     no wireless extentions[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]lo      lin encap: local loopback[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        inet addr:127.0.0.1     Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        inet6 addr: ::1/128  Scope: Host[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        Up Loopback Running Mtu:65536    Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        Rx packets:6320  errors:0 dropped: 0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        tx packets:6320  errors:0 dropped: 0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        collision:0 txqueuelen:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]        Rx bytes : 508608  (508.6 kb) Tx bytes : 508608  (508.6 kb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]# interfaces(5) file used by ifup(8)  and if down(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]auto lo[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]iface lo inet loopback[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]#Dynamic resolv.conf(5) file for glib resolver (3) generated by resolvconf(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Noteworthy-Light] [/FONT][/COLOR]


sorry for the delay  working 12 hr shifts

---

### Post by praseodym on 2013-05-17
Please deactivate the Broadcom-STA driver in "additional drivers" of the update-manager. Download the firmware file for the native driver and save it in "Downloads"

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
```
Maybe you need to clean up the old config:
```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Reboot.

---

### Post by pedroloco on 2013-05-17
i cant get on the net at all   do i jus dl it on another comp and install via usb or sumthin

---

### Post by praseodym on 2013-05-17
Yes, download it via the link above.

---

### Post by pedroloco on 2013-05-17
IT WORKED !!!!!:p   now how do i make it go wireless

---

### Post by praseodym on 2013-05-17
Klick on the network-manager applet in the panel->Edit connections->Wireless

Add the ESSID of your network and choose the encryption mode in use (mostly WPA&WPA2 Personal")

---

### Post by pedroloco on 2013-05-17
ok i entered all the information   on the connection tab it says wifi is diabled by hardware switch

---

### Post by pedroloco on 2013-05-17
ok i entered the information and in the connections tab at the top  it says wifi is disabled by the hardware switch

---

### Post by pedroloco on 2013-05-17
i got it    i appreciate  your help

---

### Post by praseodym on 2013-05-17
You're welcome.

---

