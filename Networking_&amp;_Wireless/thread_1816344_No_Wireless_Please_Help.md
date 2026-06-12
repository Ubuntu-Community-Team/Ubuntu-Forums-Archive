---
title: "No Wireless Please Help"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by PredatorOSX on 2011-08-01
i just installed ubuntu 11.04 on my Compaq Presario V6105NR Notebook PC and the wireless doesn't work i activated Broadcom STA wireless driver but it didn't do anything whats so ever.
My wireless adapter is Broadcom 802.11 a/b/g WLAN Broadcom 802.11 b/g WLAN

If anyone knows how to fix please help :/

---

### Post by wildmanne39 on 2011-08-01
Hi, please run these commands in a terminal 
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
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

Also you will need to uninstall the sta driver.
Thank you

---

### Post by PredatorOSX on 2011-08-01
> **wildmanne39 said:**
> Hi, please run these commands in a terminal 
```
sudo lshw -C network 
``````
lspci -nn | grep 0280
``````
iwconfig
``````
rfkill list all
``````
lsmod
```and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

Also you will need to uninstall the sta driver.
Thank you
1.```
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:7b:b2:50
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)


```
2.```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```
3.```
lo        no wireless extensions.

eth0      no wireless extensions.

```
4.```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
5.```
Module                  Size  Used by
ndiswrapper           192828  0 
nls_utf8               12493  0 
udf                    83795  0 
crc_itu_t              12627  1 udf
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
binfmt_misc            13213  1 
i915                  450934  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
hp_wmi                 13418  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
wl                   2642531  0 
drm                   180037  4 i915,drm_kms_helper
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
soundcore              12600  1 snd
lib80211               14570  1 wl
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
e100                   40108  0 
```

And i installed  sta driver

---

### Post by wildmanne39 on 2011-08-01
Hi, you will need to get rid of ndiswrapper by 
```
sudo apt-get autoremove ndiswrapper
```
then run this command to install your driver and firmware.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
then unplug your wired connection and restart your computer, if you still heave problems run this command
```
lsmod | grep b43
```
and post the results here.
Thank you

---

### Post by PredatorOSX on 2011-08-01
OMG! you are a life saver thank you it worked

---

### Post by wildmanne39 on 2011-08-01
Hi, your welcome! I am glad I could help.

---

