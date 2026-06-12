---
title: "Wireless totally disappeared after 12.04 system update"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by mooroha on 2012-06-04
Hi all 

I have 12.04 on an Asus eee901. I just updated and on restarting all wireless networking has gone and the network icon is missing from the desktop. 

Please help

M

Here's some additional info. 

lspci

[HTML]00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
03:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
[/HTML][HTML]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48432 (48.4 KB)  TX bytes:48432 (48.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:e6:0e:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:15:af:e6:0e:a5  
          inet addr:169.254.8.151  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
[/HTML]lsmod

[HTML]Module                  Size  Used by
btusb                  17912  0 
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55605  1 vfat
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
rt2800pci              18340  0 
psmouse                87213  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48858  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  11 btusb,rfcomm,bnep
eeprom_93cx6           12653  1 rt2800pci
ppdev                  12849  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414637  3 
binfmt_misc            17292  1 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
eeepc_laptop           19464  0 
sparse_keymap          13658  1 eeepc_laptop
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
video                  19068  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
b43                   342643  0 
mac80211              436455  4 rt2800lib,rt2x00pci,rt2x00lib,b43
cfg80211              178679  3 rt2x00lib,b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1e                  32872  0 
usb_storage            39646  2 [/HTML]sudo rfkill list all

[HTML]0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: eeepc-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
6: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no[/HTML]

lspci -nnk | grep -iA2 net

```
01:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
    Subsystem: Ralink corp. Device [1814:2790]
    Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Kernel driver in use: ATL1E

```

Interestingly I entered this command a while ago and the network controller seems to have changed. Here's the previous version from before the update.

```
01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]
    Subsystem: Ralink corp. Device [1814:2790]
    Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Kernel driver in use: ATL1E
```

---

### Post by ozPATT on 2012-06-05
With you on this one, same thing just happened to me. Trying everything but nothing working and I have to manually restart the wired connection on startup as well. Anyone got any ideas? :(

Edit: 

Actually I don't think the problem is anything to do with the drivers or anything like that, but just that the Network Manager isn't starting. 

Try going to the terminal and typing:

```
sudo service network-manager start
```

And see what happens :)

---

### Post by mooroha on 2012-06-05
Thanks Pat

I have to admit I took the cowards way out and went back to an earlier version. I wouldn't say 12.04 has been a massive improvement for me, so it was no loss.

Cheers

M

---

