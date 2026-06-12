---
title: "Kaffeine codecs"
date: 2010-06-25
forum: Multimedia Software
---

### Post by uj2n on 2010-06-25
Hello!

I just installed kaffeine using "apt-get install". I have been using kaffeine for several years, but it seems that on this installation kaffeine installed without codecs! When trying to play a movie using kaffeine, nothing happens. It is a well-known problem that kaffeine does not give error messages when the codecs don't work (just google the problem :) 

Anyhow, since kaffeine does not tell what codec it is missing I do not know how to solve this problem. What are the names of the kaffeine codecs?

Thanks in advance!

---

### Post by mc4man on 2010-06-25
Don't have kaffeine but I'd make sure this is installed
```
sudo apt-get install libxine1-ffmpeg
```

(if movie is a commercial dvd then also libdvdcss2

---

### Post by uj2n on 2010-06-26
awesome! thanks

---

