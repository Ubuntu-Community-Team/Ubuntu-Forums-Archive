---
title: "Encode video for xbox with 5.1 audio"
date: 2009-10-20
forum: Multimedia Software
---

### Post by Keith Hedger on 2009-10-20
Hi every one I hope someone can help.
I want to encode some ripped dvd's to play on my xbox360 but I want to keep the 5.1 surround sound, I can easily create a wmv or mp4 file that plays ok, but the audio is encoded as stereo ( I'm using ffmpeg ), I just can't figure out how to encode the 5.1 surround sound, I've tried variuous things and nothing seems to works, any ideas?

---

### Post by SuperSonic4 on 2009-10-20
Would adding in the following line work
```
-ac 5
```

If it was originally encoded in 5.1 couldn't you use ```
-acodec copy
```

---

### Post by Keith Hedger on 2009-10-20
Tried both of these ways and no joy, I'm using vob files from a dvd ripper that are encoded with 5.1.
any one else?

---

### Post by rockstarrem on 2009-10-21
> **apple232 said:**
> <snip spam>

Not only is this spam, but it's a Window's app :P.

---

### Post by azmo35 on 2009-10-21
Hi,try HandBrak.

---

### Post by Henrikx on 2009-10-21
Take a look...

[h264enc]("http://h264enc.sourceforge.net/")

[Requirement]("http://h264enc.sourceforge.net/links.html")

---

### Post by Keith Hedger on 2009-10-23
Tried h264enc, horrendous to use! the script falls over when it doesn't like an input and you have to start again, then mencoder fell over ( never had much luck with mencoder, I prefer ffmpeg ).
Handbrake ([http://handbrake.fr](http://handbrake.fr)) works fine, thanks azmo35, it even has a xbox preset , but needs tweeking for 5.1, now any one know how to do it in ffmpeg? ( As I like to script these things ).

---

