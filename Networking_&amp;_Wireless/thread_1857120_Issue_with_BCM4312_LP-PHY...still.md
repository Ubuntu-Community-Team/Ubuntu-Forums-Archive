---
title: "Issue with BCM4312 LP-PHY...still"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by daniel.p on 2011-10-09
I'm using Blackbuntu which is basically Ubuntu 10.10 with pen-testing tools included. I finally got tired of dual-booting backtrack and Ubuntu so this is my happy medium. That being said, I'm still having issues with wireless. Here's a few terminal outputs, hopefully I can get it fixed.

lspci -nn | grep 14e4
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```lsmod
```
Module                  Size  Used by
binfmt_misc            13214  1 
parport_pc             27954  0 
ppdev                  12900  0 
dm_crypt               18283  0 
snd_hda_codec_idt      55770  1 
snd_hda_intel          23931  2 
snd_hda_codec          79025  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                67876  2 snd_hda_intel,snd_hda_codec
joydev                 17335  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25253  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
uvcvideo               58440  0 
snd_seq                47265  2 snd_seq_midi,snd_seq_midi_event
b43                   293243  0 
videodev               77083  1 uvcvideo
snd_timer              24609  2 snd_pcm,snd_seq
psmouse                55034  0 
serio_raw              13046  0 
snd_seq_device         14152  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    51661  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mac80211              231044  1 b43
cfg80211              142832  2 b43,mac80211
lp                     13419  0 
parport                32607  3 parport_pc,ppdev,lp
dm_raid45              79668  0 
xor                    21893  1 dm_raid45
i915                  348314  3 
wmi                    14516  1 hp_wmi
drm_kms_helper         32697  1 i915
drm                   175542  4 i915,drm_kms_helper
ssb                    42118  1 b43
atl1c                  32013  0 
i2c_algo_bit           13218  1 i915
video                  18792  1 i915

```rfkill list all
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lshw -C network
```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:25:b3:58:1b:09
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:febc0000-febfffff ioport:ec80(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:25:56:5c:71:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-7-bb firmware=478.104 link=no multicast=yes wireless=IEEE 802.11bg

```NOTE: I am not using network-manager and have completely removed it. I prefer Wicd, so that is what is installed. I have version 1.6.1 as version 1.7 has issues connecting to networks secured with WPA.

With Wicd I get past the authentication then hang up on obtaining IP address. After about a minute I get a message saying it was unable to obtain an IP.

Another thing that might be worth mentioning is I've installed *firmware-b43-lpphy-installer*, however it does not show up under System -> Administration -> Additional Drivers. The only driver listed there is the normal b43, even the STA driver isn't listed.

---

### Post by praseodym on 2011-10-09
Hi,

this device only works (maybe) from kernel 2.6.36 and on with driver b43. Install the STA-driver via cable:

```
sudo apt-get install --reinstall dkms patch fakeroot bcmwl-kernel-source
sudo depmod -a
```
or the packages from CD

---

### Post by daniel.p on 2011-10-09
> **praseodym said:**
> Hi,

this device only works (maybe) from kernel 2.6.36 and on with driver b43. Install the STA-driver via cable:

```
sudo apt-get install --reinstall dkms patch fakeroot bcmwl-kernel-source
sudo depmod -a
```
or the packages from CD

My blackbuntu box currently has kernel 3.0.0-7 from the blackbuntu archives. The strange thing is I've gotten it to work once from a fresh install, tinkered with stuff, killed it, couldn't fix it, reinstalled, and have not been able to reproduce working wireless since then. If it is in fact a kernel issue though, I can try one of the Ubuntu mainline kernels and go from there. I suppose at this point it couldn't hurt.

---

### Post by praseodym on 2011-10-09
Or you compile it by hand:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#post-2865859](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#post-2865859)

Translate that posting and compile. Pay attention to 32/64bit.

---

### Post by daniel.p on 2011-10-09
> **praseodym said:**
> Or you compile it by hand:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#post-2865859](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#post-2865859)

Translate that posting and compile. Pay attention to 32/64bit.

I'll go with that option. Compiling by hand sounds like it'd be more interesting/entertaining than just downloading and installing a kernel.

EDIT: I went ahead and translated the site and noticed a problem right away. The "blacklist b43" can't happen. For injection to work with the card in this netbook it has to use the b43 driver, not STA. I'll try changing my kernel for now and see what happens.

---

