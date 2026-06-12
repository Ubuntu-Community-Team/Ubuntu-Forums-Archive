---
title: "looking for a good mp3 player/converter: wma-mp3"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by abh83 on 2006-12-10
Anyone know of a good mp3 player with converting capabilities to convert wma into mp3??

thx
ABH

---

### Post by pay on 2006-12-10
You can use mencoder ```
sudo aptitude install mencoder
```with the command```
mencoder /path/to/music.wma -oac mp3lame -o filename.mp3
```

---

