---
title: "Multithreaded x264 decoding on Linux ?"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by alanwww1 on 2008-02-10
Hello !

I tried every possible way on Ubuntu Gutsy to play my 1080p mkv files with x264 coded streams.

Tried VLC, Mplayer, Smplayer, Totem etc.

They don't do multithreaded decoding ! On my Core 2 4300 dual core CPU has a 90-100% utilization on one core.

The strangest thing is on Win XP i tried FFDSHOW which afaik uses FFMPEG LIBAVCODEC and plays my files perfectly with even CPU core utilization. 

I really can't understand why a Win compiled version of the same codec works multithreaded and not the Linux compiled one.

Anyone has an idea ?

Thanks,

Alan from Hungary

---

### Post by mad_max0204 on 2008-02-10
I installed mplayer with all the codecs as it is described here on forum and x264 video works flawlessly.

---

### Post by alanwww1 on 2008-02-10
Sure you tried high bitrate content ?

Uptil 720p resolution all works fine, because even one core can handle it, but 
with a gigher rate one core is not enough.

:(

---

### Post by Degenerate on 2008-02-21
I have exactly the same experience. I can play high bit-rate 1080p mkvs using FFDShow on Windows XP. It uses both cores of my Athlon X2 3800 processor and gives about 80% CPU utilization. On Ubuntu It's limited to one core and cannot cope with 1080p.

The reason is that the code for multi-threaded H264 playback was introduced to FFMPEG only a few months ago. The FFDShow folks put out new builds almost daily using the latest code, but the [Gutsy packages]("http://packages.ubuntu.com/gutsy/libavcodec1d") are still using a FFMPEG snapshot from March 2007.

Unfortunately, [it looks like Hardy will be using the same outdated code.]("http://packages.ubuntu.com/hardy/libavcodec1d")

It's incredibly frustrating to have to use Windows for something you know Linux can do. The Ubuntu package maintainers need to wake up to the fact that the FFMPEG folks rarely do releases. Even they would recommend that the packages should be built from a recent snapshot of the FFMPEG CVS.

Update: [I've raised a bug.]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/194226") Not sure what good it will do at this stage.

---

### Post by Rizla on 2008-02-28
**This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Im going to be running into the same issue when i finishing building my new Quad Core box specifically for encoding x264 movies.  So are you saying that we'll need to compile the latest ffmpeg?  I'm a new user so compiling still seems waaaay over my head.  ./config .. make .. make install..  doesnt make sense to me.

---

### Post by andrew.46 on 2008-03-05
Hi,

> **mad_max0204 said:**
> I installed mplayer with all the codecs as it is described here on forum and x264 video works flawlessly.

 Can I ask which walkthrough you used?

         Andrew

---

### Post by chewearn on 2008-03-05
Sooo, I finally understood why that 1080p mkv file would not play in ubuntu.

I was thinking I might need to wait a few years until a 10GHz processor is available at low cost.
:lolflag:

Thanks to all..

---

### Post by chewearn on 2008-03-06
I was following this link to compile ffmpeg from svn snapshoot:
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

After make install, I tested playback the 1080p mkv.
Previously, the playback is severely stuttering in vlc and totem.
Now, in vlc, the playback is smooth.  In totem, the playback is still severely stuttering.

In both cases, I only notice one of the CPU core is used.  But possibly, the latest ffmpeg version is much more efficient that the old version in ubuntu repo, so now vlc can playback successfully.


I tested the above on a Core2Duo T7200 2GHz.

---

### Post by aeiah on 2008-03-06
apparently CoreAVC for windows will improve HD playback a lot. especially 1080p. its commercial but im sure if you're downloading HD films you'll be able to find it.

this site here has wrappers that'll make it run under 32bit and 64bit linux with mplayer, xine and mythtv:

[http://code.google.com/p/coreavc-for-linux/](http://code.google.com/p/coreavc-for-linux/)

---

### Post by drdrewdown on 2008-03-24
> **AstalaVista said:**
> I was following this link to compile ffmpeg from svn snapshoot:
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

After make install, I tested playback the 1080p mkv.
Previously, the playback is severely stuttering in vlc and totem.
Now, in vlc, the playback is smooth.  In totem, the playback is still severely stuttering.

In both cases, I only notice one of the CPU core is used.  But possibly, the latest ffmpeg version is much more efficient that the old version in ubuntu repo, so now vlc can playback successfully.


I tested the above on a Core2Duo T7200 2GHz.

i will be testing this in a couple hours & hope it works.. thanks for your information astalavista i hope it turns out well.

cheers

---

