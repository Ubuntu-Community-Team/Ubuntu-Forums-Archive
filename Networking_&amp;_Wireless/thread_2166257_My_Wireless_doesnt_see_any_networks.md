---
title: "My Wireless doesnt see any networks"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by BlackfyreTR on 2013-08-08
Hi, I'm a new Ubuntu user, I'm writing it via my ethernet cable.
When &#305; first installed, there wasn't even "Wi-Fi" button.
Then, it came, but now it doesn't see any networks and my router is very far away from my table, so I dont want to be "ball cancer"

---

### Post by praseodym on 2013-08-08
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

### Post by BlackfyreTR on 2013-08-08
Hello,
This is the results.



> blackfyre@Blackfyre:~$ uname -a
Linux Blackfyre 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:19:35 UTC 2013 i686 i686 i686 GNU/Linux
blackfyre@Blackfyre:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0434]
    Kernel driver in use: r8169
blackfyre@Blackfyre:~$ 
blackfyre@Blackfyre:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 002 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
blackfyre@Blackfyre:~$ lsmod
Module                  Size  Used by
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202109  10 bnep,rfcomm
joydev                 17097  0 
snd_hda_codec_hdmi     36185  1 
lib80211_crypt_tkip    17160  0 
wl                   2902185  0 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              436177  1 wl
snd_hda_codec_realtek    63791  1 
coretemp               13131  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
kvm_intel             126842  0 
snd_hda_intel          38307  5 
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
kvm                   376505  1 kvm_intel
dell_wmi               12601  0 
radeon                875105  3 
sparse_keymap          13658  1 dell_wmi
snd_rawmidi            25114  1 snd_seq_midi
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
wmi                    18590  1 dell_wmi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
video                  18894  0 
ttm                    71289  1 radeon
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
dell_laptop            17161  0 
snd                    56485  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         47545  1 radeon
drm                   228489  5 ttm,drm_kms_helper,radeon
dcdbas                 14021  1 dell_laptop
mac_hid                13037  0 
psmouse                81038  0 
microcode              18286  0 
i2c_algo_bit           13197  1 radeon
lpc_ich                16925  0 
soundcore              12600  1 snd
mei                    36197  0 
serio_raw              13031  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
ums_realtek            17669  0 
usb_storage            47684  1 ums_realtek
r8169                  61543  0 
ahci                   25507  2 
libahci                26108  1 ahci
blackfyre@Blackfyre:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
blackfyre@Blackfyre:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
blackfyre@Blackfyre:~$ cat /etc/resolv.cong
cat: /etc/resolv.cong: No such file or directory

---

### Post by Bucky Ball on 2013-08-08
The last command should be:

```
cat /etc/resolv.con**f**
```

Please, the result of this:

```
sudo lshw -C wireless
```

---

### Post by BlackfyreTR on 2013-08-08
Should I use all commands again?


Here is the result of sudo lshw

> blackfyre@Blackfyre:~$ sudo lshw -C wireless[sudo] password for blackfyre: 
PCI (sysfs)  




---

### Post by praseodym on 2013-08-08
No, for this device you only need the missing firmware for your low-power chipset (LP-PHY) and uninstall the STA driver incl. its config:

```
sudo apt-get install firmware-b43-lpphy-installer
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf  
```
Reboot.

---

### Post by BlackfyreTR on 2013-08-08
Thank you, I'll reboot and report the results (Y)

---

### Post by Bucky Ball on 2013-08-08
Sorry, should have been:

```
sudo lshw -C network
```

But doesn't matter as praseodym appears to have things in hand. Must be time for bed.

---

### Post by BlackfyreTR on 2013-08-08
Restarted PC, now it says Wi-Fi disabled by hardware switch?

---

### Post by BlackfyreTR on 2013-08-08
> **Bucky Ball said:**
> Sorry, should have been:

```
sudo lshw -C network
```

But doesn't matter as it looks like praseodym may have things in hand. Must be time for bed.

Hi, typed it, so:

blackfyre@Blackfyre:~$ sudo lshw -C network

[sudo] password for blackfyre: 
PCI (sysfs)

---

### Post by Bucky Ball on 2013-08-08
Doesn't matter. Follow praseodym's advice. ;)

(You need to wait for the output from that command. Give it time, it doesn't happen immediately. You're closing the terminal before the output arrives.)

---

### Post by BlackfyreTR on 2013-08-08
Here it is:

> blackfyre@Blackfyre:~$ sudo lshw -C network[sudo] password for blackfyre: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:53:44:4b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: f0:7b:cb:13:83:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.8.0-27-generic firmware=478.104 link=no multicast=yes wireless=IEEE 802.11bg
blackfyre@Blackfyre:~$ ,




---

### Post by BlackfyreTR on 2013-08-08
the "hardware switch" thingie is now gone, and its fixed.
Thanks everybody, I'm trying to learn code, because I think my generation sucks (I'm 13 years old~)

---

