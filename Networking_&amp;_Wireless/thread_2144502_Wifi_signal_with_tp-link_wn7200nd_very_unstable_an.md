---
title: "Wifi signal with tp-link wn7200nd very unstable an fluctuating"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by Alfhw on 2013-05-12
Hi everyone. I have an Ubuntu 10.10-64 bit with a tp-link wn7200nd on usb. Ubuntu has recognized and loaded the driver rt2870sta for the ralink chipset (should be the 3070 according to wikidevi).
My problem is that the signal is very unstable keeping fluctuating from max signal to minimum (or even zero sometimes and disconnecting and reconnecting). My router is ok as I have a laptop with linux and atheros card and the signal is constant. I tried disabling N and WPA2 but with no luck. I also blacklisted rt2800usb, rt2x00usb, rt2800lib, rt2x00lib but again with no luck.

This is my iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"Alfa"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.457 GHz  Access Point: E0:46:9A:BA:89:70   
          Bit Rate=48 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=92/100  Signal level:-73 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


and this is my lsmod
```
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_nvhdmi    15451  1 
snd_hda_codec_realtek   300109  1 
nvidia              12312388  30 
binfmt_misc             7984  1 
snd_hda_intel          26147  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2870sta             446110  1 
usbhid                 42030  0 
snd                    64277  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt               1699  1 rt2870sta
psmouse                62126  0 
hid                    84966  1 usbhid
serio_raw               4910  0 
shpchp                 34910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_nforce2             6155  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22370  2 
libahci                26148  1 ahci
forcedeth              55649  0 

```

These are some screenshots taken with inSSIDer:
[ATTACH=CONFIG]242531[/ATTACH]
n with wpa2

[ATTACH=CONFIG]242529[/ATTACH]
b&g with wpa2

[ATTACH=CONFIG]242530[/ATTACH]
b&g without wpa2


I've noticed that signal drops happen when loading a web page but also when doing nothing.
Any idea on how to fix the problem?
Thanks

---

### Post by Alfhw on 2013-05-13
I've compiled and installed two drivers from [Ralink]("http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501")'s site: "RT2870USB(RT2870/RT2770) 	07/09/2010 	2.4.0.1" and the "RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB 	03/28/2012 	2.5.0.3". The first one doesn't make any difference and the second one doesn't work at all!
Does anyone has any suggestions before i throw this device out of the window???  ](*,)

---

