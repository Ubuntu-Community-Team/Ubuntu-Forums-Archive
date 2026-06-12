---
title: "HOW TO: GFX Benchmarking (Unigine)"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by Jest3r on 2007-11-26
I was having trouble finding some benchmarking tools for ubuntu for my system.  
I stumbled apon the following engine, Unigine v4.

_[**Unigine sample video [ [B]You** [COLOR="Red"]Tube[/COLOR]][/B]]("http://www.youtube.com/watch?v=cPPxMvUF3jA")_

The benchmarking tool can be downloaded for free from there site, and it runs native on thier website, [_http://unigine.com/_]("http://unigine.com/")

#_ [Sanctuary demo [26 Mb]]("http://unigine.com/download/files/Unigine_v0.4_Sanctuary.zip")_
# _[Linux binaries [3 Mb] ]("http://unigine.com/download/files/Unigine_v0.4_Sanctuary_Linux.zip")_

**Download and install 29MB**
```

$ cd /tmp
$ mkdir unigine
$ cd unigine
$ wget http://unigine.com/download/files/Unigine_v0.4_Sanctuary.zip
$ wget http://unigine.com/download/files/Unigine_v0.4_Sanctuary_Linux.zip
$ unzip Unigine_v0.4_Sanctuary.zip
$ unzip Unigine_v0.4_Sanctuary_Linux.zip
$ cd Unigine_v0.4_Sanctuary_Linux
$ cp -rp * ../Unigine_v0.4_Sanctuary
$ chmod +x sanctuary_opengl_*

```

**Run in window mode**
```

./sanctuary_opengl_windowed_1024x768.sh

```

**Run in fullscreen mode**
```

./sanctuary_opengl_fullscreen_1024x768.sh

```

The test will run for about 5 mins, then give you a score at the end. Great for stress testing as well, as it will run in a loop. I use nvclock to check my GPU temps and sensors for check my CPU.

---

### Post by K.Mandla on 2007-11-27
Moved to Multimedia and Video.

---

