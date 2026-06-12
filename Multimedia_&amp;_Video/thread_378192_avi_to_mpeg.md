---
title: "avi to mpeg"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by Sniper99 on 2007-03-07
can anybody give me the install for a avi to mpg or wmv please, i cant find one.....any help is greatly appreciated

---

### Post by pay on 2007-03-07
Why do you want to convert avi to mpeg (or especially wmv), mpeg is lower quality than most avi's and it has similar licensing. It doesn't matter what method you use you will lose quality when converting anything to anything (audio or video).Anyway with mencoder you need```
mencoder infile.avi -o outfile.mpg -ovc lavc -lavcopts vcodec=mpeg1video -oac lavc -lavcopts acodec=mp2
```

---

### Post by RomeReactor on 2007-03-07
Hi. To convert .avi to .mpeg with a graphical interface, i suggest you [install]("http://en.wikipedia.org/wiki/Avidemux") [AviDemux]("http://avidemux.sourceforge.net/"); you'll find it in Synaptic, but you'll need **multiverse** repositories enabled for that, so open Synaptic (System-->Administration-->Synaptic Package Manager) and click on "Settings-->Repositories", and on the first tab check all the boxes; press the orange **Close** button on that window, and then press the blue **Reload** button to bring Synaptic up-to-date with the repositories; then search for **avidemux** there, or to install it from the terminal:

```
sudo apt-get install avidemux
```

---

### Post by Sniper99 on 2007-03-09
i need to convert the video so i can rip it onto my zen vision...because it wont do avi files...thank you all, much appreciated

---

### Post by pay on 2007-03-10
My zen vision M does most avi's. It depends on what codec was used to compress the  movie in the first place. I use xvid with mp3 and it works fine, but lavc doesn't work unless if I change the fourcc to xvid.

---

### Post by Sniper99 on 2007-03-11
i dont understand what you are saying with the avi to zen vision m......becuase every time i try to convert a file to the transferabble format, its says it is not a valid file type,  so i am totally stumped.......

---

### Post by pay on 2007-03-12
> **Sniper99 said:**
> i dont understand what you are saying with the avi to zen vision m......becuase every time i try to convert a file to the transferabble format, its says it is not a valid file type,  so i am totally stumped.......
Play the file with mplayer ```
mplayer file.avi
```and it will tell you what codec it is using and then check to see if that codec is supported by your player.

---

