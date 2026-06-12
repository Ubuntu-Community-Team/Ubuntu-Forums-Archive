---
title: "ALSA DMIX issues"
date: 2012-03-05
forum: Multimedia Software
---

### Post by nadigo1 on 2012-03-05
Hi,

I have (L)ubuntu 11.04 and I run XBMC on top of it.
I have 2 sound cards, intel HDMI and USB audio (external, all on top of ALSA. I had set the USB to be the default one and I get sound out from XBMC. 

Recently I added another sound SW to the machine (squeezeslave)BUT i cant get both SW (XBMC and squeezeslave) to share the same card using ALSA dmix.   

I want to set the default card to be the dmix one so both will use it simultaneously with no added config  

I read a lot of articles and forums had tried various .asoundrc file versions - no luck.

I would appreciated any help, thanks

Nadav

```

sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: default [USB Sound Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

xbmc@MediaCenter:~$ sudo cat  /proc/asound/cards
 0 [default        ]: USB-Audio - USB Sound Device
                      C-Media INC. USB Sound Device         at usb-0000:00:1a.0-1.3, full speed
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xfbff8000 irq 47

```

```


pcm.dmixer {
    type dmix
    ipc_key 1024 #required and must be unique
    ipc_key_add_uid 0
    ipc_perm 0660
 slave.pcm {
        type hw card 0 device 0
    }
}

pcm.!default {
    type plug
    slave.pcm dmixer
}


ctl.!default {
    type hw card 0 device 0
}


```

---

