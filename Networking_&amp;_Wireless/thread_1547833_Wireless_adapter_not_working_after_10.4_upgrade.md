---
title: "Wireless adapter not working after 10.4 upgrade"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by tetsura on 2010-08-07
Hi. I upgraded to Ubuntu 10.4 on my Dell Inspiron 6400 yesterday (32-bit). Everything was running great, but when I turned it on today my wireless adapter is no longer working and the hardware switch doesn't do anything. It's working in Windows fine so it can't be the hardware.

Here is some information:

Adapater name: **Intel Corporation PRO/Wireless 3945ABG** [Golan] Network Connection (rev 02)

```
iwconfig:
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```

james@James-Ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
snd_hda_codec_idt      51978  1 
snd_hda_intel          21941  2 
arc4                    1153  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
radeon                674824  3 
iwl3945                68727  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
dell_wmi                1793  0 
iwlcore               105922  1 iwl3945
drm_kms_helper         29297  1 radeon
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             6856  0 
mac80211              205146  2 iwl3945,iwlcore
drm                   162377  5 radeon,ttm,drm_kms_helper
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  3 iwl3945,iwlcore,sdhci
dcdbas                  5422  1 dell_laptop
intel_agp              24119  0 
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
cfg80211              126517  3 iwl3945,iwlcore,mac80211
i2c_algo_bit            5028  1 radeon
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
usb_storage            39425  0 
b44                    25574  0 
ieee1394               81181  1 ohci1394
ssb                    38671  1 b44
mii                     4381  1 b44
```

```
james@James-Ubuntu:~$ dmesg | grep "iwl3945"
[   21.662926] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   21.662931] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   21.663068] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.663083] iwl3945 0000:0b:00.0: setting latency timer to 64
[   21.741280] iwl3945 0000:0b:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   21.741284] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.741437] iwl3945 0000:0b:00.0: irq 28 for MSI/MSI-X

```

Here it says it's disabled:
```
james@James-Ubuntu:~$ sudo lshw -C network
[sudo] password for james: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:ca:95:e5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:efcff000-efcfffff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:ae:fc:e4
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:ef9fe000-ef9fffff


```

```
james@James-Ubuntu:~$ iwlist scan wlan0
wlan0     Failed to read scan data : Network is down
```

```
Kernel:
2.6.32-24-generic i686
```

Restarting the network with 'sudo /etc/init.d/networking restart' didn't work.

If anyone could help me I would be SO grateful. I've tried Ubuntu several times before but usually there is one small issue which makes me go back to Windows. I love 10.4 so I hope I can get this working so I can stay on Ubuntu!

Thanks,
James

---

### Post by tetsura on 2010-08-09
Found a solution, I'm posting the solution here in case anyone else has the same problem.

It's caused by the laptop not going into sleep properly. To fix it, make sure all the values in the following 2 files are set to true:

/etc/NetworkManager/nm-system-settings.conf
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=**true**

```

/var/lib/NetworkManager/NetworkManager.state
```

[main]
NetworkingEnabled=**true**
WirelessEnabled=**true**
WWANEnabled=**true**
```

:)

---

### Post by nathron on 2010-09-14
Thank you for posting this tetsura I had the same issue ;)

---

### Post by athena3rm on 2010-12-28
Hello!
Can I please ask you how can I do it?
what does /etc/NetworkManager/nm-system-settings.conf
mean? could you please explain it for a beginner?
(sorry to bother, but if I cannot fix it I'll have to go back to windows, and I don't want to!)

> **tetsura said:**
> Found a solution, I'm posting the solution here in case anyone else has the same problem.

It's caused by the laptop not going into sleep properly. To fix it, make sure all the values in the following 2 files are set to true:

/etc/NetworkManager/nm-system-settings.conf
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=**true**

```

/var/lib/NetworkManager/NetworkManager.state
```

[main]
NetworkingEnabled=**true**
WirelessEnabled=**true**
WWANEnabled=**true**
```

:)

---

### Post by kevdog on 2010-12-28
/etc/NetworkManager/nm-system-settings.conf
 
This is a name of a file given as the absolute path.  You would edit this file as root.

---

### Post by interaubis on 2011-04-29
the file
/etc/NetworkManager/nm-system-settings.conf
is ok to change via sudo gedit, but the other one
/var/lib/NetworkManager/NetworkManager.state
no mather how many times I change it as 'root'  it keeps changing back to the "false" situation...

how to solve it???

tnks

---

