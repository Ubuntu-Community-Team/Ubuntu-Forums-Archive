---
title: "Opening huge wave files"
date: 2011-06-24
forum: Multimedia Software
---

### Post by yun.a.k on 2011-06-24
I have a wav file bigger than 8GB. i recorded it on a windows PC. unfortunately wav files cant be bigger than 2GB. somehow i got a file that is almost 9GB. I tried to chop the file under ubuntu into smaller pieces to open it part by part. i used gnome split to divide the file and made 10 parts out of it. 
now i have these parts of the data which i cant read with no program except for gnome split to merge them together again - which would only bring me to the beginning of my problem.
so my question is: is there any other way to open/ split&open a wav file of that size or maybe a way to open the splitted file partially?

---

### Post by Elfy on 2011-06-24
Thread moved to Multimedia & Video.

---

### Post by Jahid65 on 2011-06-24
you can use[ lxspli]("http://babeyudi.wordpress.com/2010/09/07/how-split-and-join-file-with-lxsplit-in-ubuntu/")t, which is compatible with Hjsplit. But it's a CLI app. you can use ffmpeg to split your wav file.

```
ffmpeg -i your_wav_file.wav -ss 00:00:00 -t 00:02:02  -acodec copy newtest.wav
```

Here -ss means starting time
-tt means duration

---

### Post by tgalati4 on 2011-06-24
Let sox mangle it:

sudo apt-get install sox
man sox

---

