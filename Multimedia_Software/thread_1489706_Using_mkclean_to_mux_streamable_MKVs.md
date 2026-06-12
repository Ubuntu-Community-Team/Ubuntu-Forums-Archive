---
title: "Using mkclean to mux streamable MKVs"
date: 2010-05-21
forum: Multimedia Software
---

### Post by grock215 on 2010-05-21
**Here is my backstory:**

I have a server running in my basement with 4 TBs of videos.  These videos are all H264 in MKV containers.  I currently use XBMC to play these videos on my LCD upstairs using a Atom/ION box.

This week, WebM was announced which uses an MKV container.  This got me thinking:  I wonder if I could setup my ATOM/ION box to use Chromium instead of XBMC to manage and play my video library.

So i spend the day messing around with Handbrake settings, trying to find the right combination of options that would produce an MKV that would play on Chromium's nightly build.... no luck.  The only way I could make it work was by using an MP4 container.

**My actual question**
When searching about streaming the MKV container, i came across this site: [http://diveintohtml5.org/video.html](http://diveintohtml5.org/video.html)

The author claims that you can use matroska's "mkclean" tool to remux MKV files for streaming.

Awesome!  However, I have not had any luck building the source.

Has anyone successful built this under Lucid?

---

### Post by fguillen on 2010-07-09
Same situation here :/

I have downloaded src from: 

[http://dl.matroska.org/downloads/mkclean/](http://dl.matroska.org/downloads/mkclean/)

Version 0.4.1

And then: 

$ tar -xjf mkclean-0.4.1.tar.bz2 
$ cd mkclean-0.4.1
$ ./bootstrap.sh
$ make -C mkclean

And I have an error: 

[...]
linking ../release/gcc_linux/mkclean
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../libpthread.so when searching for -lpthread
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../libpthread.a when searching for -lpthread
/usr/bin/ld: skipping incompatible /usr/lib/libpthread.so when searching for -lpthread
/usr/bin/ld: skipping incompatible /usr/lib/libpthread.a when searching for -lpthread
/usr/bin/ld: cannot find -lpthread
collect2: ld returned 1 exit status
make[1]: *** [../release/gcc_linux/mkclean] Error 1
make[1]: Leaving directory `/tmp/mkclean-0.4.1/mkclean'
make: *** [mkclean] Error 2
make: Leaving directory `/tmp/mkclean-0.4.1/mkclean'


Any suggestion is welcome.. thanks

f.

---

### Post by fguillen on 2010-07-10
I have obtained to compile mkclean installing the following packages:

(This is a 64bit)

```
$ sudo apt-get install ia32-libs
$ sudo apt-get install gcc-multilib g++-multilib libxxf86vm-dev libglu1-mesa-dev libxft-dev
```

(from: [http://blitzmax.com/Community/posts.php?topic=84385](http://blitzmax.com/Community/posts.php?topic=84385))

---

