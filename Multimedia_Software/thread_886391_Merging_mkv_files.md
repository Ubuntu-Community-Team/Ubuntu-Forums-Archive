---
title: "Merging mkv files"
date: 2008-08-11
forum: Multimedia Software
---

### Post by superarmy on 2008-08-11
I have a movie split into three mkv files. Is it possible to merge them in terminal and if so what is the command again? (I forgot)

---

### Post by superarmy on 2008-08-11
bump

---

### Post by shirilover on 2008-08-11
Easiest method would be to install mkvtoolnix, then open mmg(MkvMergeGui).
Simply add the first file using the add button then add the others using the append button.

---

### Post by superarmy on 2008-08-11
I got said programme but now I get error when I try and add files. 


```
Error: The demultiplexer for the file '/home/samuel/Desktop/Beyond.The.Clouds.Movie.DVD.
(H264.AC3).[KAA][0E715800]2.mkv' failed to initialize:
ac3_reader: No valid AC3 packet found in the first 4096 bytes.
```
Please help

---

### Post by shirilover on 2008-08-12
I don't think you'll be able to join those files since the interview and trailer use vorbis audio, while the movie uses AC-3 5.1 audio.

You could always just make a playlist to play them back in the order you want.

---

### Post by aleb on 2010-11-07
> **shirilover said:**
> Easiest method would be to install mkvtoolnix, then open mmg(MkvMergeGui).
Simply add the first file using the add button then add the others using the append button.

If you prefer the command line, use mkvmerge:
```
mkvmerge file1.mkv + file2.mkv -o file.mkv
```

---

