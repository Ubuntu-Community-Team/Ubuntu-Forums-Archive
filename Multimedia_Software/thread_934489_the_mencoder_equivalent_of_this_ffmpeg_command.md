---
title: "the mencoder equivalent of this ffmpeg command?"
date: 2008-09-30
forum: Multimedia Software
---

### Post by zach014 on 2008-09-30
ffmpeg -i <input> -acodec aac  -ac 2  -vcodec mpeg4 -s qcif -b 128kb -r 14.985 <output>

---

### Post by zach014 on 2008-10-02
bump

---

### Post by zach014 on 2008-10-10
bump

---

### Post by cor2y on 2008-10-11
If you insist.
```

mencoder <filename.avi> -ovc lavc -lavcopts vcodec=mpeg4 -oac faac -faacopts br=128:mpeg=4:object=2 -channels 2 -srate 48000 -o <output.avi>
```
That should work but keep in mind that you need libfaac-dev installed and compiled with mencoder for this to work.
If you wish to output to another container example like mp4 or mkv you will need gpac , mp4tools and mkvtools installed then demux the streams and put them back together using the tools.

---

