---
title: "can/how you convert handbrake m4v to webm?"
date: 2012-10-12
forum: Multimedia Software
---

### Post by nhtrader on 2012-10-12
Handbrake 0.9.8 (x86_64)
ubuntu 12.04.1 LTS (64)
xfe 4.8
mythtv v0.25.3
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1


I use handbrake to convert movies from mpg/vob to mp4/m4v. Now I'd like to convert them to webm. How can I accomplish this?

I have tried the following command and it didn't work. The output is just random noise/static.

avconv -i "mymovie.m4v" -threads 8 -c:v libvpx -acodec libvorbis -b:v 3900k -pass 1 -deadline good -f webm "mymovie.webm"

---

### Post by nhtrader on 2012-10-13
Well, I'm making progress. I finally got the correct parameters to create what I want - a *.webm of my movie. It isn't optimized yet, but this command worked:

avconv -i "mymovie.mp4" -threads 8 -c:v libvpx -acodec libvorbis -qmax 63 -qmin 10 -b:v 5000000 -pass 2 -f webm "mymovie.webm"

---

### Post by nhtrader on 2012-10-13
Tried a different setting:

avconv -i "mymovie-PG.m4v" -threads 8 -c:v libvpx -acodec libvorbis -qmax 60 -qmin 15 -b:v 4000000 -pass 2 -f webm "mymovie-PG.webm"

This also worked, but...

1. I can't get either of the *.webm movies to play in Opera 12.02 (X86_64). Player controls appear but no movie plays.
2. If I use MythTV FrontEnd to play the movie, it plays, but it is highly pixelated - poor quality for viewing.
3. However if I play the movie using VLC, the movie quality is much better. There are only a few digital-artifacts/slight pixelation. Viewing the movie with VLC is accecptable. Using MythTV's player is unacceptable.
4. The same result applies to both *.webm movies which were created using two different settings.

So, why does the viewing quality vary among the various video players?
Why doesn't the movie play using Opera (webbrowser)?

---

### Post by dniMretsaM on 2012-10-13
I have no experience with Handbrake, but you might try another tool such as FFmpeg.

On a side note, you edit posts if the last post was less that 24 hours ago, per the Ubuntu Forums CoC.

---

### Post by nhtrader on 2012-10-14
> **dniMretsaM said:**
> I have no experience with Handbrake, but you might try another tool such as FFmpeg.

On a side note, you edit posts if the last post was less that 24 hours ago, per the Ubuntu Forums CoC.

Thanks for the education. I didn't know that I should append my own post.


As for ffmpeg, apparently avconv is the "future". ffmpeg is being phased out.

And to be clear, I'm only referencing handbrake b/c I used it to convert *.VOB to *.m4v (it works brilliantly). Then I was forced to find another program so that I could convert *.m4v to *.webm; hence, avconv.

The next step for me would be to learn how to write a script that uses "avconv" twice. Once, to create the *.m4v and second, to create the *.webm directly from *.VOB. But for now I'm happy to use avconv once to convert *.m4v to *.webm.

---

### Post by dniMretsaM on 2012-10-14
> **nhtrader said:**
> As for ffmpeg, apparently avconv is the "future". ffmpeg is being phased out.

That's not entirely correct. Read [this]("http://ubuntuforums.org/showthread.php?p=12050679") for some info.

---

### Post by FakeOutdoorsman on 2012-10-14
> **nhtrader said:**
> As for ffmpeg, apparently avconv is the "future". ffmpeg is being phased out.

There is much confusion over this topic. FFmpeg (the project) and ffmpeg (the program) are still very active. Ubuntu switched from FFmpeg to a fork called libav. For some time libav also had a fake "ffmpeg" as a temporary name until they created avconv (their version of ffmpeg). During that transition transition libav made a message something like, "ffmpeg is no longer being development". It is true that their "ffmpeg" is no longer developed, but they made no effort to make it clear to users who may make no distinction between the program named ffmpeg and project named FFmpeg. How are general users even supposed to know that Ubuntu switched to a fork or make a distinction between "ffmpeg" and "FFmpeg"? libav taking advantage of the confusion to mislead users was not a good idea in my opinion; I have little doubt that it was intentional. At the end of the day it only hurts the users.

libav upstream eventually removed all traces of their fake ffmpeg, and the message, but Ubuntu still contains the fake ffmpeg and probably will do so some quite some time.

---

### Post by nhtrader on 2012-10-18
> **FakeOutdoorsman said:**
> There is much confusion over this topic. FFmpeg (the project) and ffmpeg (the program) are still very active. Ubuntu switched from FFmpeg to a fork called libav. For some time libav also had a fake "ffmpeg" as a temporary name until they created avconv (their version of ffmpeg). During that transition transition libav made a message something like, "ffmpeg is no longer being development". It is true that their "ffmpeg" is no longer developed, but they made no effort to make it clear to users who may make no distinction between the program named ffmpeg and project named FFmpeg. How are general users even supposed to know that Ubuntu switched to a fork or make a distinction between "ffmpeg" and "FFmpeg"? libav taking advantage of the confusion to mislead users was not a good idea in my opinion; I have little doubt that it was intentional. At the end of the day it only hurts the users.

libav upstream eventually removed all traces of their fake ffmpeg, and the message, but Ubuntu still contains the fake ffmpeg and probably will do so some quite some time.

This is of course off topic, but I'd like to get some closure on this point and to help other users that thread this path.

As you clarified, ffmpeg the program and FFmpeg the project are different. ffmpeg from libav is being phased out for avconv and yet there still exists the FFmpeg project. So if I use "sudo apt-get install ffmpeg" or synaptic and search for ffmpeg; are these the FFmpeg project's software or libav's?

---

### Post by FakeOutdoorsman on 2012-10-18
> **nhtrader said:**
> So if I use "sudo apt-get install ffmpeg" or synaptic and search for ffmpeg; are these the FFmpeg project's software or libav's?

libav as of Ubuntu 11.04 Natty Narwhal, if I remember correctly. One way to tell is to look at the console output.

FFmpeg:
```
ffmpeg version N-45086-ged015f6 Copyright (c) 2000-2012 the **FFmpeg** developers
```

libav:
```
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the **Libav** developers
```

---

### Post by nhtrader on 2012-10-18
> **FakeOutdoorsman said:**
> libav as of Ubuntu 11.04 Natty Narwhal, if I remember correctly. One way to tell is to look at the console output.

FFmpeg:
```
ffmpeg version N-45086-ged015f6 Copyright (c) 2000-2012 the **FFmpeg** developers
```

libav:
```
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the **Libav** developers
```


Thanks for bringing this to light and clarifying the details. I would have assumed that using synaptic and apt-get would have installed FFmpeg - the project. But it does not. 

Again, thanks for helping delve into this and making me aware of the two "flavors" of ffmpeg. Now I have to learn how to add the FFmpeg project's version of ffmpeg and remove libav's version.

And now, hopefully this thread can resume the original topic of webm conversions and optimizations.

---

### Post by FakeOutdoorsman on 2012-10-19
> **nhtrader said:**
> Now I have to learn how to add the FFmpeg project's version of ffmpeg and remove libav's version.

You have several options. You can [compile FFmpeg](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) or use an already compiled "static" build: for [kernel 3.2.x or later](http://ffmpeg.gusari.org/static/) (32-bit or 64-bit), for [kernel 2.6.26 or later](http://dl.dropbox.com/u/24633983/ffmpeg/index.html) (64-bit only). Also see [Ubuntu kernel chart](http://en.wikipedia.org/wiki/Ubuntu_releases#Table_of_versions).

The advantages of compiling include full control and customization, and most recent code resulting in more bug fixes and features. The disadvantages include compilation time and possible non-compatibility with repository packages that depend on the so-called ffmpeg package.

The static build advantages include ease of use (just download, extract, and use), and you don't need to spend time compiling but they might not support what you want. Note to use the binary you use: ./ffmpeg -i input ...

Of course you can have both the repo libav/fake-ffmpeg/avconv package to satisfy various dependencies, and a compiled ffmpeg on the same system, but the guide does not show how to do that yet.

---

### Post by nhtrader on 2012-10-19
> **FakeOutdoorsman said:**
> Of course you can have both the repo libav/fake-ffmpeg/avconv package to satisfy various dependencies, and a compiled ffmpeg on the same system, but the guide does not show how to do that yet.

Much Obliged. Thanks again. 

BTW, I might as well beat this to death. I know that VLC uses FFmpeg; not libav's ffmpeg. I also have VLC installed. Does this mean that I already have FFmpeg installed and available to use? I don't think the answer is yes, but perhaps you can confirm this suspicion.

---

### Post by evilsoup on 2012-10-19
VLC uses a lot of ffmpeg *libraries*, but I don't think it has the ffmpeg program.

---

### Post by FakeOutdoorsman on 2012-10-19
> **evilsoup said:**
> VLC uses a lot of ffmpeg *libraries*, but I don't think it has the ffmpeg program.

evilsoup is correct. [Dependencies of VLC](http://packages.ubuntu.com/precise/vlc) include libavcodec and libavutil, traditionally FFmpeg libraries, but now also supplied by the fork.

---

### Post by nhtrader on 2012-10-21
Got it. Thanks to you both (FakeOutdoorsman & evilsoup)

---

### Post by xscd on 2012-12-19
There are now several user-friendly (GUI) programs in Linux that can encode into the .webm format (WebM is a container file format based on Matroska but which can contain only VP8 video and ogg-vorbis audio), including Arista and Transmageddon.

---

