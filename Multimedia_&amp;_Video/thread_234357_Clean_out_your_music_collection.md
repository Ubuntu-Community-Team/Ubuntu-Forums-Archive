---
title: "Clean out your music collection"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by craig552 on 2006-08-11
If you've just moved all your music collection over to linux, you may notice a few files such as desktop.ini and Thummbs.db

This command will list all non-music files in your collection
[FONT="Courier New"]
Find . -type f | grep -vi mp3 |grep -vi m4a |grep -vi wma[/FONT]

---

