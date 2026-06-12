---
title: "Playing a 1080 mkv"
date: 2011-04-21
forum: Multimedia Software
---

### Post by pieroxy on 2011-04-21
Hi there,

I have lots of 720p MKV files which play fine on VLC and/or mplayer. These are the two players I know.

Whenever I try to play a 1080p file, the video is sluggish and quickly desynchronizes from the audio (mplayer) or the sound is choppy (vlc).

This is because one CPU cannot decode a 1080p x264 video. Not powerful enough.

Now, I have a Q6600, with 4 cores. Options in mplayer and VLC to use more than one decoding thread don't seem to do anything at this date, as one core is only user (reported by TOP).

Any idea how I can work this problem out?

---

### Post by TenPlus1 on 2011-04-21
In VLC Preferences, go to Input & Codecs and change the "Skip H.264 in-loop deblocking filter" to "ALL", this helps when playing hi-res mkv's and h.264 videos for me...  You could also see if ticking the "Use GPU acceperation" works after installing libvdpau1.

---

### Post by SeijiSensei on 2011-04-21
Support for multi-threading is in [recent SVN versions]("http://www.mplayerhq.hu/design7/news.html") of mplayer.  You can follow [this article]("http://www.omgubuntu.co.uk/2011/01/mplayer-adds-daily-build-ppa-for-ubuntu-users/") to add a repository with these versions.  These are builds by the mplayer staff itself, so they should be trustworthy.

You will need to add "-lavdopts threads=4" to the mplayer command to use all four cores.

I'm not using the version in the repositories because I build the [mplayer2]("http://www.mplayer2.org/") fork from source.  (It has some features like support for ordered chapters in Matroska that aren't in the main trunk.)  However that's basically a patched version of the SVN code, and I can confirm it uses all four cores when using the xv video driver to display 1080p material.

libvdpau only works with recent NVIDIA cards (8xxx and later).  If you have an NVIDIA adapter, install the proprietary drivers if you haven't already, then use "-vo vdpau" or select it from the driver list in smplayer. This method offloads the H.264 decoding process to the graphics hardware.  If you can use this approach, you won't need to worry about multi-threading.

---

### Post by beew on 2011-04-21
You can get a multi-threaded version of mplayer (build from svn and statically linked to its own ffmpeg library) from this ppa.[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc") (I don't use coreavc, I just install mplayer)

It plays 1080p mkv smoothly even with the open source driver on my Nvidia laptop. I tried the MOTU daily build on Natty but it is not as good, fast motion scenes kind of sluggish but ripps' version plays anything smoothly on all machines I have tested.

For multithreaded VLC, see andrew.46's post (and he is the man to go to for VLC question)
[http://ubuntuforums.org/showthread.php?t=1734268&page=2](http://ubuntuforums.org/showthread.php?t=1734268&page=2)

> **TenPlus1 said:**
> In VLC Preferences, go to Input & Codecs  and change the "Skip H.264 in-loop deblocking filter" to "ALL", this  helps when playing hi-res mkv's and h.264 videos for me...  You could  also see if ticking the "Use GPU acceperation" works after installing  libvdpau1.

That would play the video but the quality may be poor, which defeats the purpose of 1080p though.

---

### Post by beew on 2011-04-21
I forgot to mention, I find  the portable version of VLC works very well  on my system
[http://portablelinuxapps.org/](http://portablelinuxapps.org/)(try VLC 1.20-git)

---

### Post by shantiq on 2011-04-21
> **pieroxy said:**
> Hi there,

I have lots of 720p MKV files which play fine on VLC and/or mplayer. These are the two players I know.

Whenever I try to play a 1080p file, the video is sluggish and quickly desynchronizes from the audio (mplayer) or the sound is choppy (vlc).

This is because one CPU cannot decode a 1080p x264 video. Not powerful enough.

Now, I have a Q6600, with 4 cores. Options in mplayer and VLC to use more than one decoding thread don't seem to do anything at this date, as one core is only user (reported by TOP).

Any idea how I can work this problem out?


Pieroxy i found whatever settings i changed on vlc and mplayer 1080 was always a problem especially on vlc sadly as it is still my favourite player

smplayer ( which is a frontend for mplayer) which is in synaptic on the other hand plays 1080p with no problems whatsoever on my machine so maybe give that one a whirl see how it goes...

options/preferences/video/vdpau   needs to be ticked



also [xmbc]("http://xbmc.org/") has no problem whatsoever with 1080p


but i must say 10plus1   this > In VLC Preferences, go to Input & Codecs and change the "Skip H.264 in-loop deblocking filter" to "ALL", this helps when playing hi-res mkv's and h.264 videos for me... You could also see if ticking the "Use GPU acceperation" works after installing libvdpau1.   really works for me thanx

[nice one]("http://www.youtube.com/watch?v=85C2JnZOY4k") to test it with

---

### Post by SeijiSensei on 2011-04-21
> **shantiq said:**
> smplayer ( which is a frontend for mplayer) which is in synaptic on the other hand plays 1080p with no problems whatsoever on my machine so maybe give that one a whirl see how it goes...

What matters is the mplayer version in use and whether you can use VDPAU for H.264 decoding.  SMplayer is just a shell.

If the OP doesn't have a recent NVIDIA card, then he'll need to rely on the machine's CPU for decoding.  Using a multi-threaded version of mplayer can make a big difference in that case.

---

### Post by pieroxy on 2011-04-21
> **beew said:**
> You can get a multi-threaded version of mplayer (build from svn and statically linked to its own ffmpeg library) from this ppa.[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc") (I don't use coreavc, I just install mplayer)


I downloaded mplayer-build-1.0~rc4+git20110329.683953a and built mplayer. Still one thread used. I built ffmpeg-mt and I can play a movie quite smoothly (more than 100% CPU being used) with ffplay. But ffplay is... crude. 

In the top directory, I'm supposed to do a ./init --shallow but it fails with:

fatal: Not a git repository (or any of the parent directories): .git


Any idea on how to build it?

---

### Post by pieroxy on 2011-04-21
> **SeijiSensei said:**
> Support for multi-threading is in [recent SVN versions]("http://www.mplayerhq.hu/design7/news.html") of mplayer.  You can follow [this article]("http://www.omgubuntu.co.uk/2011/01/mplayer-adds-daily-build-ppa-for-ubuntu-users/") to add a repository with these versions.  These are builds by the mplayer staff itself, so they should be trustworthy.

You will need to add "-lavdopts threads=4" to the mplayer command to use all four cores.

I'm not using the version in the repositories because I build the [mplayer2]("http://www.mplayer2.org/") fork from source.  (It has some features like support for ordered chapters in Matroska that aren't in the main trunk.)  However that's basically a patched version of the SVN code, and I can confirm it uses all four cores when using the xv video driver to display 1080p material.

libvdpau only works with recent NVIDIA cards (8xxx and later).  If you have an NVIDIA adapter, install the proprietary drivers if you haven't already, then use "-vo vdpau" or select it from the driver list in smplayer. This method offloads the H.264 decoding process to the graphics hardware.  If you can use this approach, you won't need to worry about multi-threading.

I tried the nightly and I can't compile it... it fails at some point with an error.

---

### Post by SeijiSensei on 2011-04-22
Did you try installing from the PPA repository as described in [the link I gave you]("http://www.omgubuntu.co.uk/2011/01/mplayer-adds-daily-build-ppa-for-ubuntu-users/")?  You shouldn't need to compile anything if you use those.

If you want to give compiling a shot, I'd suggest using the source from the [mplayer2]("http://ftp.mplayer2.org/pub/release/mplayer2-build-2.0.tar.bz2") site, then doing the following:

```

sudo apt-get build-essential yasm git autogen autoconf automake libtool
sudo apt-get build-dep mplayer
cd /directory/where/you/downloaded/tarball
tar xjvf mplayer2-build-2.0.tar.bz2
cd mplayer2-build
./init
make
sudo make install

```

I didn't have auto* and libtool installed even after using build-dep, so I encountered some compiler errors along the way.  Once I had all the tools, mplayer2 built pretty easily.  It installs to /usr/local by default; the player is /usr/local/bin/mplayer.  On my 64-bit machine /usr/local/bin is a symlink to /usr/local/bin32, which appears to be something that mplayer2 created during installation.  bin32 has the same timestamp as mplayer.

---

### Post by D-G on 2011-04-22
> **pieroxy said:**
> I have lots of 720p MKV files which play fine on VLC and/or mplayer. These are the two players I know.

Whenever I try to play a 1080p file, the video is sluggish and quickly desynchronizes from the audio (mplayer) or the sound is choppy (vlc).
Probably pirated files. Try originals.

---

### Post by pieroxy on 2011-04-25
> **SeijiSensei said:**
> Did you try installing from the PPA repository as described in [the link I gave you]("http://www.omgubuntu.co.uk/2011/01/mplayer-adds-daily-build-ppa-for-ubuntu-users/")?  You shouldn't need to compile anything if you use those.

If you want to give compiling a shot, I'd suggest using the source from the [mplayer2]("http://ftp.mplayer2.org/pub/release/mplayer2-build-2.0.tar.bz2") site, then doing the following:

```

sudo apt-get build-essential yasm git autogen autoconf automake libtool
sudo apt-get build-dep mplayer
cd /directory/where/you/downloaded/tarball
tar xjvf mplayer2-build-2.0.tar.bz2
cd mplayer2-build
./init
make
sudo make install

```

I didn't have auto* and libtool installed even after using build-dep, so I encountered some compiler errors along the way.  Once I had all the tools, mplayer2 built pretty easily.  It installs to /usr/local by default; the player is /usr/local/bin/mplayer.  On my 64-bit machine /usr/local/bin is a symlink to /usr/local/bin32, which appears to be something that mplayer2 created during installation.  bin32 has the same timestamp as mplayer.
There is no 'init' file in the tarball you linked to (mplayer2-build-2.0.tar.bz2)

The problem with the PPA repo is that it will replace my existing mplayer install and I'm not sure I'm comfortable with this. Oh well, it looks like the only option now. I'll give it a shot.

---

### Post by SeijiSensei on 2011-04-25
> **pieroxy said:**
> There is no 'init' file in the tarball you linked to (mplayer2-build-2.0.tar.bz2)

I must have built it differently the first time through.  Now the README file says to ignore the ./init command when building from the tarball.

[quote=README]
"Basic use" (leave out the "./init" part, the tarball does not need that) details see below.
[/quote]

Sorry!

---

### Post by pieroxy on 2011-04-28
Thanks for the info. I seem to have a few packages out of date (error below), so I'll update to Natty first and try to compile again. 

Any idea when those packages are going to make it to Ubuntu?


```
checking for FONTCONFIG... no
configure: error: Package requirements (fontconfig >= 2.4.2) were not met:

No package 'fontconfig' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables FONTCONFIG_CFLAGS
and FONTCONFIG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
make: *** [libass-config] Error 1

```

---

### Post by K_45 on 2011-04-28
Try a clean install of the distro of your choice, then install VLC and try it. If you are running 9.04, its time to upgrade.

---

### Post by pieroxy on 2011-04-28
> **K_45 said:**
> Try a clean install of the distro of your choice, then install VLC and try it. If you are running 9.04, its time to upgrade.

I like insightful posts that don't assume you're dumb ;-) My distro was up to date (as of yesterday since 11.04 is out today.)

VLC didn't cut it at all, or I don't know how to do it. I will install Natty tonight and try it out again.

---

### Post by pieroxy on 2011-05-23
So... Here I am again with Natty this time.

mplayer2 compiles fine, but alas, I get no video when playing a file. I have an ATI GC with foss drivers. vlc isn't working either... 

I don't mind compiling stuff, but nothing works so far. Has anyone without VDPAU had any luck?

This drives me mad. I have twice the cpu power than my Win box, and I can't play a 1080 movie. On my win box, not only does it use the graphics acceleration, but it uses multi core as well... Oh well. I'll end up reencoding the movie in 720p I guess. Irony, encoding the movie takes up all 4 cores and is actually faster than playing it... (39fps). Go figure.

---

### Post by pieroxy on 2011-05-24
> **K_45 said:**
> Try a clean install of the distro of your choice, then install VLC and try it. If you are running 9.04, its time to upgrade.

K_45, I did just that. Clean install of Natty (amd64). I installed VLC, but no luck. It tops at 25%CPU (1 core) and after a few seconds it becomes choppy. Unusable. Did you have more luck?

---

