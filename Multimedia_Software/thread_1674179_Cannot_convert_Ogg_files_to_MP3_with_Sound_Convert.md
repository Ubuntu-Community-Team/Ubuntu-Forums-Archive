---
title: "Cannot convert Ogg files to MP3 with Sound Converter!"
date: 2011-01-23
forum: Multimedia Software
---

### Post by dreamr2011 on 2011-01-23
Hi guys,

I'm rather new to ubuntu and I've had no trouble with it until attempting to add new music to my banshee music library and ipod. I've copied the music into my music folder and tried to convert to MP3 with sound converter but it keeps popping up with the warning "Cannot overwrite source files". I tried to convert the files to MP3 directly from the cd but that didn't work either. Any ideas on how i can get around this problem? Many thanks.

---

### Post by johntaylor1887 on 2011-01-23
Did you install the mp3 codecs?

---

### Post by dreamr2011 on 2011-01-23
Yes but it's still not working :confused:

---

### Post by johntaylor1887 on 2011-01-23
You could try RipperX for converting. It has worked for me.

---

### Post by ron999 on 2011-01-23
> **dreamr2011 said:**
> "Cannot overwrite source files"

That's the clue.
You're trying to convert files into the same format.
ogg files into ogg files.
With Sound Converter go into Edit > Preferences and change format to MP3.

---

### Post by dreamr2011 on 2011-01-23
It doesn't list MP3 as an option...

---

### Post by ron999 on 2011-01-23
> **dreamr2011 said:**
> It doesn't list MP3 as an option...
You need to enable mp3 codec.
Look in the package manager for gstreamer plugins multiverse.

---

