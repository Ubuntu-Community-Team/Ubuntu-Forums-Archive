---
title: "Onboard sound and PCI sound card. Default seems to be onboard, want PCI"
date: 2005-10-20
forum: Multimedia &amp; Video
---

### Post by michael117 on 2005-10-20
I have onboard sound and a Turtle Beach Santa Cruz 5.1 sound card. I've set up XMMS to use the Santa Cruz PCI card but I was trying to watch a video on video.google.com with Firefox and flash but heard no sound so I assume other programs or maybe the system default is to use the onboard when I would instead rather it use my PCI card. How could I change this?

Thanks.

---

### Post by chanders on 2005-10-20
Try disabling the onboard soundcard on your motherboard in the BIOS. That way it wont be visible to the kernel when it boots and you would be able to use your PCI card as the primary card....

---

### Post by michael117 on 2005-10-20
Hmm... yeah, I've thought about that but there are times when I'd like to boot to mac os x86 and the onboard sound is the only one that actually has driver support on the x86 version. Thanks.

---

### Post by dotwaffle on 2005-10-21
[quote=chanders]Try disabling the onboard soundcard on your motherboard in the BIOS. That way it wont be visible to the kernel when it boots and you would be able to use your PCI card as the primary card....[/quote]

This is all well and good, but I'd like to have Skype/SIP clients coming through my headset, which is plugged into my onboard card, and regular audio (xmms etc) come through my Audigy2.

Any ideas?

---

### Post by Greyfoxwolf on 2005-11-03
im curiouse too, i have the same problem

---

### Post by az on 2005-11-03
Can't you select multiple sound cards?  System- Preferences- Sound: Default sound card

---

### Post by Greyfoxwolf on 2005-11-04
there is something like override device location, by god i do not know how to use that option (KDE HERE), its just a bar ehre input is possible

---

### Post by Greyfoxwolf on 2005-11-06
anyone? doesnt anyone one know how to do this?

---

### Post by FloSynergy on 2006-03-23
hi there,

i've got the same issue...running audigy 2 zs pcmcia soundcard on kubuntu, on an asus a2 notebook.

kmixer recognises the sound card, but i'm not sure how to get it to ignore the onboard card (fried!) and route to the pcmcia...

the onboard sound card doesn't show up in the bios.....can't disable it there.

any ideas?

flo

---

### Post by FarEast on 2006-03-27
Hi;) ,

If you have 2 sound cards or more and want to define one of them as primary...

1. Execute 'lsmod | grep snd' to know the modules which drive them.

2. Edit(or create) /etc/modprobe.d/sound, for example, as follows:

```
options snd-emu10k1 index=0
options snd-ymfpci index=1
```

3. Execute 'sudo update-modules' and 'sudo /etc/init.d/alsa-utils restart'.

I hope this helps.

---

