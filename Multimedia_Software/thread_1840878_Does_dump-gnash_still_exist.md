---
title: "Does dump-gnash still exist?"
date: 2011-09-08
forum: Multimedia Software
---

### Post by dschaller on 2011-09-08
I'm trying to convert an swf movie to a different video format. I've heard that a utility called dump-gnash can play swf to raw video output, but when I compile gnash with the dump option enabled, it seems like the dump-gnash executable is never created. Compiling Gnash 0.8.9 I used:

```
./configure --prefix=/usr/local --enable-gui=gtk,dump

```

But dump-gnash is nowhere to be found after building and installing. How do I compile and/or use the elusive dump-gnash utility?

---

### Post by .... on 2011-09-08
Just use ffmpeg.
```
ffmpeg -i flashvideo.swf <options> outputfile.<whatever format you want>
```

---

### Post by dschaller on 2011-09-08
Actually, you can't use ffmpeg or any other usual video conversion tool (like mencoder) because SWF is not a video format like FLV. Rather it stores ActionScript which is interpreted and displayed by the Flash player. I'm guessing that some combination of playback and screen capture is probably the only way to convert it to a video format if dump-gnash won't work.

---

### Post by StephenWoods69 on 2011-09-08
I found this page which may be useful [http://wiki.resourcespace.org/index.php/SWF_Support](http://wiki.resourcespace.org/index.php/SWF_Support)

---

### Post by .... on 2011-09-08
Sorry, I was thinking of FLV.

---

### Post by dniMretsaM on 2011-09-08
I found something about compiling dump-gnash [here](http://askubuntu.com/questions/16867/missing-thumbnails-for-swf-files-in-nautilus). I don't know if it's what you're looking for though.

---

### Post by dschaller on 2011-09-09
Thanks for the replies. I still have not figured this out yet. I did discover a directory for the dump source code buried in the tarball I downloaded and I found a README on the gnash stream dumper, but the instruction seemed quite out of date. Several of the configure switches in the example were not recognized and once again, when I followed the instructions the dump-gnash executable was not built and is nowhere to be found.

If anyone has actually managed to build dump-gnash recently, I'd sure be interested in how it's done. I must be doing something wrong.

---

### Post by dniMretsaM on 2011-09-09
Might this be what you need?

```
+Gnash stream dumper
+===================
+
+This is an experimental build of gnash that allows the user to dump
+both the raw (BGRA24) video stream, and the raw (PCM/Wave) audio
+stream from a movie.  The "dump gui" is disabled by default, you'd
+need to compile it with something like this:
+
+./configure \
+     --prefix=/usr/local/gnash-dump \
+     --enable-renderer=agg \
+     --enable-gui=gtk,dump \
+     --enable-media=ffmpeg \
+     --disable-kparts \
+     --disable-nsapi \
+     --disable-menus
+
+It *requires* AGG as the renderer and *ffmpeg* as the sound driver.
+Although audio and video are separate (you can dump video, even if you
+choose gstreamer for audio output).
```Copied from [http://lists.gnu.org/archive/html/gnash-commit/2008-05/msg00489.html](http://lists.gnu.org/archive/html/gnash-commit/2008-05/msg00489.html)

---

### Post by dschaller on 2011-09-09
Yes, I think that's the critical readme file on the gnash stream dumper. When I use those configure options, gnash will compile for me, but the dump-gnash executable is still nowhere to be found when it's done and installed. It doesn't show up in /usr/local/gnash-dump/bin the way the instructions say that it will. Maybe I don't have a certain necessary development file installed? (But it does finish compiling. It doesn't quit with errors.)

---

### Post by dniMretsaM on 2011-09-09
> **dschaller said:**
> Yes, I think that's the critical readme file on the gnash stream dumper. When I use those configure options, gnash will compile for me, but the dump-gnash executable is still nowhere to be found when it's done and installed. It doesn't show up in /usr/local/gnash-dump/bin the way the instructions say that it will. Maybe I don't have a certain necessary development file installed? (But it does finish compiling. It doesn't quit with errors.)

Depending on the missing dependency (if that is actually the problem), it may not quit. It may just finish because it's not necessary for it to run (it could be a bug). I really don't know, and after a lot of Googling, nothing comes up. I know it's still available because in the release announcements for 0.8.9 is mentions dump-gnash improvements. I hope you figure it out eventually!

---

### Post by HeatherZ on 2011-09-19
I am running Ubuntu 11.04,  natty.  The following shows the options I used when trying to compile dump-gnash with gnash-0.8.9

./configure --prefix=/usr/local/gnash-dump --enable-renderer=agg --enable-gui=gtk,dump --enable-media=ffmpeg --disable-kparts --disable-nsapi --disable-menus

I can't seem to get pass the errors from jemalloc.c:

  CC     libgnashbase_la-jemalloc.lo
jemalloc.c:556:35: error: âPTHREAD_ADAPTIVE_MUTEX_INITIALIZER_NPâ undeclared here (not in a function)
....

jemalloc.c: In function âmalloc_spin_initâ:
jemalloc.c:1297:35: error: âPTHREAD_MUTEX_ADAPTIVE_NPâ undeclared (first use in this function)

Anyone know how to resolve this?

---

### Post by dschaller on 2012-05-18
Just as a follow-up to this old thread... I did eventually get dump-gnash to compile. I asked an expert friend of mine to look over the configure and make scripts. He did and said they were a real mess. He fixed them so that dump-gnash would build on Ubuntu. It runs now, but I have not yet been successful in getting it to translate the swf files that I wanted. So converting flash is still a work in progress for me.

---

