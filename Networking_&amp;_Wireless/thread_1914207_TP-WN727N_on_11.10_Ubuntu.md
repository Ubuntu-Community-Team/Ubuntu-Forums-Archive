---
title: "TP-WN727N on 11.10 Ubuntu"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by samwalton on 2012-01-23
Hello WIreless gurus,
I have a tp link WN727N Version 3  that i am trying to get to work on Ubuntu 11.10 and have no luck.  I tried NDISGTK to load the driver and the wireless device does not work.. I tried compat wireless earlier and got error 2 and bunch of errors.. I am at my wits end .. By the way this worked when  i used ndisgtk in my 64 bit system ( WPA did not work ,so i had to turn off all wireless security to test the connectivity)
Here are the outputs you may want to see
> 
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:5370 Ralink Technology, Corp. 

> 

lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
binfmt_misc            17292  1 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
radeon                925178  2 
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
ttm                    65224  1 radeon
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39822  0 
psmouse                73673  0 
drm_kms_helper         32889  1 radeon
yenta_socket           27428  0 
drm                   192194  4 radeon,ttm,drm_kms_helper
pcmcia_rsrc            18367  1 yenta_socket
snd                    55902  12 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 radeon
shpchp                 32356  0 
ppdev                  12849  0 
nvram                  14029  1 thinkpad_acpi
video                  18908  0 
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e1000                 101773  0 
floppy                 60310  0 

> 
uname
3.0.0-15-generic


---

### Post by samwalton on 2012-01-25
Ok seemed to have fixed it. Needed to force the kernel to use the rt2800usb drivers.. Good instructions here.. 

[http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370](http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370)

---

