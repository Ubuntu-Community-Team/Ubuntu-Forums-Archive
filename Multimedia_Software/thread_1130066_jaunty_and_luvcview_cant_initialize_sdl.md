---
title: "jaunty and luvcview cant initialize sdl"
date: 2009-04-19
forum: Multimedia Software
---

### Post by iochinome on 2009-04-19
so i am trying to get my hp laptop up and running, i have libwebcam and the works intalled already, and just want to do a quick demo of it for myself. when i fire up luvcview though, this is what it gives me:
couldn't initialize SDL: No available video device

i will attach the 
strace -o log.txt luvcview
whatever you call that. the logfile, right?
how to make it work? thanks in advance, much appreciated!

---

### Post by tidris on 2009-04-19
Is libsdl1.2debian installed?

---

### Post by iochinome on 2009-04-19
yes, according to apt-get, i have the newest version. what else could it be?

---

### Post by iochinome on 2009-04-20
i dont really know that much about logfiles, but i noticed that near the top it says 'no such file or directory' when referring to a really long path with libm.so.6 at the end. i googled libm- it is a math library for unix. is it possible that me not having this is causing the error?

thanks

---

### Post by tidris on 2009-04-20
> **iochinome said:**
> yes, according to apt-get, i have the newest version. what else could it be?

On my computer running intrepid 8.10 I am able to compile and run luvcview and I have the following SDL libs installed: libsdl1.2debian, libsdl1.2-dev, libsdl1.2debian-alsa.

---

### Post by iochinome on 2009-04-20
hmm.. this is definitely wierd. i tried sudo apt-get install on all of those and they seem to be installed. i am looking into the logfile, not really sure what i am supposed to be seeing, but here is something interesting:

from log.txt
open("/usr/local/lib/tls/i686/sse2/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/local/lib/tls/i686/sse2", 0xbfb8d9f0) = -1 ENOENT (No such file or directory)

it repeats that same line with variations on the second paramater many many times, all saying 'no such file or directory.' (which is true, that filepath does not exist for me on this computer.) i did a search on libm.so.6, turns out that libm is a math library used in unix systems. the point where these filepaths deviate from what i have on my pc, however, is right after "lib." what am i missing?

thanks

---

### Post by tidris on 2009-04-21
Those files aren't in my computer either, so I have to assume luvcview and SDL don't need them.

If I was in your shoes I would get the source code and compile it myself to see what happens. The source can be found here:

[http://packages.ubuntu.com/source/intrepid/luvcview](http://packages.ubuntu.com/source/intrepid/luvcview)

---

