---
title: "DVDs not playing in VLC"
date: 2012-09-19
forum: Multimedia Software
---

### Post by Subcomfreak on 2012-09-19
Basically no matter what mount point I try I get this:
 p, li { white-space: pre-wrap; }```
Your input can't be opened:
 VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

```

I tried running it through the terminal:
```
john@11ukkhunbuntu:~$ vlc /dev/sr0
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x9c91908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/3469" WARN  07:53:20.621 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[0xb73040f8] filesystem access error: failed to read (Input/output error)
[0xb73040f8] filesystem access error: failed to read (Input/output error)
[0xb73040f8] filesystem access error: failed to read (Input/output error)
[0xb73040f8] filesystem access error: failed to read (Input/output error)
[0xb73040f8] filesystem access error: failed to read (Input/output error)

```

I have tried multiple DVDs and none seem to work. As you can probably see by the output I have all of the needed packages installed? Am I missing something obvious?

---

### Post by Subcomfreak on 2012-09-19
I tried several different DVDs with no luck. I also tried "Mplayer" and it doesn't work either.

---

### Post by Subcomfreak on 2012-09-19
interesting development. I tried to access the dvd via terminal and got this:
```

john@11ukkhunbuntu:/media/FIREFLY_D2$ ls
VIDEO_TS
john@11ukkhunbuntu:/media/FIREFLY_D2$ cd VIDEO_TS
john@11ukkhunbuntu:/media/FIREFLY_D2/VIDEO_TS$ ls
ls: reading directory .: Input/output error
john@11ukkhunbuntu:/media/FIREFLY_D2/VIDEO_TS$ ls -a
ls: reading directory .: Input/output error
.
john@11ukkhunbuntu:/media/FIREFLY_D2/VIDEO_TS$ man ls
john@11ukkhunbuntu:/media/FIREFLY_D2/VIDEO_TS$ 

```

Is this normal?

---

### Post by Subcomfreak on 2012-09-20
Weirdest thing happened this morning. I decided to boot to windows to check if my DVD drive was working. It loaded the DVD fine. I booted back to windows. And guess what? Linux also loaded the DVD fine. This leaves me with a lot of questions...

---

### Post by afulldeck on 2012-09-20
> **Subcomfreak said:**
> Weirdest thing happened this morning. I decided to boot to windows to check if my DVD drive was working. It loaded the DVD fine. I booted back to windows. And guess what? Linux also loaded the DVD fine. This leaves me with a lot of questions...

Is this a new machine? Where the driver wasn't loaded?

---

