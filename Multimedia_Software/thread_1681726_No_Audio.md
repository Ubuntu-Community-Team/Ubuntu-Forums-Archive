---
title: "No Audio?"
date: 2011-02-04
forum: Multimedia Software
---

### Post by vindicate on 2011-02-04
I installed Xubuntu to a flashdrive using unetbootin.  Since I only have a 2GB drive I installed Fluxbox instead of XFCE to save space.  I install alsa-utils to try to get some audio going.  aplay and speaker-test gets nothing at all.  Both as sudo and a reg user.  I have turn up the volume on everything in alsamixer.  I believe the relevant drivers are loaded.   I installed Xubuntu to a flashdrive using unetbootin.  Since I only have a 2GB drive I installed Fluxbox instead of XFCE to save space.  I install alsa-utils to try to get some audio going.  aplay and speaker-test gets nothing at all.  Both as sudo and a reg user.  I have turn up the volume on everything in alsamixer.  I believe the relevant drivers are loaded. 

```

Module                  Size  Used by
arc4                    1165  2 
lib80211_crypt_wep      2647  1 
ipw2200               136715  0 
libipw                 39808  1 ipw2200
radeon                829447  2 
pcmcia                 35973  0 
snd_intel8x0           25664  0 
ttm                    56633  1 radeon
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
drm_kms_helper         30200  1 radeon
joydev                  8767  0 
cfg80211              144694  2 ipw2200,libipw
dell_wmi_aio            1733  0 
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
drm                   168092  3 radeon,ttm,drm_kms_helper
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
dell_laptop             5730  0 
intel_agp              26566  0 
snd_timer              19067  1 snd_pcm
lib80211                5058  3 lib80211_crypt_wep,ipw2200,libipw
video                  18712  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
output                  1883  1 video
i2c_algo_bit            5168  1 radeon
agpgart                32011  3 ttm,intel_agp,drm
lp                      7342  0 
psmouse                59033  0 
dcdbas                  5402  1 dell_laptop
snd                    49038  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
parport                31492  1 lp
b44                    26253  0 
firewire_ohci          21234  0 
ssb                    39320  1 b44
sdhci_pci               6339  0 
firewire_core          46643  1 firewire_ohci
usb_storage            40172  2 
sdhci                  15890  1 sdhci_pci
led_class               2633  1 sdhci
mii                     4425  1 b44
crc_itu_t               1383  1 firewire_core

```

---

### Post by vindicate on 2011-02-05
Anyone?

---

