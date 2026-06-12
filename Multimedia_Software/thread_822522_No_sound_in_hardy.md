---
title: "No sound in hardy"
date: 2008-06-08
forum: Multimedia Software
---

### Post by cwrann on 2008-06-08
I have tried everything I can find in the forums and I still cannot get my sound to work in Hardy.

I have turned off my onboard sound card in BIOS and am trying to get my soundblaster audigy card to work.

here is what aplay -l tells me.

```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Nothing is muted, all the volumes are up. I can't figure this out.

---

### Post by Pjotr123 on 2008-06-08
This will probably fix it:
- Right click on the speaker icon (Volume Control) on the top panel.
- Make sure that Volume control is using your device Audigy 1, et cetera.
           - If wrong device, change it by clicking, File
           - Change Device
           - Select your device
- From here some new tabs should show up in the main window.
- Click the Switches Tab
- Uncheck Audigy Analog / Digital Output Jack

That's it.  :)

Greeting, Pjotr.

---

### Post by cwrann on 2008-06-08
P.S.

I did a fresh install of the hardy heron live cd, the AMD 64 version.

---

### Post by Pjotr123 on 2008-06-08
> **cwrann said:**
> P.S.

I did a fresh install of the hardy heron live cd, the AMD 64 version.

Our posts have crossed: look above. :)

---

### Post by cwrann on 2008-06-08
Under switches the text next to the box is "IEC958"
Unchecking this box is what got the sound working in gutsy, no such luck in Hardy.

---

### Post by cwrann on 2008-06-08
I don't know how I did it but I got sound back. ( I really don't know how, I tried a bunch of things nothing worked, them I opened the sound controls, like I already did a hundred times and the sound kicked on without doing anything.)

However the sound is analog, should I be able to control the sound with the IEC958 controls?

---

### Post by Pjotr123 on 2008-06-08
> **cwrann said:**
> I don't know how I did it but I got sound back. ( I really don't know how, I tried a bunch of things nothing worked, them I opened the sound controls, like I already did a hundred times and the sound kicked on without doing anything.)

However the sound is analog, should I be able to control the sound with the IEC958 controls?

If it isn't broken (anymore), then don't fix it....  :)

The problem for this particular sound card seems to lie in the digital / analog switch. So you'd better leave things as they are, is my advice.

---

