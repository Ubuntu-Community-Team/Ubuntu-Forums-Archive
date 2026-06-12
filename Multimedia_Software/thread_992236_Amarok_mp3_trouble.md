---
title: "Amarok mp3 trouble"
date: 2008-11-24
forum: Multimedia Software
---

### Post by The Scientist on 2008-11-24
hi,

I'm relatively new to linux, and I've tried many distro's. Currently testing kubuntu intrepid.
I had Amarok playing mp3's, but now, for some strange reason it won't do this anymore.
When I throw a mp3 at it, it asks to install mp3 support (even though it was already installed). If I click "no", it won't play my mp3 file. If I click 'install mp3 support' nothing happens.
What can I do ?

---

### Post by LucaTNT on 2008-12-19
Try deleting the .xine folder in your home:
```
rm -r ~/.xine
```
It worked for me.

---

