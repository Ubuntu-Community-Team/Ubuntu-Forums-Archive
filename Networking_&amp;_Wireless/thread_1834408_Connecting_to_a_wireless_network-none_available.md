---
title: "Connecting to a wireless network-none available"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by birdhen on 2011-08-27
Hi there,
I am a beginner and I have no idea how to connect to my wireless network. When I click on the internet icon the wireless networks tab is dark gray and can't be clicked on. I have tried to go through the instructions on many websites to no avail.
Can anyone help?
Thanks!

---

### Post by wildmanne39 on 2011-08-27
Hi, please run these commands in a terminal and post the out come here:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
lsmod
```
```
rfkill list all
```
Thank you

---

### Post by birdhen on 2011-08-27
[QUOTE=wildmanne39;11192727]Hi, please run these commands in a terminal and post the out come here:
[CODE]sudo lshw -C network[
*-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 40:61:86:a5:fa:e0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fdef0000-fdefffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 40:61:86:b4:1d:6f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:d800(size=256) memory:f9fff000-f9ffffff memory:f9ff8000-f9ffbfff memory:fdfe0000-fdffffff

[CODE]lspci -nn | grep 0280[
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]]

[CODE]iwconfig[
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
]
[CODE]lsmod[
Module                  Size  Used by
usb_storage            50372  1
parport_pc             30086  0
ppdev                   6804  0
binfmt_misc             7984  1
snd_hda_codec_atihdmi     3079  1
joydev                 11363  0
snd_hda_codec_realtek   299533  1
snd_hda_intel          26019  2
rt2860sta             559618  0
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
arc4                    1497  2
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0
radeon                906714  3
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
rt2800pci              10233  0
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
snd_timer              23850  2 snd_pcm,snd_seq
ttm                    68212  1 radeon
rt2x00pci               6993  1 rt2800pci
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt               1699  2 rt2860sta,rt2800pci
drm_kms_helper         32836  1 radeon
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
drm                   206161  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            6208  1 radeon
edac_core              46822  0
soundcore               1240  1 snd
cfg80211              170293  2 rt2x00lib,mac80211
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_piix4              10047  0
edac_mce_amd            9387  0
shpchp                 34910  0
k10temp                 3535  0
eeprom_93cx6            1789  1 rt2800pci
psmouse                62080  0
serio_raw               4910  0
video                  22176  0
output                  2527  1 video
lp                     10201  0
parport                37032  3 parport_pc,ppdev,lp
r8169                  42222  0
mii                     5261  1 r8169
ahci                   21857  0
libahci                26167  3 ahci
]
[CODE]rfkill list all[
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
]
Thank you!

---

### Post by birdhen on 2011-08-27
I guess the face icons were supposed to be something else..I coied and pasted..

---

### Post by wildmanne39 on 2011-08-27
Hi, please post the outcome of this command.
```
cat /etc/lsb-release; uname -a
```
Thank you

---

### Post by birdhen on 2011-08-27
> **wildmanne39 said:**
> Hi, please post the outcome of this command.
[CODE]cat /etc/lsb-release; uname -a[
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux angela-unix 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
]
Thank you.

---

### Post by wildmanne39 on 2011-08-27
Hi, lets blacklist some drivers.
```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
exit
echo "blacklist rt2x00pci " >> /etc/modprobe.d/blacklist.conf

```
now unplug your wired connection and restart your computer and see if wireless comes on.
Thank you

---

### Post by birdhen on 2011-08-27
No, it is still almost the same as before except now I can go to connect to hidden networks and it tries to connect but doesn't.
PS thank you for all your help!

---

### Post by wildmanne39 on 2011-08-27
Hi, first unhide your network, then post the results of these commands please:
```
nm-tool
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
lsmod | grep rt2
```
```
dmesg | grep rt2
```
Thank you

---

### Post by birdhen on 2011-08-27
Hi,

I will have to come back to this in a week as I am going away now. Thank you for all your help so far!

---

### Post by wildmanne39 on 2011-08-27
Hi, your welcome! I will see you when you get back.

---

