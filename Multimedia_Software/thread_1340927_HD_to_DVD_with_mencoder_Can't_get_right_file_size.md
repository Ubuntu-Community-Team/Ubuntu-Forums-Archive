---
title: "HD to DVD with mencoder: Can't get right file size"
date: 2009-11-29
forum: Multimedia Software
---

### Post by pssturges on 2009-11-29
Hi,

I have some 1080i DVB-t recordings that I'm trying to back up to DVD. I have calculated a bit rate to give a resulting file size that neatly fits on a DVD5 disc. I'm trying to use mencoder to produce a dvd compliant mpeg file of the correct size.

Using the claculator [here]("http://www.videohelp.com/calc.htm") my 91 minute video with 448kbps audio should be encoded at a bit rate of 6225 in order to fit snugly on a dvd5. So I use the following mencoder command:
```

mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=6225:keyint=15:vstrict=0:aspect=16/9 -ofps 25 -o <output file> <input file>

```

With this however, I get a file size of 3.1gb. Way smaller than what it should be.

I've seen other people having a similar problem when using a lower quality source video, but as my source is HD I don't this is the same issue.

Any ideas how I can make mencoder encode at the correct rate?

Cheers
Phil

---

### Post by pssturges on 2009-12-02
bump!

---

### Post by VertexPusher on 2009-12-02
Try 2-pass mode.

---

