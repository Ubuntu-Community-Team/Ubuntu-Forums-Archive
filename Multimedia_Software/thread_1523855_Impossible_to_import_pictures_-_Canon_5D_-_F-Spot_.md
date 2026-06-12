---
title: "Impossible to import pictures - Canon 5D - F-Spot LibGphoto2"
date: 2010-07-04
forum: Multimedia Software
---

### Post by dudumomo on 2010-07-04
Hi everyone !

I got serious difficulties to import pictures from my Canon 5D on my Lynx 64b system.

When I tried to import pictures with F-Spot using a USB Cable, I got the following error:
```
Error GeneralError: LibGPhoto2.GP&#7719;otoException: Erreur indéfinie
at LibGPhoto2.Error.CheckError (ErrorCode error) [0x00000]
etc....
```

But with my Canon G11 still with the USB cable, everything works !

I have no idea why....

And if I try to copy my pics without F-Spot, just with nautilus, it doesn't work...


Any idea ?

The G11 uses a SD card and the 5D a CF card.
May be a problem with that ? or with the filesystem ? I don't know.

Thank you for your help !!

---

### Post by mouths on 2010-07-04
Canon doesn't supply raw codecs for 64bit systems.

(Not even for Win or Mac)

In 32bit linux kernel canon raw codec is preinstalled.

---

### Post by dudumomo on 2010-07-04
> **mouths said:**
> Canon doesn't supply raw codecs for 64bit systems.

(Not even for Win or Mac)

In 32bit linux kernel canon raw codec is preinstalled.

The pictures are saved in jpg (As we can select either RAW or JPG in the settings of the 5D)
So...is it really linked to the 64b system....?

I might try a 32b live cd to be sure !

---

### Post by dudumomo on 2010-07-06
I didn't try yet a 32b System, but I don't understand why a 32b system will do better as the pictures are in JPG....

---

### Post by mouths on 2010-07-07
Yor problem lives in the  LibGPhoto2.

Try reinstalling it through synaptic.

Check first to restore ruined packages (synaptic),

make update and upgrade and see if it's ok.

But my objection is why to use the lossy jpeg format

instead of the lossless RAW.

---

