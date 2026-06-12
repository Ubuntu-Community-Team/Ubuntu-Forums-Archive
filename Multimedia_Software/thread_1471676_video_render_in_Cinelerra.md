---
title: "video render in Cinelerra"
date: 2010-05-03
forum: Multimedia Software
---

### Post by tubunu on 2010-05-03
Hello,

I'd like some advice on how I can output my edited film so that I can burn it on DVD with Devede. The problem is that my film is 2 hours long and which ever format I choose to render it, the resulting file size is HUGE. (i.e. 1 minute of .avi = 1.2GB! or around 500MB when I output to .dv)

What file format would be best to render to?

I currently have only around 13GB free disk space and I'm afraid it won't be enough for a 2 hour film. And then I'm not sure if Devede would accept such a big file anyway. Please advise. Thank you.

---

### Post by tubunu on 2010-05-04
Anybody, please?

---

### Post by tubunu on 2010-05-05
bump...

---

### Post by tubunu on 2010-05-06
bumpety! :D

---

### Post by tubunu on 2010-05-06
bump

---

### Post by monraaf on 2010-05-06
I was about to answer your question until I saw all these *bumps*. I hate that. And I don't think that behavior should be rewarded. ):P

---

### Post by tubunu on 2010-05-07
> **monraaf said:**
> I was about to answer your question until I saw all these *bumps*. I hate that. And I don't think that behavior should be rewarded. ):P

Well, thanks, that's SO comforting... Do you know of a better way to get a question answered? It's not like I was bumping the question every 5 minutes. Look at the first post date. Once the thread becomes buried in the avalanche of other posts, the chances of getting it answered become very low, but the problem still remains. And I do think it's OK to bring it up when it gets buried in there. So, now, when I start a new thread (if this one doesn't get any more *meaningful* replies), you'll criticize me again, huh? How cool is that...

---

### Post by wildhostile on 2010-05-18
Hi tubunu,

I don't really know the workflow to create dvd but.... maybe you should not use .dv codec to export your video.
Cinelerra-CV (Community Version) gives you two solutions:
- File -> Render -> MPEG-Video. Choose the colour model and the codec in the dialogue box.
- File -> Render -> YUV4MPEG Stream. That's the best choice. Make tests using the pipe presets.
For both of these solutions you will have to render audio and video parts separately to mux them later with your dvd program. 
As I never used this output format myself, I suggest you to make searches to find the best workflow to make your dvd.
see:
[http://cinelerra.org/docs.php](http://cinelerra.org/docs.php)
[http://womble.decadent.org.uk/talks/dvd-ukuug06/dvd-talk-ukuug06-paper.html](http://womble.decadent.org.uk/talks/dvd-ukuug06/dvd-talk-ukuug06-paper.html)
or the cinelerra mailing list ==> [http://cinelerra.org/mailinglists.php](http://cinelerra.org/mailinglists.php)

---

### Post by linuxford on 2010-05-21
Not sure as I am pretty new, but here is what I do.
1) import multiple mpegs into Kino tool
2) export from Kino (File format: 8-DVD)
3) ./makexml -dvd -chapters 5 tvnews.mpeg -out tvnews 
4) ./makedvd "tvnews.xml"
5) dvdauthor -x "/home/username/Videos/tvnews.xml"
6) gxine "dvd://home/username/Videos/tvnews" 
7) ./makedvd -burn "tvnews"

---

### Post by tubunu on 2010-05-22
Thanks, wildhostile and linuxford! I'll try doing that.

---

