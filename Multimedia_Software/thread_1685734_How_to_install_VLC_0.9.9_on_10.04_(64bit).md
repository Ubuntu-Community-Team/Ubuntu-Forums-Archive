---
title: "How to install VLC 0.9.9 on 10.04 (64bit) ?"
date: 2011-02-11
forum: Multimedia Software
---

### Post by user68 on 2011-02-11
Since converting to Ubuntu a few week ago I've found VLC to be the most difficult to understand by far. I've followed many guides on installing different versions and want to now try VLC 0.9.9, as I've read there's a chance this version might work for what I'm trying to do. I've followed a couple of guides to installing 0.9.9 that were written for 8.04 but am getting errors.

/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation R_X86_64_32 against `ff_a64multi_encoder' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[6]: *** [libavcodec_plugin.la] Error 1
make[6]: Leaving directory `/home/mark/vlc-0.9.9/modules/codec/avcodec'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/mark/vlc-0.9.9/modules/codec/avcodec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/mark/vlc-0.9.9/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/mark/vlc-0.9.9/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mark/vlc-0.9.9/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mark/vlc-0.9.9'
make: *** [all] Error 2

Can anyone please help?

---

### Post by Cracklepop on 2011-02-11
Mm? Why 0.9.9?

 Install 1.1.4 straight out of the repositories: no hassle, no headaches.
System > Administration > Synaptic... > type vlc into the search box > tick the box next to  vlc > click apply at the top... > done!

---

### Post by user68 on 2011-02-11
I wish I could use the current VLC version but Im trying to grab the stream from a dreambox satellite receiver for Wowza media server. Have had no success with any VLC yet and I read somewhere that only VLC 0.9.9 and maybe 1.0.5 work due to changes made in subsequent versions.

---

### Post by user68 on 2011-02-11
Can somebody please help me with this error?

/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation  R_X86_64_32 against `ff_a64multi_encoder' can not be used when making a  shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[6]: *** [libavcodec_plugin.la] Error 1
make[6]: Leaving directory `/home/mark/vlc-0.9.9/modules/codec/avcodec'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/mark/vlc-0.9.9/modules/codec/avcodec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/mark/vlc-0.9.9/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/mark/vlc-0.9.9/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mark/vlc-0.9.9/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mark/vlc-0.9.9'
make: *** [all] Error 2

---

### Post by Cracklepop on 2011-02-11
I personally can't help, 86, but maybe this will be of some use, even though it isn't exactly what you want?:  [http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

---

### Post by mc4man on 2011-02-11
What ffmpeg source are you linking in you vlc build? A 64 bit vlc build either needs compatible _patched_  static ffmpeg or a  shared ffmpeg
That's the very first error (shared builds almost always use -fPIC
> relocation R_X86_64_32 against `ff_a64multi_encoder' can not be used when making a shared object; recompile with -fPIC

It's probable you can build 0.9.9 in lucid, maybe a little work. 
 The 1.0.5 would be fairly straightforward, I know I did that build when using lucid for a very short while.

---

### Post by user68 on 2011-02-11
The 1.0.5 looks like my best option. I've downloaded vlc-1.0.5.tar.bz2 from download.videolan.org. Should I install it by building the development files, live555, codecs, x264 and FFmpeg as described in Andrew.46's thread?  [http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

What I find most difficult is knowing which development files I need - is there a guide somewhere or is there a standard set of files for all versions of VLC and Ubuntu?

---

### Post by mc4man on 2011-02-11
You could try using that guide - though it's designed for the current 1.2-git. It will provide a patched ffmpeg source, though the 0.6.X 
(not sure if there is any issue there or not.

The build-deps would be more than needed, maybe a few package name changes. You'd need to work that out or look for some posts later in thread about building the 1.1.X version, more like what you need.

What may prove easier is to remove any current self-builf ffmpeg and x264.

Add medibuntu so you get the 'extra' versions of ffmpeg libs

Then a sudo apt-get build-dep vlc should provide most of the needed/desired dependencies. (inc. a shared ffmpeg and x264

The 1.0.X vlc needs to have some things enabled in the ./configure, don't have a minimum example handy here, certainly several posted either in that thread or this forum.

This would be a decent start
```
./configure --enable-libmpeg2 --enable-vorbis --enable-shout \
--enable-qt4 --enable-flac --enable-speex --enable-libmpeg2 --enable-theora \
--enable-twolame --enable-faad  --enable-v4l --enable-realrtsp --enable-real \
--enable-snapshot
```

Run the configure and then scroll back in the terminal and review - passing a vlc configure doesn't guarantee a well enabled build
At your source prompt ./configure --help will show you what is enabled by default and what's not.

See here for 1.0.6 on 10.10, similar deal
[http://ubuntuforums.org/showthread.php?p=10022290](http://ubuntuforums.org/showthread.php?p=10022290)

---

