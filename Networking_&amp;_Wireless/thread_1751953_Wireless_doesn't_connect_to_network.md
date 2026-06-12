---
title: "Wireless doesn't connect to network"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by wkcchampion on 2011-05-07
Hi, I've just upgraded to Ubuntu 11.04 (kernel 2.6.38-8-generic i686) on my Netbook (Asus EEEPC 1000H). It does connect thru cable, but not by the wifi.
The wifi worked perfectly under 10.10 and it does under XP.

I followed the Sticky and here is the results of the commands listed there:
```

marco@marco-eeepc:~$ $ lspci
$: comando non trovato
marco@marco-eeepc:~$ $ lsusb
$: comando non trovato
marco@marco-eeepc:~$  lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
marco@marco-eeepc:~$ $ lsusb
$: comando non trovato
marco@marco-eeepc:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
marco@marco-eeepc:~$ 

```

```

marco@marco-eeepc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:63:8a:8e  
          indirizzo inet:192.168.0.5  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::223:54ff:fe63:8a8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5335 errors:0 dropped:0 overruns:0 carrier:4
          collisioni:0 txqueuelen:1000 
          Byte RX:6144223 (6.1 MB)  Byte TX:866221 (866.2 KB)
          Interrupt:44 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:5520 (5.5 KB)  Byte TX:5520 (5.5 KB)

marco@marco-eeepc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

marco@marco-eeepc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Befyabe"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:B2:FC:C0:28   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0



```

```

marco@marco-eeepc:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
rt2860sta             494649  0 
arc4                   12473  2 
snd_hda_codec_realtek   255820  1 
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  2 rt2860sta,rt2800lib
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
rt2x00pci              13986  1 rt2800pci
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
i915                  450944  2 
snd_hwdep              13274  1 snd_hda_codec
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
drm_kms_helper         40745  1 i915
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm                   180037  3 i915,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 rt2x00lib,mac80211
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
eeepc_laptop           19417  0 
serio_raw              12990  0 
eeprom_93cx6           12653  1 rt2800pci
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
sparse_keymap          13666  1 eeepc_laptop
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
atl1e                  32576  0 


marco@marco-eeepc:~$ sudo lshw -C network
[sudo] password for marco: 
PCI (sysfs)  


```

---

### Post by chili555 on 2011-05-07
Please see here. Same problem, same solution. Please detach the ethernet cable before you attempt to connect with wireless.

[http://ubuntuforums.org/showthread.php?t=1727945&highlight=rt2860sta](http://ubuntuforums.org/showthread.php?t=1727945&highlight=rt2860sta)

---

