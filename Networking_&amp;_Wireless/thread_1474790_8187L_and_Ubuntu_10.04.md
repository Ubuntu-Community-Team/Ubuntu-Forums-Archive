---
title: "8187L and Ubuntu 10.04"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by skan on 2010-05-06
Hi

I've just installed Ubuntu 10.04 and my wireless (eRize with Realtek 8187L) doesn't work.
It seems to be connected but I can't surf the web, though I can use aircrack.
In Windows I can surf without problems.

Two days ago I read I had to install new drivers and I installed compat-wireless.
Everything got compiled and installed but I still can't surf.

**lsmod**
> 
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_codec_realtek   278890  1 
arc4                    1473  2 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
nouveau               515131  2 
rtl8187                53204  0 
ttm                    60815  1 nouveau
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              238128  1 rtl8187
drm_kms_helper         30742  1 nouveau
led_class               3732  1 rtl8187
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198770  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
cfg80211              148386  2 rtl8187,mac80211
eeprom_93cx6            1765  1 rtl8187
soundcore               8052  1 snd
xhci                   40958  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
pata_jmicron            2747  0 
ahci                   37646  2 
**ifconfig**

> 
lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:32 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:32 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:2087 (2.0 KB)  TX bytes:2087 (2.0 KB)

mon0      Link encap:UNSPEC  direcciónHW XX-XX-XX-XX-XX-XX-00-00-00-00-00-00-00-00-00-00  
          ACTIVO DIFUSIÓN SINAVANCES FUNCIONANDO PROMISCUO ALLMULTI  MTU:1500  Métrica:1
          Paquetes RX:94969 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:12357324 (12.3 MB)  TX bytes:0 (0.0 B)

wlan0     Link encap:UNSPEC  direcciónHW XX-XX-XX-XX-XX-XX-00-00-00-00-00-00-00-00-00-00  
          ACTIVO DIFUSIÓN  MTU:1500  Métrica:1
          Paquetes RX:87543 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:80 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:11310974 (11.3 MB)  TX bytes:14049 (14.0 KB)
**iwconfig**

> 
lo        no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Monitor  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon0      IEEE 802.11bg  Mode:Monitor  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

What drivers should I remove and what other should I install and how?
Thanks

---

