---
title: "converting dv to mpg (vcd) and theora by script/sh"
date: 2008-07-31
forum: Multimedia Software
---

### Post by tom_a_sparks on 2008-07-31
I have group of dv file dived into folders by tape number

I am looking for a script/sh that can run these commands on each file inside of each folder


```
ffmpeg -i <filenamehere>.dv -target pal-vcd  <filenamehere>.mpg
```
(skip mpeg if already there, do not convert mpg to theora)
and 
```
ffmpeg2theora --deinterlace -v 5 -a 6 <filenamehere>.dv
```
(skip theora (ogg/ogv) if already there)

---

