---
title: "Kdenlinve"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by ketzerei on 2007-11-30
Okay, I was recommended KDEnlive by several people and I like it. The interface is nice, and its fairly simple to use. HOWEVER, somehow, subclips wont encode the way you save them. What i mean by this is when I razor a clip, then razor where I want it to end and save it, it encodes from a random point in the original clip, and the subclip isnt even in the movie. Help!

---

### Post by ketzerei on 2007-12-01
bump

---

### Post by mgmiller on 2007-12-02
I haven't gotten that far with kdenlive yet.  

I was having a sound issue where I had no sound in any clips within kdenlive, but things I saved did have sound.  Running the program from a terminal showed an error with sdl.  I reported this as a bug on the kdenlive forum and was given the following solution:
```
sudo apt-get install libsdl1.2debian-all
```

This replaced the libsdl1.2debian-oss package that was in my system and the kdenlive sound started working.

Sorry I can't address your problem, but I thought this thread might attract others with various kdenlive problems and at least this is a solution to one of them.

---

