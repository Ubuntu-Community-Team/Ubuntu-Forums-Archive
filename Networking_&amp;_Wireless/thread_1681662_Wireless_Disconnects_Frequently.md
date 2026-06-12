---
title: "Wireless Disconnects Frequently"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by Leprkan on 2011-02-04
This is strange:

I'm using rt2870sta drivers for my RNX-N1MAC wireless card. It manages to connect but then frequently disconnects every few seconds.

Here's where it gets weird...

In frustration I disabled wireless from the network manager to find... my wireless works perfectly now.

I could just leave it at that, but I kinda wanna know what's going on.  

Seems like a conflicting driver issue but lsmod returns:

```
Module                  Size  Used by
aes_i586                7280  504 
aes_generic            26875  1 aes_i586
dm_crypt               11385  0 
binfmt_misc             6599  1 
nvidia               9329739  52 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22203  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26058  1 
rt2870sta             406690  1 
agpgart                32011  1 nvidia
joydev                  8767  0 
soundcore                880  1 snd
crc_ccitt               1351  1 rt2870sta
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59033  0 
serio_raw               4022  0 
shpchp                 29886  0 
i2c_nforce2             5179  0 
asus_atk0110           11423  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21234  0 
firewire_core          46643  1 firewire_ohci
usbhid                 36882  0 
hid                    67742  1 usbhid
floppy                 54311  0 
crc_itu_t               1383  1 firewire_core
forcedeth              49433  0 
sata_nv                19420  2 
pata_amd                8746  0 
```

and I don't see any conflicts.

My blacklist looks like this:

```
# Blaclisted to prevent driver conflict
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
```


Someone sate my curiosity!
Alex

---

### Post by Leprkan on 2011-02-20
*shameless bump* d(^.^)b

---

