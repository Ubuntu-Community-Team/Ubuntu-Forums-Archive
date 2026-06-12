---
title: "MPlayer dvdnav in gui - recognizes dvd images on disk as well."
date: 2011-08-28
forum: Multimedia Software
---

### Post by rickyrockrat on 2011-08-28
Hi,
Well, I've been frustrated with a GUI multi-media player. I like getting the previews, but when you back up your DVDs to disk, it seems mplayer has to be invoked from the command line - which is REALLY inconvienent if you just want to watch a movie, so I patched MPlayer to behave similar to VLC in that it recognizes DVD structures on disk, so when you do a dvdbackup -M, gmplayer will now play the DVD like it should.

NOTE: someone has written a very nice thread (except for the multiple commands thrown together) on this as well. You might try this:

[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Then you will have to split the single cd/svn/configure/make command up  so make is called all by itself.  You can split that command up by removing all the '&& \' from the lines.
 Run the patch command just before make, then add --enable-gui to the configure line. (*sigh*, nothing is ever simple.)

If not, read on.

You're going to have to use a terminal for this...

You need to bring in the mediubuntu repo:
```
sudo wget -O /etc/apt/sources.list.d/medibuntu.list 
  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
```
  sudo apt-get update
  sudo apt-get install medibuntu-keyring
  sudo apt-get update
  sudo apt-get upgrade

Now you will need to get the development headers like so: If you are running Lucid like I am, you'll have to build some of your own libs (see end of post for details)


```
sudo apt-get install libavcodec-extra-* libavdevice-extra-* libavfilter-extra-* \
  libavformat-extra-* libpostproc-extra-* libavutil-extra-*  \
  libdvdcss-dev libswscale-extra-* libdvdcss2 aacgain aacplusenc \
  alsa-firmware app-install-data-medibuntu apport-hooks-medibuntu \
  ices  non-free-codecs w64codecs libdvdnav4 libdvdread4 libdvdnav-dev \
  libdvdread-dev  liblircclient-dev lirc lirc-modules-source lirc-x \
 libmpcdec-dev libmp3lame-dev libmpeg2-4-dev libmpeg3-dev libmpg123-dev \
 libmp4v2-dev libmpeg4ip-dev libavc1394-dev libavcodec-dev libavdevice-dev \
 libavfilter-dev libavformat-dev libavutil-dev libpostproc-dev libswscale-dev \
 libavbin-dev libavifile-0.7-dev libvalhalla-dev libmpg123-0 libfaad-dev \
 libgsm1-dev libogg-dev libschroedinger-dev libspeex-dev libtheora-dev \
 libvorbis-dev libx11-dev libxext-dev zlib1g-dev libraw1394-dev \
 libdc1394-22-dev libavutil-dev libao-dev libflac-dev libmad0-dev libmad0-dev \
 libmtp-dev libnice-dev libsamplerate0-dev libsdl1.2-dev libspeexdsp-dev \
 libtagc0-dev libvorbis-dev libvorbisenc2 libvorbis0a libwavpack-dev \
 libxine-dev libxine1-ffmpeg libfaac-dev libvpx-dev libopenjpeg-dev \
 libdirac-dev libx264-dev libxvidcore-dev libdvd-dev libdv4-dev libdca-dev \
 liba52-0.7.4-dev libtwolame-dev liblzo2-dev  libdts-dev
```

Was that fun for you? There's lots of dependencies.

make a directory to do the rest:
mkdir build
cd build

Now, grab MPlayer source:
wget [http://www.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc4.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc4.tar.bz2)

Copy the attached patch (to build):
wget -O patch.txt [http://ubuntuforums.org/attachment.php?attachmentid=200988&d=1314561202](http://ubuntuforums.org/attachment.php?attachmentid=200988&d=1314561202)


Extract the source
tar -xjf ../MPlayer-1.0rc4.tar.bz2

Goto to the build directory
cd MPlayer-1.0rc4

Patch the source (note, if this is not a clean directory, use the exact name of the patch file)
patch -p1 < ../*.txt

Configure it:
./configure ./configure --enable-gui --enable-lirc 

Check the printout (scroll a couple pages up) to make sure you've got all the pieces you want enabled. It prints a list of enabled and disabled modules. 

Make it:
make

Install it (note: you can run w/out installing, just do ./mplayer -gui):
sudo make install-gui

Now when you Open File..., and browse to a directory that contains VIDEO_TS in it, mplayer assumes that you want to play a DVD, and it pops up a dialog asking if you want to NAV (i.e. DVD menus) or play title 1-5 (button for each). Title 1 is usually the main feature.  I need to go look at the DVD, scan the titles, then present the list, but for now it's hard-coded and will work for 90% of the cases.  

For Lucid,
Here are my notes and how I built each one. I also removed the -devs using apt (sudo apt-get remove libdvdread-dev libdvdnav-dev libx264-dev libdca-dev)

build Install libdvdread 4.1.x (use autogen.sh first, ./configure, make, make install)
build install libdvdnav 4.1.x  (use autogen.sh first, ./configure, make, make install)
build install x264x   ./configure --enable-shared --enable-static
build install libdca ./bootstrap, ./configure, make, make install

Links:
libdca -
[ftp://ftp5.uk.freebsd.org/pub/FreeBSD/ports/distfiles/libdca-0.0.5.tar.bz2](ftp://ftp5.uk.freebsd.org/pub/FreeBSD/ports/distfiles/libdca-0.0.5.tar.bz2)
[http://download.videolan.org/pub/videolan/libdca/0.0.5/libdca-0.0.5.tar.bz2](http://download.videolan.org/pub/videolan/libdca/0.0.5/libdca-0.0.5.tar.bz2)

libdvdnav -
[http://www.mplayerhq.hu/MPlayer/releases/dvdnav/libdvdread-4.1.3.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/dvdnav/libdvdread-4.1.3.tar.bz2)
[https://launchpadlibrarian.net/22760800/libdvdread_4.1.3.orig.tar.gz](https://launchpadlibrarian.net/22760800/libdvdread_4.1.3.orig.tar.gz)

libdvdread -
[http://www.mplayerhq.hu/MPlayer/releases/dvdnav/libdvdnav-4.1.3.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/dvdnav/libdvdnav-4.1.3.tar.bz2)
[https://launchpadlibrarian.net/22883494/libdvdnav_4.1.3.orig.tar.gz](https://launchpadlibrarian.net/22883494/libdvdnav_4.1.3.orig.tar.gz)

x264:
[ftp://ftp.videolan.org/pub/videolan/x264/snapshots/x264-snapshot-20110827-2245-stable.tar.bz2](ftp://ftp.videolan.org/pub/videolan/x264/snapshots/x264-snapshot-20110827-2245-stable.tar.bz2)

THEN build mplayer. Again, these are for lucid.

Cheers.

---

### Post by beew on 2011-08-29
Hi,

I am trying to build mplayer following your instruction. But I get stuck after ./configure --enable-gui
Here is the error 

> Checking for GTK+ version ... GTK-2 devel packages were not found, trying GTK 1.2
Checking for GTK version ... 
Error: The GUI requires GTK devel packages (which were not found).


I checked Synaptic and there seems to be many GTK related packages, I am not sure which one to install.  

Also, I have put the directory MPlayer-1.0rc4 inside the build directory, is it correct?

Thanks.

---

### Post by rickyrockrat on 2011-08-29
What Ubuntu version are you on? Try apt-get libgtk2.0-dev
Yes - that is mainly so you have a clean directory. It doesn't matter where you put it really.
It should look like:
build
[INDENT]MPlayer-1.0rc4.tar.bz2
  patch.txt (or whatever you called it)
  MPlayer-1.0rc4[/INDENT]
 
I'm having issues with DVDNav in Natty for some reason - it finds the menu page just fine, but it won't give me little white boxes, and seems to ignore the keypad keys - weird. It plays the DVD fine if you select, say Title1. I haven't given up on it yet - it *HAS* to work. It's the same code, same revision of libdvdnav/libdvdread, same patch. Argh.  I'll figure it out eventually.

But this patch *does* allow you to browse to a directory structure on the HDD and play a DVD like it was in the drive - without the command line.

---

### Post by beew on 2011-08-29
> **rickyrockrat said:**
> What Ubuntu version are you on? Try apt-get libgtk2.0-dev
Yes - that is mainly so you have a clean directory. It doesn't matter where you put it really.
It should look like:
build
[INDENT]MPlayer-1.0rc4.tar.bz2
  patch.txt (or whatever you called it)
  MPlayer-1.0rc4[/INDENT]
 
I'm having issues with DVDNav in Natty for some reason - it finds the menu page just fine, but it won't give me little white boxes, and seems to ignore the keypad keys - weird. It plays the DVD fine if you select, say Title1. I haven't given up on it yet - it *HAS* to work. It's the same code, same revision of libdvdnav/libdvdread, same patch. Argh.  I'll figure it out eventually.

But this patch *does* allow you to browse to a directory structure on the HDD and play a DVD like it was in the drive - without the command line.

Thanks, I will try that tonight when I go home.

I am on Natty. 

I am mostly using mplayer2 built from source with Umplayer as a gui front end. [http://www.mplayer2.org/comparison.html](http://www.mplayer2.org/comparison.html)

I have tried to enable dvd menu by checking the box in umplayer (its option layout is like Smplayer) and add the option 
> -mouse-movements -nocache dvdnav:// for mplayer options. The menu shows up (for some dvds) but there is no sound for some reason.

---

### Post by beew on 2011-08-29
Hi,

I installed libgtk2.0-dev (which pulled in a lot of other dependencies) and the build process went through smoothly. But I am still having a few problems and questions.

The build process created a mplayer gui .desktop file, but clicking it nothing happens.

 I tried gnome-mplayer with the mplayer binary set to the built version in the folder MPlayer1.0-rc4 to open a dvd and the menu shows up, but when I choose to actually play something, there was no sound.

I have a Nvidia card, the mplayer built here doesn't seem to support VDPAU. I tested with a video using the version of mplayer built here, cpu usage was at 80%, but with the system version of mplayer it was somewhere around 10% (installed from [https://launchpad.net/~longinus00/+archive/mplayer-mt]("https://launchpad.net/%7Elonginus00/+archive/mplayer-mt")) ,with mplayer2 cpu usage was around 5%.

What should I do if I want to update mplayer? If I want to remove it, should I just delete the build folder? It seems that sudo was invoked only to create the .desktop file for the MPlayer-gui in /usr/local/share/applications.

Thanks a lot for your help.

P.S.  There is a tutorial for building the svn version of MPlayer on the forum, does your patch work with that? [http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

---

### Post by rickyrockrat on 2011-08-29
Well, I knew Natty was screwed up, and now I know for sure.

I used the svn build (r34027), i.e. today's svn, which has a *completely* different structure, and built a patch for it as well.  I then built it on Lucid and Natty, Lucid works just fine, but Natty has a bad pointer on a free if do anything then exit. Gcc went from 4.4 to 4.5, and there's other people having issues with 4.5 as well:
[https://bbs.archlinux.org/viewtopic.php?pid=751716](https://bbs.archlinux.org/viewtopic.php?pid=751716)
So then I moved back to gcc-4.4 (remove gcc-4.5, then install gcc-4.4 g++-4.4 gcc-4.4libstd++6-4.4-dev libtool), re-compiled, then tried again. Same issue.  So then I grabbed the binary I built on Lucid and put it on Natty, fixed the libs that were missing, and the same thing happens on Natty with the binary from Lucid.  I suspect one of the libraries is very hosed on Natty.  I've attached a patch for the latest SVN
[mplayer.r34027.gui.dvdnav.patch.txt]("http://ubuntuforums.org/attachment.php?attachmentid=201073&stc=1&d=1314665912")

Sorry I wasted your time - though you can play DVDs with out the cmd line on Natty.
The DVDNAV doesn't fully work on Lucid, either, but at least the menu comes up and you can select whatever - but when you go to play the DVD, it does something weird. Same thing happens by doing -dvd-device dvdnav:// from the command line, so at least my code isn't bad.

I'm very interested in your results.

---

### Post by beew on 2011-08-29
Thanks for the explanations. So if I want to try your new patch with the new svn version what should I replace this line with?
> wget [http://www.mplayerhq.hu/MPlayer/rele...1.0rc4.tar.bz2]("http://www.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc4.tar.bz2")

I will try to build it in Natty in the weekend and let you know the result, though I am kind of hesitant to downgrade the gcc  packages as it may screw up other things. :(

There is no waste of time, even if it doesn't work I learn something from it. Besides, you are trying to contribute something, that is very kind of you. I hope I can do that one day when I learn enough. :)

Thanks again.

---

### Post by rickyrockrat on 2011-08-29
So don't downgrade GCC. That didn't fix the problem. I suggest following the other thread that builds from SVN.  A couple notes. He combines commands by doing && \, which is great if it all works, but it sucks if something goes wrong, then you have to tear the command apart.  See the top of the post where I updated what to change from his build.

To answer the question about wget, do a 
```
svn co -r 34027 svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```

This will give you a svn directory called mplayer. In this case, I suggest you use a separate build directory like this:
```
mkdir svn.patched
cd svn.patched
lndir ../mplayer

```
Then patch, configure, and build from here.  lndir is handy (in xutils-dev) because you can make changes in the svn dir that don't effect the svn co.  Very cool for building different builds on the same source.

Want to build something without the patch, create a directory like 
```

mkdir svn.clean
cd svn.clean
lndir ../mplayer
config,make, build.

```

No need to install, BTW, just do a ./mplayer -gui to run it in GUI mode for testing.

also, you should do a sudo make install-gui if you are going to install

---

