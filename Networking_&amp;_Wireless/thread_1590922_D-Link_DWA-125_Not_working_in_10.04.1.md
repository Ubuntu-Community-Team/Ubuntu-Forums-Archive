---
title: "D-Link DWA-125 Not working in 10.04.1"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by WhyCali on 2010-10-08
[FONT=Arial][SIZE=2]I had to reinstall 10.04.1 from scratch, and can't get the DWA-125 USB N adapter working. I'm not sure how I got it to work before, but it was working under 10.04.1.

I've looked at [http://ubuntuforums.org/showthread.php?t=1518043](http://ubuntuforums.org/showthread.php?t=1518043) and tried it, but no luck.

Below is some more info about my system. Before reloading, when the DWA-125 USB was working, both of my network adapters worked at the same time. I'd prefer to disable the internal G adapter, but only once i get the DWA-125 working.

Thanks for your help!

Mike

[B]lsusb:
[/B] 
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1058:070c Western Digital Technologies, Inc.
Bus 001 Device 003: ID 07d1:3c16 D-Link System
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```[B]lshw -C network
[/B] 
```
 *-network              
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:73:ae:f6
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 memory:fe1fc000-fe1fffff ioport:d800(size=256) memory:fe1c0000-fe1dffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:6a:70:0a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.107 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:fe2f0000-fe2fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 multicast=yes wireless=Ralink STA
```**lsmod**

```
Module                  Size  Used by
cryptd                  8116  0
aes_x86_64              7912  1
aes_generic            27607  1 aes_x86_64
udf                    85529  0
crc_itu_t               1715  1 udf
binfmt_misc             7960  1
ppdev                   6375  0
lp                      9336  0
parport                37160  2 ppdev,lp
dm_crypt               13043  0
snd_hda_codec_realtek   279040  1
arc4                    1473  2
snd_hda_intel          25773  2
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0
snd_seq_oss            31219  0
ath5k                 134405  0
snd_seq_midi            5829  0
snd_rawmidi            23420  1 snd_seq_midi
mac80211              238896  1 ath5k
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
sdhci_pci               6700  0
pcmcia                 35580  0
ath                     9723  1 ath5k
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci                  17928  1 sdhci_pci
cfg80211              148725  3 ath5k,mac80211,ath
yenta_socket           22901  1
fujitsu_laptop         12753  0
snd_timer              23649  2 snd_pcm,snd_seq
rsrc_nonstatic          9830  1 yenta_socket
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               3764  3 ath5k,sdhci,fujitsu_laptop
joydev                 11072  0
pcmcia_core            38176  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9639  0
rt2870sta             618586  0
snd                    71187  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  3944  0
soundcore               8052  1 snd
psmouse                64576  0
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
edac_core              45423  0
edac_mce_amd            9278  0
shpchp                 33711  0
serio_raw               4918  0
squashfs               21868  1
aufs                  175496  1
nls_iso8859_1           4633  1
nls_cp437               6351  1
vfat                   10866  1
fat                    55350  1 vfat
ses                     6683  0
enclosure               8649  1 ses
dm_raid45              75532  0
xor                     4685  1 dm_raid45
fbcon                  39270  71
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0
vgastate                9857  1 vga16fb
radeon                740890  3
ttm                    60847  1 radeon
video                  20623  0
drm_kms_helper         30742  1 radeon
ohci1394               30260  0
usbhid                 41084  0
hid                    83472  1 usbhid
usb_storage            49961  3
output                  2503  1 video
ieee1394               94771  1 ohci1394
sky2                   48835  0
drm                   198948  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
pata_atiixp             4209  0
sata_sil                8895  0
```**iwconfig**

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

wlan0     IEEE 802.11abg  ESSID:"maxwell"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 68:7F:74:17:3A:04  
          Bit Rate=1 Mb/s   Tx-Power=27 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```[/SIZE][/FONT]

---

