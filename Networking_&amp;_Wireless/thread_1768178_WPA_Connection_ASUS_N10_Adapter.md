---
title: "WPA Connection ASUS N10 Adapter"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by sharpbiohazard on 2011-05-26
Hello all, brand-new to Ubuntu.

I am having a problem connecting to my home's wireless. My wireless adapter is working, because it is showing other networks in my neighborhood. With the sudo iwlist scan command I am seeing networks, including my home network that is hidden from broadcasting.

When I go to "Connect to a hidden wireless network," I put in the SSID and password. The wireless icon shows that it is trying to connect, but then hangs. I am then shown a window that states "Wireless Network Authentication Required." I re-input the password, but I am then faced with a looping process of hanging and then re-inputing the password after that.

Just to clarify, my network is WPA secured, and does not broadcast publicly.
Using Ubuntu 11.04.

I am brand new to using Linux, Ubuntu, and the terminal, so any help needs to be dumbed down for my sake :)

This is my wireless adapter - [http://www.asus.com/Networks/WiFi_Networking/USBN10/](http://www.asus.com/Networks/WiFi_Networking/USBN10/)

---

### Post by chili555 on 2011-05-26
Does your card really use the r8192su driver? Please post:```
lsmod | grep 8192
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by sharpbiohazard on 2011-05-26
It appears as entering grep 8192 does nothing. I therefore entered lsmod only.
```
username@username-System-Product-Name:~$ lsmod | grep 8192
username@username-System-Product-Name:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_via      56765  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
psmouse                73312  0 
nvidia               7098106  24 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
r8712u                281937  0 
lp                     13349  0 
asus_atk0110           17664  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
atl1e                  32576  0 
username@username-System-Product-Name:~$ 
```

---

### Post by chili555 on 2011-05-26
Ahh! Your device uses r8712u. I am not sure whether it's Network Manager, wpa_supplicant, r8712u or an unfortunate combination of the three but hidden networks are always very tricky. Can you connect if the SSID is broadcast? If so, I suggest you broadcast; neither I nor Google seem to have any magic fix. Sorry.

---

### Post by sharpbiohazard on 2011-05-27
So I am out of luck even though ASUS provides a Linux driver on the page I gave above?

---

### Post by chili555 on 2011-05-27
> r8712u                281937  0 Your installation provides a driver that is more current than on the website. Except for hidden networks, I assume it is working fine:> My wireless adapter is working, because it is showing other networks in my neighborhood. With the sudo iwlist scan command I am seeing networks, including my home network that is hidden from broadcasting.

---

