---
title: "usrobotics 5416 pci troubleshooting"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by BikerBandit on 2011-09-08
linux newbie. spent two days on this (...) hope someone can help ;)

pc desktop, no brand, intel pentium 4 3ghz, 2gb ram, video board ati 3450, usrobotics pci wireless
os lubuntu 11.04
system works just fine under win xp since years.


during wifi troubleshooting i have been following recommendation found at:
[https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111](https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111)

as well as
[http://sourceforge.net/apps/mediawiki/acx100/index.php?title=ACX](http://sourceforge.net/apps/mediawiki/acx100/index.php?title=ACX)

by using firmware tiacxlllc16 from 
[http://acx100.erley.org/fw/acx111_1.2.1.34/](http://acx100.erley.org/fw/acx111_1.2.1.34/)

and using driver from
[http://sourceforge.net/projects/acx100/files/acx100/20080210/acx-20080210.tar.bz2](http://sourceforge.net/projects/acx100/files/acx100/20080210/acx-20080210.tar.bz2)

nevertheless i keep on getting same error on step:
make -C /lib/modules/`uname -r`/build M=`pwd`

as follows:

luca@luca-P4M800PRO-M:~/ACX/acx-20080210$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/luca/ACX/acx-20080210/wlan.o
In file included from /home/luca/ACX/acx-20080210/acx.h:2:0,
                 from /home/luca/ACX/acx-20080210/wlan.c:49:
/home/luca/ACX/acx-20080210/wlan_compat.h:224:14: error: conflicting types for ‘irqreturn_t’
include/linux/irqreturn.h:16:24: note: previous declaration of ‘irqreturn_t’ was here
In file included from /home/luca/ACX/acx-20080210/acx.h:6:0,
                 from /home/luca/ACX/acx-20080210/wlan.c:49:
/home/luca/ACX/acx-20080210/acx_func.h:109:0: warning: "printk_ratelimited" redefined
include/linux/printk.h:237:0: note: this is the location of the previous definition
make[1]: *** [/home/luca/ACX/acx-20080210/wlan.o] Error 1
make: *** [_module_/home/luca/ACX/acx-20080210] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'


more details on system follow:

$ lspci
00:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

$ iwconfig
no wireless extensions

 $ ls mod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_via82xx            24685  0 
gameport               15027  1 snd_via82xx
snd_usb_audio          91410  0 
snd_ac97_codec        105614  1 snd_via82xx
snd_usbmidi_lib        24388  1 snd_usb_audio
ac97_bus               12642  1 snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
snd_hda_codec_hdmi     27535  1 
snd_seq_midi           13132  0 
snd_hda_intel          24113  1 
uvcvideo               66851  0 
snd_rawmidi            25269  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_hda_codec          90901  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
snd_pcm                80042  6 snd_via82xx,snd_usb_audio,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_page_alloc         14073  3 snd_via82xx,snd_hda_intel,snd_pcm
videodev               75143  1 uvcvideo
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  16 snd_via82xx,snd_usb_audio,snd_usbmidi_lib,snd_ac97_codec,snd_mpu401_uart,snd_hda_codec_hdmi,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
shpchp                 32345  0 
i2c_viapro             12969  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
radeon                900494  2 
ttm                    65184  1 radeon
8139too                23208  0 
drm_kms_helper         40745  1 radeon
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0 
drm                   184164  4 radeon,ttm,drm_kms_helper
pata_via               13368  0 
8139cp                 22497  0 
sata_sil               13278  2 
i2c_algo_bit           13184  1 radeon

$ lsb_release -d
Ubuntu 11.04

$ uname -mr
2.6.38.11-generic i686

---

