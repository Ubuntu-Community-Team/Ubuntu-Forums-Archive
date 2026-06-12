---
title: "Asus Intel Centrino Wireless-N + WiMax 6150, Not connecting."
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by Lolnutz on 2011-11-23
Hi there, Im new to these forums and ubuntu. Decided to dual boot on my laptop for fun.

I have seen a bundle of tutorials helping fix wireless problems for multiple scenarios even for the same card, but the guy always has an acer.......or a Ienovo....Never an Asus... So I need some specialized help I guess getting my wireless working as well.

% iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```% rfkill list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no

```% dmesg | grep iwl
```
[   13.945329] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.945332] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   13.945389] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.945399] iwlagn 0000:02:00.0: setting latency timer to 64
[   13.945460] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   13.956072] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[   13.956076] iwlagn 0000:02:00.0: Device SKU: 0X9
[   13.956078] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   13.961236] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.961331] iwlagn 0000:02:00.0: irq 50 for MSI/MSI-X
[   14.130089] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   14.132830] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.961104] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   33.968834] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   47.978982] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   56.322766] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   64.646567] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   78.656707] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   88.774721] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   97.074466] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  105.338354] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  113.646132] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  121.925939] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  130.241724] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  138.537546] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  146.885300] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  155.596671] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  163.940418] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  177.874664] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  191.836894] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  200.120681] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  208.444441] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  225.663427] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  233.931272] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  242.263030] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  250.538847] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  258.902585] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  267.226372] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  281.184573] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  289.448413] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  297.756200] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  306.035994] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  314.307850] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  322.579680] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  330.879449] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  339.191224] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
```% lsmod | grep asus
```
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
wmi                    19256  1 asus_wmi

```% lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
03:00.0 USB Controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
```And pulling from a tutorial on an acer, directed to from a thread that pertained to the same wireless card I got...

% sudo rmmod -f asus-wmi
```
ERROR: Removing 'asus_wmi': Resource temporarily unavailable

```Something is failing to flush something. I hope this helps produce a fix for me :) Ill be on tomorrow as it is late here now and I would like some rest :| 

PS ubuntu is pretty cool, itll be great if my wireless is finally working(might replace windows 7 idk...)

---

### Post by Lolnutz on 2011-11-26
Le Bump

---

### Post by TZed on 2011-12-02
Free bump. I have the same problem, although I don't have nearly as much output from those commands as you. I'll post it next time my computer's up. I also have an Asus with no wireless.

---

### Post by bkratz on 2011-12-02
Not good news, but here is a description of what is happening.

[http://ubuntuforums.org/showpost.php?p=11505434&postcount=2](http://ubuntuforums.org/showpost.php?p=11505434&postcount=2)

---

### Post by TZed on 2011-12-04
Sorry to hijack your thread, but that solution didn't apply for me. I'm already using Ubuntu 10.04, 2.6.x kernel. Laptop is an Asus with Intel 6150 wireless.

% iwconfig
```

lo        no wireless extensions.

```% rfkill list all
```


``` (nothing)

% dmesg | grep iwl
```


``` (also nothing)

% lsmod
```

 Module                  Size  Used by
  binfmt_misc             6587  1 
  ppdev                   5259  0 
  snd_hda_codec_realtek   203376  1 
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
  snd_timer              19098  2 snd_pcm,snd_seq
  snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
  uvcvideo               57374  0 
  videodev               34361  1 uvcvideo
  v4l1_compat            13251  2 uvcvideo,videodev
  fbcon                  35102  71 
  tileblit                1999  1 fbcon
  font                    7557  1 fbcon
  bitblit                 4707  1 fbcon
  softcursor              1189  1 bitblit
  snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  xhci                   36936  0 
  psmouse                63677  0 
  serio_raw               3978  0 
  video                  17375  0 
  output                  1871  1 video
  soundcore               6620  1 snd
  snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
  vga16fb                11385  1 
  vgastate                8961  1 vga16fb
  lp                      7028  0 
  parport                32635  2 ppdev,lp
  ahci                   32360  1 
     
```% lspci -nn
```

 00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
  00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0126] (rev 09)
  00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
  00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
  00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
  00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
  00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
  00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
  00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
  00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
  00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c49] (rev 05)
  00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
  00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
  **02:00.0 Network controller [0280]: Intel Corporation Device [8086:0885] (rev 67)**
  03:00.0 USB Controller [0c03]: Device [1b73:1000] (rev 04)
 ** 04:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)**
    
```

---

### Post by paulbdavis on 2011-12-07
There us a fix here, involving a new kernel install. 

This is what I have been working with, but it only works for me if I install this kernel from the .deb files shown in the post. When I compiled my own 2.6.38 kernel (on openSUSE) it did not recognize the wireless at all.

EDIT: Forgot to add the link. [http://ubuntuforums.org/showpost.php?p=11362436&postcount=42]("http://ubuntuforums.org/showpost.php?p=11362436&postcount=42")

---

