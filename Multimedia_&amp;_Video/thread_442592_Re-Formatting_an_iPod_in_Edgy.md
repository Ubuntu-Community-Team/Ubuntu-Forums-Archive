---
title: "Re-Formatting an iPod in Edgy"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by vozzon on 2007-05-13
So my brother gave me his old iPod and I want to re-format it to FAT32 and just start over. How could I do that in Edgy?

---

### Post by joe.turion64x2 on 2007-05-13
Have you tried Gparted? (Gnome Partition Editor) Try it when you plug your device.

---

### Post by tgoose on 2007-05-13
If you don't have gparted install that 

```

sudo aptitude install gparted

```

You should be able to use that to format the iPod. Do bear in mind that, unless you use Apple's official updater (Windows and OS X only), I don't think you'll be able to install the default iPod firmware. Rockbox should work fine though.

---

### Post by joe.turion64x2 on 2007-05-13
> **tgoose said:**
> If you don't have gparted install that 

```

sudo aptitude install gparted

```

You should be able to use that to format the iPod. Do bear in mind that, unless you use Apple's official updater (Windows and OS X only), I don't think you'll be able to install the default iPod firmware. Rockbox should work fine though.
You guys who own an Ipod, is it possible to play OGG files in it? Perhaps after formatting it or with new firmware?

---

### Post by vozzon on 2007-05-13
Hm so if I re-format it, I won't have the firmware? Is it possible to restart it to factory settings to keep the firmware and keep it FAT32?

---

### Post by aysiu on 2007-05-13
I don't think you can install Windows iPod firmware from Ubuntu.

You'll need Windows to do that.

Alternatively, you could try Rockbox:
[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by vozzon on 2007-05-13
> **aysiu said:**
> I don't think you can install Windows iPod firmware from Ubuntu.

You'll need Windows to do that.

Alternatively, you could try Rockbox:
[http://www.rockbox.org/](http://www.rockbox.org/)

Doesn't work because it's a 2nd gen nano :\

So now I have to try to figure this out. So  I'll read the iPod in gtkpod and it says: ```
Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.

```

Then I remove all tracks from the iPod, add my music, then I hit sync and it says: ```
 Some tracks could not be deleted from the iPod. Export aborted
``` and if I hit it again it says stuff like: ```
Error opening '/media/ipod/iPod_Control/Music/F02/gtkpod754151.mp3' for writing (Read-only file system).

```

and I tried to chmod +w /media/ipod but it doesn't work. What do I do?

---

### Post by vozzon on 2007-05-15
I need to bump this because I still have this problem.

---

