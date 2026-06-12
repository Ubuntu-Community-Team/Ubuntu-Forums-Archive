---
title: "Realtek RTL8187B unstable + &quot;bad password&quot; problem wicd"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by TraBruno on 2011-04-12
Hello all,

I'm stuck with a problem that made me abandon ubuntu years ago with the jaunty jackalope release. I had hoped the problem would have been fixed and went ahead and installed 10.10, but apparently it's still around to bug me (and others). There are already a few threads on the same or similar problems, but since none of the appeared solutions or suggestions have worked for me I start a new one.

Machine type is medion MD96290 laptop 
Wifi:Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

I usually have a good connection with the internet when I start a session on ubuntu (though not always), but after a while it always starts to fail, and I can't manage to get it working again after that. The driver loaded is RTL8187 and not RTL8187B.

Some of the things I tried, as suggested in other posts:

- Adding a constant bit rate to /etc/rc.local
iwconfig wlan0 rate 5.5M

- disable the power saving function on the device 
sudo iwconfig wlan0 power off
this gave me an error:
```
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
```

- tried to install a specific driver that someone obtained from Realtek ([http://ubuntuforums.org/showthread.php?t=1101296](http://ubuntuforums.org/showthread.php?t=1101296))
This gave me some errors I can't interpret (since I'm new to linux (well, trying to be at least!)):
make
```

make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_softmac.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/dot11d.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_rx.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_tx.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_wx.o
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.o
/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2

```

make install
```

kernel/drivers/net/wireless/rtl818x/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/drivers/leds/led-class.ko kernel/net/wireless/cfg80211.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko
make[1]: Entering directory `/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211'
make -C /lib/modules/2.6.35-28-generic/build M=/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.o
/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[3]: *** [/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211/ieee80211_module.o] Error 1
make[2]: *** [_module_/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/bruno/rtl8187B_linux_26.1052.0225.2009.release/ieee80211'
make: *** [install] Error 2

```

- Unloading the RLT8187 module with sudo rmmod rtl8187, sudo modprobe rtl8187. This had no effect whatsoever

- uninstalling network manager and replacing by wicd. 
This is the last thinf I tried and it gave me a whole different world of buggy behaviour. I could access the internet immediately after I installed wicd, but after a while (just as before) it disconnected, only now it gave me a reason: "bad password". That's rubbish of course because it could connect before and I didn't change the password. Next session same thing. It works for a while, the it decides that the password is wrong and throws me off.

This last issue has a whole history of its own that has nothing to do with the RTL8187B driver so I don't know where to look anymore.

Here are some outputs, please tell me if there is information missing!

lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 064e:a100 Suyin Corp. Acer OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0a:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"FRITZ!Box Fon WLAN 7112"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

lsmod
```

Module                  Size  Used by
rtl8187                51470  0 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_si3054     3440  1 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
arc4                    1165  2 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
i915                  295435  4 
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168060  4 i915,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
intel_agp              26566  2 i915
snd                    49038  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                    9536  0 
joydev                  8767  0 
agpgart                32011  2 drm,intel_agp
mac80211              231959  1 rtl8187
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
sm_common               3285  1 r852
videodev               43098  1 uvcvideo
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
i2c_algo_bit            5168  1 i915
mtd                    18877  2 sm_common,nand
lp                      7342  0 
cfg80211              144694  2 rtl8187,mac80211
video                  18712  1 i915
output                  1883  1 video
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
eeprom_93cx6            1345  1 rtl8187
serio_raw               4022  0 
parport                31492  3 parport_pc,ppdev,lp
acer_wmi               13929  0 
sdhci_pci               6601  0 
ahci                   19198  5 
sdhci                  15922  1 sdhci_pci
firewire_ohci          21234  0 
led_class               2633  3 rtl8187,acer_wmi,sdhci
r8169                  36521  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
libahci                21728  1 ahci
mii                     4425  1 r8169

```

I really hope someone can make sense out of any of this and get me on the way. I would love to get on board of this thing, but without a reliable wifi connecting I can't work!

Cheers, BP

---

### Post by josephmills on 2011-04-12
what repo's do you have checked in software sources and when was the last time you updated && upgraded?

---

### Post by TraBruno on 2011-04-12
I just made a fresh install not a week ago, so I should have all the latest no? I have all sources checked except 'source code'.

---

### Post by josephmills on 2011-04-12
I am also new to ubuntu too but I update and upgrade every time I add a new driver or program or a repo. I would say take off wicd if its giving you troubles then put network manager back on and update and upgrade

---

