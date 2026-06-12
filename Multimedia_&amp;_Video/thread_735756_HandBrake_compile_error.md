---
title: "HandBrake compile error"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by BurkDP on 2008-03-26
I'm running a minimal (CLI) Gusty 7.10 install and every time I try to compile handbrake from the latest svn I get this error

antediluvian@antediluvian:~/hb-dev$ jam
...found 320 target(s)...
...updating 1 target(s)...
[B]Link HandBrakeCLI 
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status[/B]

g++  -o HandBrakeCLI  test/test.o test/parsecsv.o libhb/libhb.a contrib/lib/liba52.a contrib/lib/libavformat.a contrib/lib/libavcodec.a contrib/lib/libavutil.a contrib/lib/libdca.a contrib/lib/libdvdread.a contrib/lib/libmp4v2.a contrib/lib/libfaac.a contrib/lib/libmp3lame.a contrib/lib/libmpeg2.a contrib/lib/libvorbis.a contrib/lib/libvorbisenc.a contrib/lib/libogg.a contrib/lib/libsamplerate.a contrib/lib/libx264.a contrib/lib/libxvidcore.a contrib/lib/libmkv.a contrib/lib/libswscale.a contrib/lib/libtheora.a -lz -lpthread -ldl 

...failed Link HandBrakeCLI ...
...failed updating 1 target(s)...
antediluvian@antediluvian:~/hb-dev$ 


I've installed all the required packages/dependencies (to my knowledge) and some extras:
automake
build-essential
dpkg-dev
gcc
gcc-multilib
g++
g++-multilib
jam
libtool
make
libdvdcss2 (medibuntu)
nasm

I've gotten it to compile on another machine running a full Ubuntu 7.10 install, but only after going into synaptic and installing everything in the entire g series of compilers, and anything even tangentially related to them. I could go through and systematically try to determine which package fixed it or what, but i though I'd ask and see if there's a simple solution I'm not aware of. I did check through the forums and internet but couldn't find this specific problem mentioned.

I don't really know much about Linux and coding in general so i was going to put this in Absolute Beginners Talk, but I've had to sudo nano some config files (following **blatant** instructions) in the past so this seemed a better choice.

I know the latest svn dev build is 'at your own risk', and that there're pre-compiled binaries, but my personal server I'm building is AMD so I'd have to compile it from the source regardless (same error).

Any answer would be appreciated. Thank you for your time and consideration.

PS - This particular compile is from and ibook G3 I recently forced 7.10 onto, didn't expect it to work but thought why not give it a go.  I have gotten the exact same error on a newer i386 laptop so it'd be helpful to get any answer. I just realized i haven't tried make, but all the indicators from the HandBrake site wiki indicate jam is the preferred method.

---

### Post by BurkDP on 2008-03-26
deleted

---

### Post by BurkDP on 2008-03-26
Adding the *zlib1g-dev* package made it work. \\:D/ Go figure. :rolleyes:

I got the info from this post [http://forum.handbrake.fr/viewtopic.php?f=13&t=4740]("http://forum.handbrake.fr/viewtopic.php?f=13&t=4740")

---

### Post by cchi on 2008-04-27
Very nice..  that was what I was missing it seems too..
Thanks!

---

