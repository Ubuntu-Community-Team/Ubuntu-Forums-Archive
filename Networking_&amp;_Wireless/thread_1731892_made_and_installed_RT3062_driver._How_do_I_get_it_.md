---
title: "made and installed RT3062 driver. How do I get it to load?"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by itguy1985 on 2011-04-17
There were no errors or anything during the make and install. Now I just need to know how to start it.

---

### Post by itguy1985 on 2011-04-17
did iwconfig got


Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
It knows it's there but it's not working.

---

### Post by Leppie on 2011-04-17
did you load the module?
what is the output of:
```
lsmod
```

---

### Post by itguy1985 on 2011-04-17
~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
rt3562sta             948128  0 
snd_hda_codec_realtek   336647  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nouveau               682322  2 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ttm                    76664  1 nouveau
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42136  1 nouveau
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227573  4 nouveau,ttm,drm_kms_helper
sp5100_tco             13707  0 
i2c_algo_bit           13400  1 nouveau
psmouse                73535  0 
video                  19438  1 nouveau
edac_core              53845  0 
soundcore              12680  1 snd
serio_raw              13166  0 
i2c_piix4              13303  0 
edac_mce_amd           23464  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k10temp                13119  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  1 
ahci                   25951  2 
uas                    17996  0 
r8169                  48022  0 
libahci                26642  1 ahci
pata_atiixp            13165  0 
nolan@THEMAN:~$

---

### Post by itguy1985 on 2011-04-17
Don't have a hardwire, only wireless, have to log in and out to respond. I'm sorry if it's taking to long.

---

### Post by Leppie on 2011-04-17
looks like it's still using the old rt3562sta driver.
issue these commands:
```
sudo rmmod rt3562sta
sudo modprobe rt3062
```

---

### Post by MooPi on 2011-04-17
The 3062 chip uses rt3562.sta so all you need to do is 
```
sudo modprobe rt3562.sta
```
Your wireless will probably be designated ra0 instead of wlan0.
Just to check all bases before I assume it will work what is the results for lspci
Here is my tutorial for the chip in question.  [http://ubuntuforums.org/showthread.php?t=1608095]("http://ubuntuforums.org/showthread.php?t=1608095")

---

### Post by itguy1985 on 2011-04-17
> **MooPi said:**
> The 3062 chip uses rt3562.sta so all you need to do is 
```
sudo modprobe rt3562.sta
```Your wireless will probably be designated ra0 instead of wlan0.
Just to check all bases before I assume it will work what is the results for lspci
Here is my tutorial for the chip in question.  [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095)

Thanks. I started over and used your tutorial everything is working fine now.

---

