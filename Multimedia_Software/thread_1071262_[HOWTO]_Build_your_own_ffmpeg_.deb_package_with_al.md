---
title: "[HOWTO] Build your own ffmpeg .deb package with all codecs enabled"
date: 2009-02-16
forum: Multimedia Software
---

### Post by TrinitronX on 2009-02-16
Since the license does not enable me to redistribute the compiled debian binary package I have made, I will show you how to do it yourself.

**[COLOR=darkred]Q: Why would I want this?[/COLOR]**
[COLOR=green]**A:** Ubuntu's stock ffmpeg does not enable support for x264, xvid, 3gp, amr, faac, and even mp3!!
You need to build your own packages to enable support for files through the following libraries: libmp3lame, libxvid, libamrnb, libamrwb, libx264, libfaac[/COLOR]
**[COLOR=darkred]Q: Why can't you just give me a .deb file?[/COLOR]**
[COLOR=green]**A:** Enabling support for libamr-nb & libamr-wb in the source changes the license so I cannot redistribute it.  Basically a bunch of legal mumbo jumbo prevents me from just giving you a .deb.[/COLOR]

After this, you should be able to use ffmpeg to convert most any type of file :D

First install build environment packages:
```
sudo apt-get install build-essential devscripts ubuntu-dev-tools dh-make module-assistant cdbs debconf-utils fakeroot
```Next, follow this tutorial to add medibuntu sources to your sources.list file:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Now we can install some build dependencies for ffmpeg:
```
sudo apt-get install libamrnb-dev libamrwb-dev liba52-dev libdts-dev libgsm1-dev libvorbis-dev  libxvidcore4 libxvidcore-dev libdc1394-22-dev libfaac-dev libmp3lame-dev libx264-dev libfaad-dev libtheora-dev libsdl1.2-dev
```Now make your own src directory in your home dir:
```
cd ~
mkdir src
cd ~/src
```Grab the current ubuntu source file package:
```
apt-get source ffmpeg
```Change directory into ffmpeg-debian-*.  Apt will automatically unpack the .tar.gz file and apply the .diff.gz debian patches onto it.
This gives you a directory named something similar to: ffmpeg-debian-0.svn20080206
Yours may not be the same once this guide becomes outdated.
```
cd ffmpeg-debian-**INSERT_SOURCE_VERSION_HERE_OR_USE_TAB_COMPLETION**
```Now we are ready to grab some more build depends for ffmpeg:
```
sudo apt-get build-dep ffmpeg
```For me, these included:
doxygen libfreetype6-dev libgif-dev libimlib2-dev libjpeg62-dev libltdl7-dev
libpng12-dev libtiff4-dev libtiffxx0c2 libungif4-dev texi2html zlib1g-dev

So now we must uncomment some lines in debian/confflags:
```
vim debian/confflags
```Uncomment these lines:
```

# Uncomment the following lines to allow the use of nonfree code,
# the resulting packages will be unredistributable!
  weak-build-deps += libamrnb-dev
  confflags += --enable-nonfree --enable-libamr-nb
  weak-build-deps += libamrwb-dev
  confflags += --enable-nonfree --enable-libamr-wb

```Usually it is nice to update the debian/changelog file when you have changed a package.
We will use the --nmu option because it is a non-maintainer upload (we won't be uploading however).
This should also increment the version number for your soon-to-be-built .deb packages.
Replace your name/email in the variable set here:
```
export DEBEMAIL="Firstname Lastname <youremail@yourdomain.com>"
debchange --nmu "Enabled nonfree config flags, should enable libamr-nb, libamr-wb support"
```Now build your binary package without signing using the externalcodecs build option:
```
DEB_BUILD_OPTIONS="--enable-externalcodecs" debuild -rfakeroot -uc -us -b
```After this completes (hopefully successfully), you will see a bunch of .deb files in the directory above ffmpeg-debian-* (should be ~/src/ if you were following this guide fully)

You should be able to install these now using these commands:
```
cd ..
sudo dpkg -i libavcodec51*.deb libavdevice52*.deb libpostproc51*.deb libavformat52*.deb libavutil49*.deb libswscale0*.deb
sudo dpkg -i ffmpeg*.deb
```Note: if these file glob matches don't work for you, install each by hand, or **[COLOR=red]carefully[/COLOR]** try:
```
sudo dpkg -i *.deb
```That will install ALL files matching *.deb in your ~/src directory!  Assuming that the only ones you have are those we just created, then you should be fine.  Do note that this could also install some unnecessary development packages too, but it should be ok if you're not worrying about drive space.

You may now check your installed version of ffmpeg to see it's new enabled options!
```
trinitronx@saturn:~/src$ ffmpeg -version

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr--enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad **--enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-nonfree --enable-libamr-nb --enable-nonfree --enable-libamr-wb --enable-libmp3lame --enable-libfaac** --enable-gpl **--enable-libxvid** --enable-gpl **--enable-libx264** --enable-shared--disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb 15 2009 21:28:22, gcc: 4.3.2
FFmpeg r11872+debian_3:0.svn20080206-12ubuntu3.1
libavutil   3212800
libavcodec  3355136
libavformat 3409664
libavdevice 3407872
```Now you should be able to use ffmpeg to work on .3gp or .amr files like so:
```
ffmpeg -i Recording.amr -ar 22050 -acodec libmp3lame Recording.mp3
```ENJOY!  :popcorn:


For more examples of how to BUILD debian packages in this way, see:
[http://www.debian.org/doc/maint-guide/ch-build.en.html](http://www.debian.org/doc/maint-guide/ch-build.en.html)
[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)
[http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source](http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source)
[http://linuxdevices.com/articles/AT8047723203.html](http://linuxdevices.com/articles/AT8047723203.html)

For more examples of how to USE ffmpeg to do conversions, see:
[http://www.hiteshagrawal.com/ffmpeg/converting-audiovideos-using-ffmpeg](http://www.hiteshagrawal.com/ffmpeg/converting-audiovideos-using-ffmpeg)

---

### Post by abulyomon on 2009-04-18
Very useful. Thank you.

---

### Post by geoff123 on 2009-08-21
Thank You.  I've built source many times before, but doing it the "debian" way is very useful.  I was just able to set up the latest koala version of ffmpeg and jaunty libxine on my jaunty system using this info as a guide. This Geoff

---

### Post by CDrewing on 2010-05-05
Very nice, took 2 hrs on my P-IV 2G6Hz :popcorn:
But: Where is libxvid and h.264? :confused:

Best regards
Christian

---

### Post by mysoogal on 2010-09-18
> **CDrewing said:**
> Very nice, took 2 hrs on my P-IV 2G6Hz :popcorn:
But: Where is libxvid and h.264? :confused:

Best regards
Christian

here
in zip includes the following 

bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb
ffmpeg_4:SVN-r25135-1_i386.deb
lame-ffmpeg_3.98.4-1_i386.deb
libvpx_201009162100-git-1_i386.deb - VP8 encoder  :mrgreen: look into webm project  ;)
qt-faststart_4:SVN-r25135-1_i386.deb
x264_2:0.104.1713+gitc276662-1_i386.deb

[link]("http://www.megaupload.com/?d=OU1MBTRT")

patent trolls 
get a life :popcorn:

---

