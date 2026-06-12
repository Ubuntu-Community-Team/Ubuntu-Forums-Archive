---
title: "How do I extract a single chapter from a DVD ISO?"
date: 2008-10-24
forum: Multimedia Software
---

### Post by feedmecereal on 2008-10-24
What would be the easiest way to extract a single chapter from a DVD that I have ripped as an ISO to my hard drive? I don't really need to convert it to another format (I may even prefer not to).

I have tried Googling this and all of the programs that I have found are command line only and I can hardly make heads or tails of them.

---

### Post by justsomedude on 2008-10-24
For a GUI application, try dvd::rip (available in the repos).


Other than that, you can use mplayer:

Extract title 1 from a DVD:

```
mplayer dvd://1 -v -dumpstream -dumpfile output.vob
```


Extract title 3, chapter 5:

```
mplayer dvd://3 -chapter 5-5 -v -dumpstream -dumpfile output.vob
```


Extract title 3, chapters 5 to 7

```
mplayer dvd://3 -chapter 5-7 -v -dumpstream -dumpfile output.vob
```

Replace dvd://x with the path to your .iso file, if you want to use that.

---

### Post by jerome1232 on 2008-10-24
k9copy is also very good at this, you open the disc and it'll display all of the chapters, you can select one to rip out and transcode.

---

