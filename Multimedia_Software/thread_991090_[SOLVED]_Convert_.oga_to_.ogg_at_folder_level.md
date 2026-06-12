---
title: "[SOLVED] Convert .oga to .ogg at folder level"
date: 2008-11-23
forum: Multimedia Software
---

### Post by brandoncolorado on 2008-11-23
Hello,

My new MP3 player works great with Linux.  However, I ripped my CD collection using Audio CD Extractor, and the default was the rip the files to .oga format.  I searched and read that this is the new standard for ogg audio files, but my Sansa Clip MP3 players only recognizes .ogg files (.oga doesn't even show up).

Can you think of a way for me to convert a whole folder full of music from .oga to .ogg?  What about if I wanted to convert the whole folder (which includes mp3 too) to ogg?

Thank you

---

### Post by brandoncolorado on 2008-11-23
For anyone that needs the answer to this:

1)  Install soundconverter (add/remove programs)
2)  Set output as .ogg
3)  Select whole folder, and make sure mp3 codec is installed
4)  ?????????
5)  Profit!

---

### Post by FakeOutdoorsman on 2008-11-23
Did you try just renaming the files instead of reconverting them?  I would guess the Vorbis audio stream would be the same between OGG and OGA.

---

### Post by brandoncolorado on 2008-11-23
> **FakeOutdoorsman said:**
> Did you try just renaming the files instead of reconverting them?  I would guess the Vorbis audio stream would be the same between OGG and OGA.

That does work, but I wanted to avoid that because there were about 600 files.  I suppose I could have found a script for that, but I am a bit too inept to attempt that.

---

### Post by FakeOutdoorsman on 2008-11-23
Try this in a terminal, it's not folder recursive, but do it in a test folder first:
```
for i in *.oga; do mv "$i" "${i%.oga}.ogg"; done
```

---

### Post by rumli on 2009-01-02
The following will recursively convert all the files in a given directory from .oga to .ogg.
```

find [directory] -regextype posix-extended -regex '(.*/)([^/]*\.ogg$)' -execdir bash -c 'mv $0 $(echo $0 | sed -e"s@\.ogg\$@.oga@g")' '{}' \;

```
I should point out that it's probably better to do the opposite (i.e., rename .ogg to .oga), since that's the recommended extension for Ogg/Vorbis files.  To do so, simply swap all instances of "ogg" and "oga" in the above command.

---

### Post by puppe on 2009-11-07
well you can always use pyrenamer

---

