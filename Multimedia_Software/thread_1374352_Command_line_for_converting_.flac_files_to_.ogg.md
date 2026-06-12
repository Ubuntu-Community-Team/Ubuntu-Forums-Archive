---
title: "Command line for converting .flac files to .ogg"
date: 2010-01-06
forum: Multimedia Software
---

### Post by cprofitt on 2010-01-06
I am looking for a command line command to convert ~2500 .flac files to .ogg files.

All of the .flac files are in one folder and I would like to have the .ogg files put in a folder labled OGG - I would like to retain song information etc if possible.

Thanks.

---

### Post by garryknight on 2010-01-06
I would try ffmpeg for this. It's pretty good at working out which codecs to use by inspecting the filename extensions.
```

ffmpeg -i musicfile.flac musicfile.ogg

```might work and is worth trying before delving further into ffmeg's manual page.

---

### Post by manosx on 2010-01-06
This way seems nice and fast:

```
find . -name "*flac" -exec oggenc -q 7 {} \;
```

check the details in the last post here:
[[http://old.nabble.com/Tag-preserving-Flac-to-ogg-mp3-converter-td16382110.html]](http://old.nabble.com/Tag-preserving-Flac-to-ogg-mp3-converter-td16382110.html])


And a graphical program:
[http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

---

### Post by size_XXM on 2010-10-14
Have a look at [dir2ogg](http://packages.ubuntu.com/search?keywords=dir2ogg&searchon=names&suite=all&section=all). Preserves tags! :)

---

