---
title: "Change lame bitrate in k3b?"
date: 2009-12-21
forum: Multimedia Software
---

### Post by keenPenguin on 2009-12-21
Hi, 

I am using Ubuntu 9.10. From the repos, I installed k3b, lame and libmp3lame0. I test-ripped an audio CD track successfully, but the standard bitrate seems to be 128kb. 

After installing lame, it was offered in the "Editing external audio encoder" dialog in k3b. The line by which lame is called is

```
lame -r --bitwidth 16 --little-endian -s 44.1 -h --tt %t --ta %a --tl %m --ty %y --tc %c - %f
```

Can you tell me how I can change the bitrate, e.g. set it to 192kb?

Another question: I am no expert in ripping and bitrates, but I've read that variable bitrates deliver the best results. I don't know if it's true. Anyway, which configuration would you suggest is the best if I want a quality of about 192kb? (possibly a constant one, or possibly variable - I don't know).

Thanks in advance!

---

### Post by keenPenguin on 2009-12-22
Maybe, somebody has an idea?

---

### Post by anonSam on 2009-12-22
[http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/switchs.html](http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/switchs.html)

I may be wrong but to create a CBR at 192kbps it would be --cbr 192

For the highest quality mp3s I would always recommend a cbr of 320kbps.

---

### Post by keenPenguin on 2009-12-23
I tried

```
lame -r --cbr 192 -s 44.1 -h --tt %t --ta %a --tl %m --ty %y --tc %c - %f
```

but k3b returned an error. The error appears not really to be specified. The order of where I put cbr and its argument do not matter, do they?

---

### Post by anonSam on 2009-12-28
[http://www.mepis.org/node/11843](http://www.mepis.org/node/11843)


It says here:



If you require a set constant bitrate of 224 kbps you could change the -h to -b 224



So I guess try just removing the the -h (and the --cbr 192) and replace it with -b 192



Again, I'm just guessing with the information I can find. Hope this works. I don't know if the order matters or not, I'm learning as I go along too.

---

### Post by Bobbuntu96 on 2012-01-15
Thx anonSam....that was right on the money and worked fine in 11.10....:D

---

### Post by overdrank on 2012-01-15
Back to sleep thread. Thread closed.

---

