---
title: "Noobie installing AvView"
date: 2009-12-17
forum: Multimedia Software
---

### Post by shortmort37 on 2009-12-17
The AvView INSTALL instructions includes this:

[COLOR=Blue]To compile:

    ./configure --with-ffmpeg=/path/to/compiled/ffmpeg/tree
    make
    
Note: I mean *** compiled *** ffmpeg tree, i.e. the where you compiled ffmpeg, 
not where you installed. it. AVview does not rely on installed ffmpeg binaries.[/COLOR]

How the h*ll do I know where ffmpeg was compiled?  I just installed it using the Synaptic Package Manager.

The installation of all the prerequisites went swimmingly, including gatos.  Not sure where to go from here, though.

adTHANKSvance
Dan

---

### Post by Ylon on 2009-12-18
> **shortmort37 said:**
> The AvView INSTALL instructions includes this:

[COLOR=Blue]To compile:

    ./configure --with-ffmpeg=/path/to/compiled/ffmpeg/tree
    make
    
Note: I mean *** compiled *** ffmpeg tree, i.e. the where you compiled ffmpeg, 
not where you installed. it. AVview does not rely on installed ffmpeg binaries.[/COLOR]

How the h*ll do I know where ffmpeg was compiled?

To find file:
Application > [Accessories](http://futuredesktop.org/karmic/images/picture-7a.png) > Search for Files...


and your reply is: /usr/bin/ffmpeg


Enjoy

---

### Post by shortmort37 on 2009-12-18
That's where ffmpeg ***is*** -- not, where it was ***compiled***.

I've since learned that the problem is I don't have ffmpeg-devel -- that the package is stripped.  Here's the complaint I'm getting in config.log:
[COLOR=Blue]
configure:8339: gcc -o conftest -g -O2 -I/usr/bin/ffmpeg/libavformat -I/usr/bin/
ffmpeg/libavcodec    conftest.c -lXext -lX11 -logg -lzvbi -lpthread -lm -lz -ldl
  /usr/bin/ffmpeg/libavformat/libavformat.a /usr/bin/ffmpeg/libavcodec/libavcode
c.a >&5
gcc: /usr/bin/ffmpeg/libavformat/libavformat.a: Not a directory
gcc: /usr/bin/ffmpeg/libavcodec/libavcodec.a: Not a directory
cc1: error: /usr/bin/ffmpeg/libavformat: Not a directory
cc1: error: /usr/bin/ffmpeg/libavcodec: Not a directory
configure:8342: $? = 1
configure: program exited with status 1
[/COLOR]
It ain't a directory, because I don't have the libraries -- just the binary ffmpeg.

From this thread:

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

I followed these instructions:

sudo apt-get install ffmpeg libavcodec-extra-52

And then searched the drive for the missing libraries, but they didn't show up.

So, how do I get them?  Do I have to download (from somewhere) the ffmpeg kit and compile it?

Dan

---

### Post by shortmort37 on 2009-12-18
That's what I did:  I installed ffmpeg using this tutorial:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

I got further this time -- no complaints about libraries.  But, I get:

[COLOR=Blue]checking ffmpeg version...

*** AVview requires ffmpeg 0.4.8
If you are sure you are using correct version of ffmpeg check config.log for details[/COLOR]

AVview requires 0.4.8 specifically?!  I edited the inline code for conftest.c to skip this check (to my demise?), and now it's complaining about X libraries...

Oh, well.  I'll revisit another day.  Other fish to fry.

Dan

---

