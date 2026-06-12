---
title: "Downsample and transfer script"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by MaX on 2007-02-08
Hi

I want to be able to use my K800i to listen to mp3 and to save space I use lame to make all of them 96 or 128 bit.
The command I use looks like this:
```
mpg321 -w - filename.mp3 | lame -b 96 - filenameout.mp3
```
And to transfer it to my phone I do
```
gnome-obex-send filenameout.mp3
```

Now I'd like to have this as an icon on my desktop so that when I drag a file there it'll downsample it and then transfer the file to the unit.
It should use the same name as the original file too (and preferably preserve tags and such).

So does anyone have a clue on how I write this?
:guitar:

---

