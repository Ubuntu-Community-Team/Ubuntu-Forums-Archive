---
title: "K3b FLAC ripping"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by Quintasan on 2007-02-04
Hello!
I have a problem with k3b
I've tried to rip audio tracks form my CD to HDD
And k3b instatly gave me an error
```
Error while encoding track 1.
```

And this is my debug output

```
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.6
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
LITE-ON DVDRW SHW-16H5S LS0R (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R dwuwarstwowa; DVD+R; DVD+RW; DVD+R dwuwarstwowa] [DVD-ROM; DVD-R sekwencyjna; DVD-R dwuwarstwowa sekwencyjna; DVD+R dwuwarstwowa; DVD-RW w trybie ograniczonego zast&#281;powania; DVD-RW sekwencyjny; DVD+RW; DVD+R; DVD+R dwuwarstwowa; CD-ROM; CD-R; CD-RW] [Sesja naraz (SAO); TAO; RAW; SAO/R96P; SAO/R96R; Surowe/R16; Surowe/R96P; Surowe/R96R; Ograniczone zast&#281;powanie; Przeskok warstwy]
```

Sorry for the polish words but I'm form Poland and the localization is downloaded automaticly, at polish forums noone could help me so I'm asking here

I forgot to mention that when i do ```
sudo k3b
``` everything works fine :S

---

### Post by threethirty on 2007-02-04
k3b is a burning app, not a ripping app.  I hate to tell you but I don't know what the KDE ripping app is.  I use GNOME for most things, but I use K3b all the time.

---

### Post by Quintasan on 2007-02-04
Your not right, I used it very frequently and it had worked :S
But now it doesn't :confused:

---

### Post by kansei on 2007-09-10
> **threethirty said:**
> k3b is a burning app, not a ripping app.  I hate to tell you but I don't know what the KDE ripping app is.  I use GNOME for most things, but I use K3b all the time.

Hate to dig up an old post but this went unresolved so I figured I'd try and help where I can.

K3b *is* able to rip music. To rip to FLAC, you need the packages 'flac', 'libflac++6', and probably 'libflac8' as well.

As for the original issue, it is quite interesting that it does work fine when running it with 'sudo'.

Can you run k3b from a command prompt and see if it gives any other useful output when it errors out?

---

