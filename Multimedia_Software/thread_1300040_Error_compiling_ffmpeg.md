---
title: "Error compiling ffmpeg"
date: 2009-10-24
forum: Multimedia Software
---

### Post by spizo on 2009-10-24
ok, so I'm a newb and I'm totally stuck.  This is what I've done.
I'm compiling ffmpeg from the source as follows:
1. ./configure --prefix=/home/me/myffmpeg (works fine)
2. make (works fine)
3. make install (I get this error):

nbriz@HAL9000:~/me/src/ffmpeg$ make install
install -d "/home/me/myffmpeg/lib"
install: cannot create directory '/home/me': Permission denied
make: *** [install-libavdevice-static] Error 1

I also tried to do a "sudo make install" to get around the permission issue, but when I do this it appears as though it works but the files don't actually get created.

---

### Post by mc4man on 2009-10-24
Why don't you have a read here (for intrepid and jaunty)
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Maybe start fresh

> ....but when I do this it appears as though it works but the files don't actually get created.

d. check and remove anything that was created in home folder, if at all

---

### Post by vinutux on 2009-10-25
compiling is not recommended for newbies...

Why are you compile ffmpeg there is already debs available in repos...

---

### Post by FakeOutdoorsman on 2009-10-25
> **vinutux said:**
> compiling is not recommended for newbies...
I disagree.  Anyone who can open a terminal and follow good instructions can compile successfully.  It is also a good way to learn a little about the command-line.

> Why are you compile ffmpeg there is already debs available in repos...
There are several reasons to compile FFmpeg.  Depending on your Ubuntu version, the repo FFmpeg may be lacking additions and bugfixes present in the SVN FFmpeg.  An example is the libx264 presets which make encoding to H.264 much easier.  These presets are not available for Hardy and Intrepid without compiling FFmpeg.

---

### Post by andrew.46 on 2009-10-26
Hi vintux,

> **vinutux said:**
> compiling is not recommended for newbies...

While I agree that for somebody totally new to Linux compiling software without guidance is a potential recipe for disaster I would still insist that compiling cutting edge software under the guidance of a more experienced user is ideal even for the most raw Linux recruit. This guidance is offered in several places on these Forums and a shining example is the FFmpeg guide linked by mc4man.

All the best,

Andrew

---

