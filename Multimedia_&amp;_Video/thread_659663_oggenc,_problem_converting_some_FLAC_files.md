---
title: "oggenc, problem converting some FLAC files"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by DocForbin on 2008-01-05
I hacked together a small python program to parse a rhythmbox playlist, copy all the files to my portable music player, and convert any FLAC files that happen to be on it to Ogg Vorbis. I initially tried using LAME, but it did not carry the tags over. So I installed vorbis tools and am now using oggenc. The problem is oggenc does not like some of my FLAC files, while it handles others just fine. On some FLAC files I get this error:

ERROR: Input file "myfile.flac" is not a supported format

If I use LAME the same file converts without error, but then I have the problem with not preserving the tags.

Any input would be appreciated.

---

### Post by DocForbin on 2008-01-06
Update: I just tried using flac --ogg on the problematic files, and get

ERROR: Input file myfile.flac has an ID3v2 tag

I assume this is the problem for oggenc too. Does anyone know a workaround, or maybe a way to bulk convert these tags. Or if I could get LAME to preserve the tags I could just use it.

---

### Post by DocForbin on 2008-01-06
Well the ID3 tags are definitely the issue. EasyTag  converts them if I force a save, then oggenc works fine.

---

### Post by DocForbin on 2008-01-06
btw, does anyone happen to know what the beep means in EasyTag when you are bulk updating? I am about 80% done batch updating ~3000 FLAC files, and on 5 or 6 of the albums so far EasyTag beeped updating every track. From a look at the modification date the files weren't altered, but no error message.

---

