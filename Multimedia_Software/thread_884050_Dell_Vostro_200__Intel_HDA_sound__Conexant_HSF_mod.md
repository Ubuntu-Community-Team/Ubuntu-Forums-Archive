---
title: "Dell Vostro 200 / Intel HDA sound / Conexant HSF modem"
date: 2008-08-08
forum: Multimedia Software
---

### Post by sean4u on 2008-08-08
I lost an hour or so of my life to the modem and sound in my new Dell Vostro 200. Dell is selling this model super cheap in Malaysia currently, with no Windows installed. I'm really liking it, apart from the sound and modem.

I installed a .deb for the modem from a Dell site (I'll track it down again if anyone wants to know - it was on another PC). The modem worked a treat. Went back to some content with audio - no sound. Saw some other threads on here about Dell / Intel HDA / Alsa, and tried almost all of the suggestions in them, to no avail.

The one suggestion I didn't try was to reinstall modules / ubuntu. I'd just installed it fresh, even if it was going to work, it seemed silly. Looking at the output of

```
lsmod | grep snd
```

I couldn't see a device driver... I was expecting something to do with the Intel HDA device that I could see when I type 'lspci'. So I had a look in

```
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci
```

...and there was the answer! The snd-hda-intel module was there, alright, but the module was called

```
snd-hda-intel.ko.REPLACEDBYhsfmodem
```:lolflag:

So if anybody else is in the same spot, this is another thing to check! Just renaming that module to

```
snd-hda-intel.ko
```

and doing 'modprobe snd-hda-intel' had sound back for me.

I hope this saves someone some life!

---

