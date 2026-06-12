---
title: "Audio CDs do not work"
date: 2011-08-31
forum: Multimedia Software
---

### Post by medevacs on 2011-08-31
My DVD drive does not play audio CDs. I have all codecs/restricted codecs, normal (with files) CDs and DVDs as well as DVDs with movies work great but after inserting audio CD nothing happens. If i start VLC (or Parole) and choose to play content from disc -> audio CD nothing happens. File manager sees "Audio Disc" in the drive but clicking on it returns "Failed to mount "Audio Disc". Drive /dev/sr0 does not contain audio files.". I am sure it does contain audio files as I tried 3 different legit audio CDs. Does DVD drive have to be declared in /etc/fstab? This file is pretty much empty in my system, there are only lines regarding hard drive partitions. But as I already said, other CDs or DVDs work without any trouble, it is just Audio CDs that don't work. How to fix it?

---

### Post by edwardoclese on 2011-11-20
Same here! Mal-function, exactly as you describe, yet the drive operates perfectly under other OS's.

I am a Panasonic CF-52 running Ubuntu Studio 11.10 Oneiric.

---

### Post by andrew.46 on 2011-11-21
This problem has popped up quite often with not much resolution. Oddly enough many can still play their audio cds with MPlayer:

```

mplayer -cache 2048 cdda://

```

or even:

```

mplayer -cache 2048 -cache-min 80 cddb://

```

Not sure how to resolve the underlying issue though...

---

### Post by edwardoclese on 2011-11-21
I installed [FONT=Courier New]gvfs-backends [FONT=Verdana]and my problems seem to be solved.[/FONT][/FONT]

---

### Post by lekremyelsew on 2011-12-01
> **edwardoclese said:**
> Same here! Mal-function, exactly as you describe, yet the drive operates perfectly under other OS's.

I am a Panasonic CF-52 running Ubuntu Studio 11.10 Oneiric.

That's because the problem is related to Thunar (which isn't there in the other OS's). In the Removable Drives and Media settings window turn off the mount and browse removable media check boxes and that should do the trick.

---

### Post by mikrowelle on 2011-12-13
> **edwardoclese said:**
> I installed [FONT=Courier New]gvfs-backends [FONT=Verdana]and my problems seem to be solved.[/FONT][/FONT]

 Thanks, this worked for me!  Changing the settings for removable drives as suggested in the above post didn't do anything for me.

---

### Post by carreiro on 2011-12-14
Thanks after that I installed [FONT=Courier New]gvfs-backends pack cdrom works very well. 

 [/FONT]

---

