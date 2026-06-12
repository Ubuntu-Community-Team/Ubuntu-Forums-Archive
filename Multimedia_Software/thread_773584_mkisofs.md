---
title: "mkisofs"
date: 2008-04-29
forum: Multimedia Software
---

### Post by bmenge on 2008-04-29
Well i have been trying to get an iso file made from a .vob file.  I have done it in the past with no problems but have spent many hours trying to get things working with two different projects.  I have read the man page and searched endlessly on the web.  

I do have the AUDIO_TS and the VIDEO_TS folders in the same location.  The AUDIO_TS is empty but I put it there because everything says to do so.  

```
brian@brian-desktop:~/Desktop/SLIDESHOW$ ls
AUDIO_TS  VIDEO_TS
brian@brian-desktop:~/Desktop/SLIDESHOW$ cd VIDEO_TS/
brian@brian-desktop:~/Desktop/SLIDESHOW/VIDEO_TS$ ls
SLIDESHOW.vob
```

```
brian@brian-desktop:~/Desktop$ mkisofs -dvd-video -o FILM.ISO /brian/Desktop/SlIDESHOW
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - '/brian/Desktop/SlIDESHOW'.

```

here is one of the many post I have read and I get these results [http://ubuntuforums.org/showthread.php?t=126166]("http://ubuntuforums.org/showthread.php?t=126166")

```
brian@brian-desktop:~/Desktop$ mkisofs -dvd-video -udf pumpkin.iso /brian/Desktop/SLIDESHOWI: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - 'pumpkin.iso'.
```

Maybe I am looking over something very obvious but I am at my whits end on this I need some help

---

### Post by bmenge on 2008-04-29
Somebody has got to see my error out there

---

