---
title: "how to play dvd movie"
date: 2009-09-19
forum: Multimedia Software
---

### Post by Diagom on 2009-09-19
how can i play non original dvd movie in linux mint
and i have install gom player with wine and everithing work fine but a cant play movie
when i play it is just blank screen time is counting but there is not sound and picture

---

### Post by Oceanic on 2009-09-20
First check whether you have the right codec (es) 
installed.

```
sudo aptitude install non-free-codecs libdvdcss2
```

this command will install codecs (coding / decoding) that are proprietary and which you need to watch certain DVD etc

---

