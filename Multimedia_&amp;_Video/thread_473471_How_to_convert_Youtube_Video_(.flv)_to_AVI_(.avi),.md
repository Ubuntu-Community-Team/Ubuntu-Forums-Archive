---
title: "How to convert Youtube Video (.flv) to AVI (.avi),WMV,DV,MP4,MOV,3GP or MPEG (.mpg)"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by loell on 2007-06-14
:p but ummm, its a windows shareware, 

[http://vixy.net]("http://vixy.net") for easy conversions

---

### Post by Gwasanaethau on 2007-06-14
The latest Totem Movie Player in Feisty plays FLV files well (in sync and everything), and I've found ffmpeg to be a really easy way of converting FLV files to AVI for the other media players…

---

### Post by jjf on 2007-06-19
I use ffmpeg.

At command prompt (in directory where my FLV sits):

```
 ffmpeg -i original_file.flv new_file.mpg
```

ffmpeg defaults to 320x240.  If you want a higher resolution, use the -s tag:

```
 ffmpeg -i original_file.flv -s 640x480 new_file.mpg
```

man ffmpeg for tons of other options.

---

### Post by blueb73 on 2007-07-11
> **Gwasanaethau said:**
> The latest Totem Movie Player in Feisty plays FLV files well (in sync and everything), and I've found ffmpeg to be a really easy way of converting FLV files to AVI for the other media players…

cant fast forward with it though  :(

---

### Post by blueb73 on 2007-07-11
although, it seems the arrow keys work

better than nothing...

---

### Post by chek2fire on 2007-07-12
take a look to this programme
[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

---

### Post by helloimalemur on 2007-11-24
i just use [www.media-convert.com]("www.media-convert.com") it'll convert anything :D

---

### Post by stooshbunutu on 2008-03-11
try winff ([http://www.biggmatt.com/winff](http://www.biggmatt.com/winff)) as a GUI for ffmpeg (sudo apt-get install ffmpeg)

---

