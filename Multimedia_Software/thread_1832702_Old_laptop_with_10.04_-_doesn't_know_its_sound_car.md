---
title: "Old laptop with 10.04 - doesn't know its sound card?"
date: 2011-08-25
forum: Multimedia Software
---

### Post by .CID on 2011-08-25
Hi all,

I've been struggling to get my old toshiba laptop (Satellite Pro 4200) to record audio. Seems simple, doesn't it? >_< 
I can't seem to get any input on the mic port, and was just about starting to think the sound card is broken, until I noticed this:

according to LSHW, the card in the laptop is 
```
 id:    
multimedia
description:     Multimedia audio controller
product:     YMF-744B [DS-1S Audio Controller]
vendor:     Yamaha Corporation
physical id:     
c
bus info:     
pci@0000:00:0c.0
version:     02
width:     32 bits
clock:     33MHz
capabilities:     pm bus_master cap_list
configuration:    
driver    =    Yamaha DS-1 PCI
latency    =    64
maxlatency    =    25
mingnt    =    5
resources:    
irq    :    11
memory    :    febf8000-febfffff
ioport    :    ff00(size=64)
ioport    :    fefc(size=4)
```So far, so good. Now the weird part: after trying several mixers and even enabling all inputs at the same time, I installed yet another mixer: GNOME-ALSA mixer. This one shows one thing others didn't: the name of the sound card it controls. This is the part I can't figure out: it shows
```
Asahi Kasei AK4543
```and doesn't give me the option of using the Yamaha card or drivers.

Audio playback over the built-in speakers works peachy, no problems at all.. oddly enough. Also when sticking the mic jack into the appropriate jack I hear some cracking, which makes it even more confusing.

Does anyone have any ideas? I've been trying to get this to work for the past two weeks but I'm afraid I'm on a dead end atm..

thanks in advance!   

P.S. I'm running 10.04LTS with xfce4, and don't think it can handle anything newer.   

edit: line breaks ftw

---

### Post by .CID on 2011-08-25
Small update: Apparently the Asahi Kasei AK4543 is a chip on the sound card. I've managed to get *some* input on the mic now by compiling and installing alsa-firmware, but it's limited to noise or more noise with the +20db boost on.  Is there a way to check in the software for a busted sound card? (the insides look squeaky clean, so no traces of magic smoke) It's a second hand thing after all.

---

