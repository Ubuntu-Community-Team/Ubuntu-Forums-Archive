---
title: "calling all obsessive music junkies..."
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by fflarex on 2007-06-19
So far I've been ripping my collection with the FLAC defaults on Sound Juicer, which is fine as I'm not so paranoid that I need EAC or anything like that. But what I *would* like to do is re-encode my collection to the latest version of FLAC, 1.1.4 at the maximum compression level in order to save some space. What's the best way to do this? I tried getting foobar2000 to work on my Ubuntu box, but it only seems to want to tag things right now, and I can't get the converter to work.

After I'm done ripping my entire collection (which will not be for a while), I'm going to want to upgrade the LAME version from 3.96.1 to 3.97 and encode them at VBR quality 4 or 5 (for use on my DAP). I've so far been unable to find a suitable converter that let's me specify all of this (both for FLAC and LAME), unless I feel like working from the command line half the time, or at least needing to input a confusing command to just set it up.

Any help is appreciated.:)

---

### Post by usernamed on 2007-06-25
First, install grip:
```
sudo apt-get install grip
```

Then look at the link below:

[http://www.hydrogenaudio.org/forums/index.php?showtopic=45939]("http://www.hydrogenaudio.org/forums/index.php?showtopic=45939")


Hope this helps!

---

### Post by fflarex on 2007-06-25
Okay, but what is the best way to update the encoders that come with Feisty Fawn? The restricted LAME codec is 3.96.1 when the latest stable version is 3.97,  the FLAC encoder is also not up-to-date with version 1.14, and I would like to use aoTuV for Vorbis encoding.

---

### Post by Delirious on 2007-06-30
> **fflarex said:**
> Okay, but what is the best way to update the encoders that come with Feisty Fawn? The restricted LAME codec is 3.96.1 when the latest stable version is 3.97,  the FLAC encoder is also not up-to-date with version 1.14, and I would like to use aoTuV for Vorbis encoding.


I'm also curious as to why flac is so out of date, apt-get installed version 1.12?

---

### Post by hugmenot on 2007-07-28
When I was still on feisty I built those myself.

Lame 3.97, vorbis aotuv and FLAC 1.1.4.
I&#8217;m afraid I deleted the packages, though.

It&#8217;s not hard, building takes a while though. It&#8217;s essentially a backporting process.

---

### Post by fflarex on 2007-08-05
How did you do it then? I've essentially just been using windows executables instead, because compiling always failed on Ubuntu.

---

### Post by hugmenot on 2007-08-06
It&#8217;s easy but it takes a while compiling. And for aotuv I would wait until the next release is done, soon.

Just add the deb-src lines of gutsy for a minute -- I&#8217;ll just assume basic knowledge for now, okay?. 

```
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse universe
```

Then, after a cache update, go "apt-get source lame flac libvorbis0".
To make sure all can be built fetch the dependencies with "apt-get build-dep lame flac libvorbis0". Then you cd into the new directories and call "dpkg-buildpackage -rfakeroot -b" in each one. The results will be placed in the containing directory.

I can explain how to patch vorbis with the aotuv patch if you want to know.

And if you edit the debian/changelog file you can mark the release with you own version  info. Make sure the entry is well-formed (by analogy).

---

### Post by fflarex on 2007-08-06
Thanks. I found instructions on how to patch vorbis on google. Can I somehow patch LAME and FLAC as well?

Why exactly do the repos have the latest versions of these (although for gutsy, but still) while gstreamer (which nearly every gnome program uses) is behind the times?

---

### Post by hugmenot on 2007-08-06
You got it wrong. Once you have the basic libs installed even GStreamer will use them. That means if you install liblame 3.97 you will encode with LAME 2.97 from Sound Juicer. The same with FLAC and Vorbis. GStreamer is just an intermediary layer.

EDIT: AFAIK Lame and FLAC are recent enough, aren&#8217;t they. What patches do you want to apply?

Oh, and if you&#8217;re unlucky GSteamer might have to be rebuilt as well. This is stuff that usually prevents clean backporting and is what distros deal with every day, it&#8217;s their job. You might consider upgrading to gutsy in that case. But, I hope Lame and FLACs ABI are stable anough.

---

### Post by fflarex on 2007-08-06
Alright, I guess I was confused about GStreamer. I thought media formats had to be specially implemented into GStreamer somehow.

I guess nothing's too outdated, but the newest versions of LAME and FLAC are perfectly stable and better than previous versions, so I don't see why they haven't been updated yet. As for ogg, I'm just disappointed that Xiph.org has been dead for so long and won't officially incorporate the new aoTuV encoders like they did with Beta 2. If you go to their website the last update they had was in 2004...

Anyways, back on topic. I got FLAC & LAME to build just fine. I tried Ogg Vorbis using your instructions and got an error. Does libvorbis0 exist, or should it be libvorbis0a? Also, when I use apt-get for source code, where does the source go?

EDIT: I just noticed FLAC 1.2.0 has been released. Looks like some format changes are upcoming.

---

### Post by hugmenot on 2007-08-07
So, the versions in Gutsy are

```
    lame |   3.97-0.0 | http://archive.ubuntu.com gutsy/multiverse Sources
      flac | 1.1.4-3ubuntu1 | http://archive.ubuntu.com gutsy/main Sources
 libvorbis | 1.2.0.dfsg-1 | http://archive.ubuntu.com gutsy/main Sources

```

[you can see I made an error citing the vorbis package, it is ...0a.].
I guess unless the upstream version freeze comes up theres a chance FLAC gets updated.

The source tarballs are downloaded into the current dir and extracted into the current dir.
If you want to patch Vorbis with aotuv, the cleanest way is to drop the patch into the debian/patches folder. There are different styles of debian patch (like quilt or dpatch) and some involve entering the patch into the 00list file. The patch then gets applied before compilation and not to the extracted source directly.

---

### Post by fflarex on 2007-08-07
Alright, thanks. I got it all working now, except that, in trying to upgrade to flac 1.2.0, I messed something up again. Building flac 1.2.0 from source failed, so I tried to get back to version 1.1.4 (which compiled correctly). However, now it insists that it is indeed version 1.2.0

I've tried removing everything that I felt comfortable wouldn't mess up my system, but no matter how many times I remove the current version of flac and compile a different version, it insists that is is 1.2.0

Do you have any idea what might be preventing me from compiling 1.2.0 correctly, or if not, how I can get the version straight? I'm not quite sure anyone on these forums are the experts I'm looking for, but I don't really know where to ask this. (maybe the hydrogenaudio forums, but I never get confirmation emails when I try to register there)

---

### Post by hugmenot on 2007-08-08
Well, without any output of when it failed, not really.
As for why it claims it is 1.2, did you install perhaps flac 1.2 with a make script and it got installed to /usr/local?

What does "which flac" or "whereis flac" say?

EDIT: In addition, I made a debian package source tarball for you. Just extract the source, cd into it, and call "dpkg-buildpackage -rfakeroot -b".

[flac_1.2.0-0local1.tar.gz]("ftp://ftp.tuebingen.mpg.de/kyb/towolf/flac_1.2.0-0local1.tar.gz")

---

### Post by fflarex on 2007-08-08
'which flac' returned /usr/local/bin/flac before I removed it (by means of 'make uninstall') to try your debian package. Here's the output when I try the debian source tarball you gave me:

```
dpkg-buildpackage: source package is flac
dpkg-buildpackage: source version is 1.2.0-0local1
dpkg-buildpackage: source changed by Tobias Wolf <towolf@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 1.2.0-0local1
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 4) nasm (>= 0.98.34-1) doxygen libid3-3.8.3-dev (>= 3.8.3-4.2) libogg-dev dpatch
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
```

---

### Post by hugmenot on 2007-08-08
Well, you need some build dependencies for building the package.
```
sudo apt-get build-dep flac 
```
should fix that.

---

### Post by fflarex on 2007-08-09
Thanks, everything's in working order now.

---

### Post by Aleksandersen on 2007-08-30
Google can die. Yahoo! Search gave me the answer (this thread) as result number one!

Thanks. ^^ By some odd reason I feel much better with the new version of FLAC on my system.

---

