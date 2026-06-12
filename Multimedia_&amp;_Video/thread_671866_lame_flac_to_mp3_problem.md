---
title: "lame flac to mp3 problem"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by DocForbin on 2008-01-19
Somehow I hosed lame. Encoding to mp3 (or any other format) results in a file with nothing but static. I've reinstall lame and flac. Not sure where to look next.

btw, does anyone know a nice command line tool for flac to mp3 that carries the tags over? I've seen some bash and perl scripts that use metaflac to extract the tags, but something like lame that just worked would be ideal.

---

### Post by DocForbin on 2008-01-19
bumpski

---

### Post by disturbed1 on 2008-01-19
To carry the FLAC tags over to mp3, use SoundConverter (gui not cli).

Lame can not decode flac files. They need to be decompressed first.

---

### Post by DocForbin on 2008-01-19
> **disturbed1 said:**
> To carry the FLAC tags over to mp3, use SoundConverter (gui not cli).
I have soundconverter, but require a cli.

> Lame can not decode flac files. They need to be decompressed first.
doh, thanks

---

