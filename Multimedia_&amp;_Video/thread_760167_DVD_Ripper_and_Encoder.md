---
title: "DVD Ripper and Encoder"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by sifon187 on 2008-04-19
I am looking for a good dvd ripper and possible encoder to encode to divx. I want to "backup" my movies in the harddrive. Now I did use nero on windows but no more windows lol. I already tried Acidrip, dvd:rip and thoggen. All do alright , but I need the movies to be in a a better quality.

---

### Post by mc4man on 2008-04-19
For most titles (ie. no structure protection) Vobcopy rips well and quick. I'd use ver. 1.02 or 1.1.1 - you could pick up hardy ver. or compile. (only takes a min or so ) A good comm. with those versions would be ```
vobcopy -v -m -F 16 /media/cdrom0
```  - adjust device if necessary.)
for encoding use [http://divxenc.sourceforge.net/](http://divxenc.sourceforge.net/)   - high quality may take some time depending on your hardware
edit:
divxenc may work off of disk
K9copy with no compression (set target size high) is also a good way  - re author with 1 audio stream works well

re edit : if you use divxenc (or the other 2, h264enc, xvidenc ) after installing run ```
divxenc -sc or h264enc -sc  or xvidenc -sc
``` 
Lets you know whats missing, needed for full capabilities

---

