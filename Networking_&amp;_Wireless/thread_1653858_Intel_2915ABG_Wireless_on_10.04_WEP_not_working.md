---
title: "Intel 2915ABG Wireless on 10.04: WEP not working"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by openversus on 2010-12-27
Recently I need top use the wireless card but unfortunately, after having switched on to the zyxel 600HW series, can not login: I've read many posts with no results.
I'm trying to use the wireless card and with Ubuntu 10.04 'as follows:

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:03:25:25:02:db
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.33 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:c4000000-c4003fff ioport:4000(size=256) memory:d8000000-d801ffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:c8:97:ce
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:17 memory:c8008000-c8008fff

The ipw2200 module seems to be charged:

lsmod
Module                  Size  Used by
arc4                    1153  0
lib80211_crypt_wep      2667  0
binfmt_misc             6587  1
ppdev                   5259  0
vboxnetflt             12740  0
vboxdrv               168721  1 vboxnetflt
fbcon                  35102  71
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0
vgastate                8961  1 vga16fb
ipw2200               135216  0
libipw                 39896  1 ipw2200
lib80211                5046  3 lib80211_crypt_wep,ipw2200,libipw
snd_intel8x0           25588  2
snd_hda_intel          22005  0
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_mixer_oss          13746  1 snd_pcm_oss
joydev                  8708  0
snd_seq_dummy           1338  0
snd_pcm                70694  5 snd_intel8x0,snd_hda_intel,snd_ac97_codec,snd_pcm_oss,snd_hda_codec
snd_seq_oss            26722  0
snd_seq_midi            4557  0
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                 30784  0
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                676897  3
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
yenta_socket           20408  1
sdhci_pci               5470  0
tifm_7xx1               3690  0
drm_kms_helper         29329  1 radeon
rsrc_nonstatic         10015  1 yenta_socket
video                  17375  0
output                  1871  1 video
sdhci                  15462  1 sdhci_pci
snd                    54180  17 snd_intel8x0,snd_hda_intel,snd_ac97_codec,snd_pcm_oss,snd_hda_codec,snd_hwdep,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  0
tifm_core               6045  1 tifm_7xx1
psmouse                63245  0
serio_raw               3978  0
drm                   162409  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               2864  1 sdhci
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_intel8x0,snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,intel_agp,drm
usbserial              33019  0
lp                      7028  0
parport                32635  2 ppdev,lp
ohci1394               26950  0
ieee1394               81181  1 ohci1394
sky2                   40807  0


I tried to remove the authenitication and I can connect ... but obviously it's not the solution :-)

Anyone can 'help me?

---

