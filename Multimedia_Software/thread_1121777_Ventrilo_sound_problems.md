---
title: "Ventrilo sound problems"
date: 2009-04-10
forum: Multimedia Software
---

### Post by alzorz on 2009-04-10
Recently my headsets mic died so i took out my old AK5370 mic, fyi im only using the mic for ventrilo running through wine. At first the mic didn't work so i googled abit about it and found this:
```
pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:0,0"
}
capture.pcm {
type plug
slave.pcm "hw:1,0"
}
} 
```
which was pasted in the .asoundrc file in my home folder after doing this my mic work with ventrilo but now i don't have any sound.

from "aplay -l" i get this this
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
and from "arecord -l" this
```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [AK5370          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

according to that text it seems to me (knows nothing about linux) that it should work, my sound works great with spotify (also running in wine) but in ventrilo i have nothing.

Anyone knows what im doing wrong here?

EDIT: after looking into it some more i found the reason for my loss of sound. In winecfg audio i found out that after pasting the code in .asoundrc i didn't have any wave out device, and if i remove the code from .asoundrc i get a wave out devide and the sound works great anyone know how i can change the code to get both?

---

### Post by alzorz on 2009-04-11
anyone?

---

### Post by arterio on 2009-04-20
I'm having an issue getting my mic to work in Ventrilo in WINE. It works fine in Ubuntu, but I can't get it to work in Ventrilo.

Using Asus Xonar DX sound card.

---

### Post by arterio on 2009-04-20
EDIT:
Seems that my mic is working in Ventrilo, I just thought it wasn't because when I was trying to do the sound test I couldn't hear myself, but people on Ventrilo can hear me.

---

