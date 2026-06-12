---
title: "VLC with ffmpeg can't transcode MPEG4."
date: 2009-12-29
forum: Multimedia Software
---

### Post by dr_latino999 on 2009-12-29
I have been trying to compile a version of VLC which would correctly stream and transcode media with the settings of MPEG4 + AAC (video/audio). The normal response from package versions is the following:

```
  p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]VLC could not open the encoder.[/COLOR]

```Ok, so using the a guide constructed by one of the VLC devs I created a script to install and compile everything under the sun necessary for VLC in 9.04.

```
#!/bin/bash
#
# http://juliensimon.blogspot.com/2008/12/howto-compiling-ffmpeg-x264-mp3-xvid.html
mkdir /opt/build
cd /opt/build/
apt-get install subversion git git-core -y
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
apt-get update
apt-get install medibuntu-keyring --force-yes -y
apt-get update
apt-get install libgpac-dev nasm libfaac-dev libfaac0 libfaad-dev libfaad0 libschroedinger-dev libtheora-dev libtheora0 libvorbis-dev libvorbis0a libvorbisenc2 libvorbisfile3 libxv-dev libxvmc-dev libmp3lame-dev libmp3lame0 libgsm-tools libgsmme-dev libdirac-dev libdirac0c2a libdc1394-13 libdc1394-13-dev libopenjpeg-dev libopenjpeg2 libspeex-dev libspeex1 libspeexdsp-dev libspeexdsp1 libamrnb-dev libamrwb-dev g++ libavc1394-dev libraw1394-dev libdc1394-13-dev libdvdread-dev libdvdnav-dev libdvdcss2 libdvdcss-dev libfaad-dev libtwolame-dev liba52-dev libvcdinfo-dev libiso9660-dev libcddb2-dev libflac-dev libogg-dev libvorbis-dev liblua5.1-0-dev libgnomevfs2-dev libtag1-dev libqt4-dev libfribidi-dev libhal-dev libmtp-dev libshout3-dev libdvbpsi5 libdvbpsi5-dev libv4l-dev zvbi libzvbi-dev libpulse-dev libxcb-keysyms0-dev --force-yes -y
apt-get upgrade -y
wget http://transact.dl.sourceforge.net/project/opencore-amr/opencore-amr/0.1.2/opencore-amr-0.1.2.tar.gz
tar xvf opencore-amr-0.1.2.tar.gz
rm opencore-amr-0.1.2.tar.gz
cd opencore-amr-0.1.2
./configure
make
#checkinstall --fstrans=no --install=yes --pkgname="libopencore-amr" --pkgversion="0.1.2" --backup=no --default
#ldconfig
make install
cd ..
wget http://www.tortall.net/projects/yasm/releases/yasm-0.7.2.tar.gz
tar xvfz yasm-0.7.2.tar.gz
rm yasm-0.7.2.tar.gz
cd yasm-0.7.2
./configure --prefix=/usr/local
make
sudo make install
cd ..
svn co svn://svn.mplayerhq.hu/nut/src/trunk/ nut
cd nut
make
make install
cd ..
git clone git://git.videolan.org/x264.git
cd x264
./configure --prefix=/usr/local --enable-shared
make
#checkinstall --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`" --backup=no --default
make install
cd ..
wget http://downloads.xvid.org/downloads/xvidcore-1.2.2.tar.gz
tar xvfz xvidcore-1.2.2.tar.gz
rm xvidcore-1.2.2.tar.gz
cd xvidcore/build/generic
./configure --prefix=/usr/local
make
make install
cd ..
cd ..
cd ..
cd ffmpeg
./configure --prefix=/usr/local --enable-gpl --enable-nonfree --enable-shared --enable-postproc --enable-avfilter --enable-avfilter-lavf --enable-pthreads --enable-x11grab --enable-bzlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libmp3lame --enable-libnut --enable-libschroedinger --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib
#--enable-libtheora
# --enable-libgsm 
make
make install
cd ..
LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
ldconfig
# http://juliensimon.blogspot.com/2009/04/howto-compiling-vlc-099-live555-all.html
cd /opt/build/
wget http://ovh.dl.sourceforge.net/sourceforge/mad/libmad-0.15.1b.tar.gz
tar xvfz libmad-0.15.1b.tar.gz
rm libmad-0.15.1b.tar.gz
cd libmad-0.15.1b
./configure --prefix=/usr/local
#
cp /home/edwin/Desktop/Makefile /opt/build/libmad-0.15.1b/Makefile
#
make
make install
cd ..
wget http://download.videolan.org/pub/videolan/libdca/0.0.5/libdca-0.0.5.tar.bz2
bzip2 -d libdca-0.0.5.tar.bz2
tar xvf libdca-0.0.5.tar
rm libdca-0.0.5.tar
cd libdca-0.0.5
./configure --prefix=/usr/local
make
make install
cd ..
wget http://libmpeg2.sourceforge.net/files/libmpeg2-0.5.1.tar.gz
tar xvfz libmpeg2-0.5.1.tar.gz
rm libmpeg2-0.5.1.tar.gz
cd libmpeg2-0.5.1
./configure --prefix=/usr/local
make
make install
cd ..
wget http://developer.kde.org/~wheeler/files/src/taglib-1.5.tar.gz
tar xvfz taglib-1.5.tar.gz
rm taglib-1.5.tar.gz
cd taglib-1.5
./configure --prefix=/usr/local
make
make install
cd ..
wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
tar xvfz live555-latest.tar.gz
rm live555-latest
cd live
./genMakefiles linux
make
cd ..
cp -r live /usr/lib
wget http://get.qt.nokia.com/qt/source/qt-everywhere-opensource-src-4.6.0.tar.gz
tar xvf qt-everywhere-opensource-src-4.6.0.tar.gz
rm qt-everywhere-opensource-src-4.6.0.tar.gz
cd qt-everywhere-opensource-src-4.6.0/
./configure
make
make install
cd ..
wget http://download.videolan.org/pub/videolan/vlc/1.0.4/vlc-1.0.4.tar.bz2
bzip2 -d vlc-1.0.4.tar.bz2
tar xvf vlc-1.0.4.tar
rm vlc-1.0.4.tar
cd vlc-1.0.4
cp -r /opt/build/ffmpeg extras
cp -r /opt/build/x264 extras
cp -r /usr/lib/live extras
ls extras
./configure --prefix=/usr/local --with-x264-tree=extras/x264 --with-live555-tree=extras/live --enable-release --enable-switcher --enable-shout --enable-dc1394 --enable-dv --enable-dvdread --enable-v4l --enable-pvr --enable-gnomevfs --enable-vcdx --enable-faad --enable-twolame --enable-real --enable-realrtsp --enable-flac --enable-tremor --enable-tarkin --enable-theora --enable-ogg --enable-vorbis --enable-a52 --enable-gnomevfs --enable-dca
make
make install
```When I run this script (and come back 8 hours later), VLC is compiled but it crashes on playback of a test .avi.

Main point and question being, what do I have to do to enable VLC to stream and transcode any media into the MPEG4 + AAC format?

BTW, I have tried this thread --> [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) with a fresh install on 9.10 and still no dice.

---

### Post by FakeOutdoorsman on 2009-12-29
As an alternative to compiling VLC, did you try the repository VLC with the **libavcodec-unstripped-52** package?  Although I'm not too familiar with VLC, I believe it will enable encoding to some restricted formats including MPEG-4 and AAC.

---

### Post by dr_latino999 on 2009-12-29
I have tried it, but that was no dice. What does seem to hold me up is that MPEG works if you change the sound away from AAC. I'll get back to you on if I have AAC support after the latest compile.

---

### Post by HappyFeet on 2009-12-29
What version of vlc are you trying to install?

---

### Post by dr_latino999 on 2009-12-29
> **HappyFeet said:**
> What version of vlc are you trying to install?

1.0.4 was the original intention, but for testing of the script to iron out stability bugs I'm falling back on 1.0.0.

---

### Post by HappyFeet on 2009-12-29
> **dr_latino999 said:**
> 1.0.4 was the original intention, but for testing of the script to iron out stability bugs I'm falling back on 1.0.0.

I just installed 1.0.4 via PPA, and it works great.

---

### Post by SuperSonic4 on 2009-12-29
What happens if you compile with ```
sudo mkdir /opt/vlc
```
```
./configure  '--prefix=/opt/vlc' '--program-suffix=-git' '--enable-static=x264' '--enable-dbus' '--enable-run-as-root' '--enable-dvdread' '--enable-dvdnav' '--disable-smb' '--enable-pvr' '--enable-cddax' '--enable-libcddb' '--enable-mkv' '--enable-ogg' '--enable-merge-ffmpeg' '--enable-faad' '--disable-twolame' '--enable-real' '--enable-a52' '--enable-flac' '--enable-libmpeg2' '--enable-vorbis' '--enable-theora' '--enable-png' '--enable-x264' '--enable-libass' '--disable-fribidi' '--enable-caca' '--enable-pulse' '--enable-alsa' '--enable-qt4' '--enable-ncurses' '--disable-bonjour' '--enable-udev' '--enable-mtp' '--with-x' 'PKG_CONFIG_PATH=/usr/lib/pkgconfig'
```

and then ```
make
```
```
sudo make install
```

This will install VLC as vlc-git to /opt/vlc/bin/vlc-git independent of any repo version

---

### Post by e-Gee on 2009-12-29
You have to install [B]libavcodec-unstripped-52  but from medibuntu repository, thet works for me
[/B]

---

### Post by FakeOutdoorsman on 2009-12-29
> **dr_latino999 said:**
> I have tried it, but that was no dice. What does seem to hold me up is that MPEG works if you change the sound away from AAC. I'll get back to you on if I have AAC support after the latest compile.

I was assuming that you were using 9.04, not 9.10.  The libavcodec-unstripped-52 package in the Karmic repository does not support AAC encoding, but the version from Medibuntu that e-Gee mentioned does support AAC encoding (the Medibuntu libavcodec-unstripped-52 package is only available for Karmic users).  For more details see option C in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by dr_latino999 on 2009-12-29
> **FakeOutdoorsman said:**
> I was assuming that you were using 9.04, not 9.10.  The libavcodec-unstripped-52 package in the Karmic repository does not support AAC encoding, but the version from Medibuntu that e-Gee mentioned does support AAC encoding (the Medibuntu libavcodec-unstripped-52 package is only available for Karmic users).  For more details see option C in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283")

No dice on the link as I mentioned before, in particular the unstripped-52 package tries to erase my newly compiled ffmpeg.

[SIZE=4]**Play by Play**[/SIZE]
Here is a play by play of exactly what the script is doing when run under 9.04 when attempting to create a complete (all bells and whistles) VLC installation.:


[LIST=1]
[*]Creates the build directory, which was arbitrary, and declare which version of VLC I would like to try and build. At the same time, the latest ffmpeg is pulled down ```
vlcver=1.0.0
mkdir /opt/build
cd /opt/build/
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg

```
[*]I then enable the Medibuntu repository. ```
wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
apt-get update
apt-get install medibuntu-keyring --force-yes -y
apt-get update

```
[*]Install ALL the packages that this will require, then checking one last time that I didn't miss anything. ```
apt-get install subversion git git-core libgpac-dev nasm libfaac-dev libfaac0 libfaad-dev libfaad0 libschroedinger-dev libtheora-dev libtheora0 libvorbis-dev libvorbis0a libvorbisenc2 libvorbisfile3 libxv-dev libxvmc-dev libmp3lame-dev libmp3lame0 libgsm-tools libgsmme-dev libdirac-dev libdirac0c2a libdc1394-13 libdc1394-13-dev libopenjpeg-dev libopenjpeg2 libspeex-dev libspeex1 libspeexdsp-dev libspeexdsp1 libamrnb-dev libamrwb-dev g++ libavc1394-dev libraw1394-dev libdc1394-13-dev libdvdread-dev libdvdnav-dev libdvdcss2 libdvdcss-dev libfaad-dev libtwolame-dev liba52-dev libvcdinfo-dev libiso9660-dev libcddb2-dev libflac-dev libogg-dev libvorbis-dev liblua5.1-0-dev libgnomevfs2-dev libtag1-dev libqt4-dev libfribidi-dev libhal-dev libmtp-dev libshout3-dev libdvbpsi5 libdvbpsi5-dev libv4l-dev zvbi libzvbi-dev libpulse-dev libxcb-keysyms0-dev --force-yes -y
apt-get upgrade -y
```
[*]I then instal[COLOR=Black]l libopencore-amr [/COLOR]```
[URL="http://ubuntuforums.org/showthread.php?t=1117283"][COLOR=Black]wget http://transact.dl.sourceforge.net/project/opencore-amr/opencore-amr/0.1.2/opencore-amr-0.1.2.tar.gz
tar xvf opencore-amr-0.1.2.tar.gz
rm opencore-amr-0.1.2.tar.gz
cd opencore-amr-0.1.2
./configure
make
#checkinstall --fstrans=no --install=yes --pkgname="libopencore-amr" --pkgversion="0.1.2" --backup=no --default
#ldconfig
make install
cd ..[/COLOR][/URL]
```
[*]Next yasm is compiled to have the almost newest version. ```
wget http://www.tortall.net/projects/yasm/releases/yasm-0.7.2.tar.gz
tar xvfz yasm-0.7.2.tar.gz
rm yasm-0.7.2.tar.gz
cd yasm-0.7.2
./configure --prefix=/usr/local
make
sudo make install
cd ..

```
[*]Nut is downloaded and installed ```
svn co svn://svn.mplayerhq.hu/nut/src/trunk/ nut
cd nut
make
make install
cd ..

```
[*]x264 is pulled down for installation. ```
cd ..
git clone git://git.videolan.org/x264.git
cd x264
./configure --prefix=/usr/local --enable-shared
make
make install
cd ..

```
[*]Xvid is pulled down and installed. ```
wget http://downloads.xvid.org/downloads/xvidcore-1.2.2.tar.gz
tar xvfz xvidcore-1.2.2.tar.gz
rm xvidcore-1.2.2.tar.gz
cd xvidcore/build/generic
./configure --prefix=/usr/local
make
make install
cd ..
cd ..
cd ..
```
[*]FFmpeg is installed with all the options under the sun. ```
cd ffmpeg
./configure --prefix=/usr/local --enable-gpl --enable-nonfree --enable-shared --enable-postproc --enable-avfilter --enable-avfilter-lavf --enable-pthreads --enable-x11grab --enable-bzlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libmp3lame --enable-libnut --enable-libschroedinger --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib
#--enable-libtheora
# --enable-libgsm 
make
make install
cd ..
LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
ldconfig

```
[*]Libmad is built. ```
cd /opt/build/
wget http://ovh.dl.sourceforge.net/sourceforge/mad/libmad-0.15.1b.tar.gz
tar xvfz libmad-0.15.1b.tar.gz
rm libmad-0.15.1b.tar.gz
cd libmad-0.15.1b
./configure --prefix=/usr/local
#
cp /home/edwin/Desktop/Makefile /opt/build/libmad-0.15.1b/Makefile
#
make
make install
cd ..
``` You will notice I have to copy the Makefile from the desktop. Basically there is an error in this makefile that requires manual editing, I can't remember what it is off the top of my head.
[*]Libdca is compiled. ```
wget http://download.videolan.org/pub/videolan/libdca/0.0.5/libdca-0.0.5.tar.bz2
bzip2 -d libdca-0.0.5.tar.bz2
tar xvf libdca-0.0.5.tar
rm libdca-0.0.5.tar
cd libdca-0.0.5
./configure --prefix=/usr/local
make
make install
cd ..
```
[*]Libmpeg is compiled. ```
wget http://libmpeg2.sourceforge.net/files/libmpeg2-0.5.1.tar.gz
tar xvfz libmpeg2-0.5.1.tar.gz
rm libmpeg2-0.5.1.tar.gz
cd libmpeg2-0.5.1
./configure --prefix=/usr/local
make
make install
cd ..

```
[*]Taglib is compiled. ```
wget http://developer.kde.org/~wheeler/files/src/taglib-1.5.tar.gz
tar xvfz taglib-1.5.tar.gz
rm taglib-1.5.tar.gz
cd taglib-1.5
./configure --prefix=/usr/local
make
make install
cd ..

```
[*]Live555 is compiled. ```
wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
tar xvfz live555-latest.tar.gz
rm live555-latest
cd live
./genMakefiles linux
make
cd ..
cp -r live /usr/lib

```
[*]The next part is optional. During VLC compiling it warns that QT must be updated. I tried to update it and it took 6 hours :-({|=. And I still don't think it registered properly. ```
#wget http://get.qt.nokia.com/qt/source/qt-everywhere-opensource-src-4.6.0.tar.gz
#tar xvf qt-everywhere-opensource-src-4.6.0.tar.gz
#rm qt-everywhere-opensource-src-4.6.0.tar.gz
#cd qt-everywhere-opensource-src-4.6.0/
#./configure
#make
#make install
```
[*]I then download the version of VLC I am trying to build and then proceed to attempt to build it with all the bells and Whistles. ```
wget http://download.videolan.org/pub/videolan/vlc/$vlcver/vlc-$vlcver.tar.bz2
bzip2 -d vlc-$vlcver.tar.bz2
tar xvf vlc-$vlcver.tar
rm vlc-$vlcver.tar
cd vlc-$vlcver
cp -r /opt/build/ffmpeg extras
cp -r /opt/build/x264 extras
cp -r /usr/lib/live extras
cp ~/Desktop/x264.c /opt/vlc-$vlcver/modules/codec/x264.c
ls extras
./configure --prefix=/usr/local --with-x264-tree=extras/x264 --with-live555-tree=extras/live --enable-release --enable-switcher --enable-shout --enable-dc1394 --enable-dv --enable-dvdread --enable-v4l --enable-pvr --enable-gnomevfs --enable-vcdx --enable-faad --enable-twolame --enable-real --enable-realrtsp --enable-flac --enable-tremor --enable-tarkin --enable-theora --enable-ogg --enable-vorbis --enable-a52 --enable-gnomevfs --enable-dca
make
make install
```
[/LIST]
When all is said and done, VLC working is spotty at best. All commands were sourced from [http://ubuntuforums.org/showpost.php?p=8345112&postcount=636](http://ubuntuforums.org/showpost.php?p=8345112&postcount=636), [http://juliensimon.blogspot.com/2008/12/howto-compiling-ffmpeg-x264-mp3-xvid.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-ffmpeg-x264-mp3-xvid.html), and with modifications [http://juliensimon.blogspot.com/2009/04/howto-compiling-vlc-099-live555-all.html](http://juliensimon.blogspot.com/2009/04/howto-compiling-vlc-099-live555-all.html).

The overall goal at the end of the day is to have VLC do this:
[img]http://farm3.static.flickr.com/2757/4225983313_2da57a1a0b.jpg[/img]

Without presenting this error message:
[img]http://farm3.static.flickr.com/2521/4225983379_b82de7aec9_o.png[/img]

---

### Post by andrew.46 on 2009-12-29
Hi dr_latino,

> **dr_latino999 said:**
> I have tried it, but that was no dice. What does seem to hold me up is that MPEG works if you change the sound away from AAC.

Have you checked that your copy of FFmpeg *definitely* supports aac encoding? 

```
ffmpeg -codecs | grep 'aac'
```

BTW keep up the good work, a fully featured vlc is a difficult one to compile :).

Andrew

**Edit:** oops, just noticed that my own compiled vlc 1.0.4 fails with the same message :(. Not compiled under Ubuntu though.... Perhaps mc4man could comment here?

---

### Post by mc4man on 2009-12-30
Can't help you out with the udp streaming but there should be no issue with vlc encoding mpeg4 and aac ( a quick test to file using mpeg4 and for the heck of it h.264 goes fine. ( attached file info - sorry about .txt - r. click 'save as is best if interested.

Andrew - I'd ck. vlc -vv and see if any plugins aren't being loaded (usually in yellow

dr_latino999 - While I'm not at a loss as what to say it's a bit late and I think many of my posts are too long anyway.

I think your making something that's ultimately not that complicated way too much so.
I'd venture to think you could eliminate at least 6 of your steps ( 1, 10-13, 15) and some of the others done a bit differently.

Personally I build ffmpeg statically into vlc, ala mplayer, though others may disagree. ( the same goes for any other library specifically built for vlc and or ffmpeg - I don't want to have to maintain and keep track of dependencies with them.

this doesn't do anything useful
> cp -r /opt/build/ffmpeg extras

And some other minor stuff.

Here's a post with some very basic tips, may or may not be of any value to you.

[http://ubuntuforums.org/showthread.php?t=786095&page=78](http://ubuntuforums.org/showthread.php?t=786095&page=78) # 776

Another thing you may want to keep in mind, - there is no guarantee the current versions of some libs, particularly actively updated ones like x264 and ffmpeg will work correctly with any one version of vlc, vlc 1.0.0 was released quite some time ago.

( I find if one is building vlc more than once or so that for releases a debian package set is much better and easier to maintain. For the 1.1 git a make install is atm the way to go.

edit:
actually taking a closer look at vlc's x264 encode it did screw it up, though the audio's fine and  the video looks fine the time is  too short. (is an anime so didn't notice at quick glance though can't see using vlc for that anyway, ffmpeg does the same file perfectly

---

### Post by andrew.46 on 2009-12-30
Hi mc4man,

> **mc4man said:**
> For the 1.1 git a make install is atm the way to go.

Not for the first time I have to thank you :). I have scavenged enough information from many of your posts to compile a very fully featured git vlc under Karmic Koala. Now if I could just work out where the icon has gone from the menu...

Thanks again!! I have a bit more work to do on the installation but the basics are now all in place.

Andrew

**Edit:** OIC, desktop icons not picked up in /usr/local/share/vlc .... an easy fix :)

---

### Post by mc4man on 2009-12-30
lots of ways to add the icon from 'edit menus' -> S & V -> vlc -> properties

Probably the easiest is just grab one (32x32..?) and drop it into documents folder and then add from properties (easy to find

To add directly from git source from the 'add icon' in properties browse to vlc-git source folder/vlc/share and you won't see any icons, but click on open anyway. (non-intuitive

Then you'll see them all in the add screen, pick one (.png I think is best

*- I see still hanging onto the that excedrine clip - actually  still have also...


Edit - I see it does install them to /local/share/, haven't installed a git for a while, just ck from build folder w/ ./vlc - am curious if they'll ever fix the loader properly

---

### Post by andrew.46 on 2009-12-30
Hi mc4man,

> **mc4man said:**
> lots of ways to add the icon from 'edit menus' -> S & V -> vlc -> properties

An easy one to sort :).

> *- I see still hanging onto the that excedrine clip - actually  still have also...

I am a bit of a squirrel with some things and this little clip amused me somewhat :).

A quick question, at the risk of hijacking this thread... I compiled x264 and FFmpeg as per the Fakeoutdoorsman's guide and installed to the system. But I subsequently installed x264 with '--with-x264-tree=' to a *local* copy and the idea of doing the same with FFmpeg is quite appealing, + the newer libass and a few others. Have you managed to use a 'local' copy of FFmpeg rather than the system one? I monkeyed around for some time with:

```
export PKG_CONFIG_PATH=/home/you/ffmpeg/
```

with no meaningful results... Certainly the slackbuild I use does something similar and does not even build FFmpeg, FFplay or FFserver. Installation itself I have cobbled together the old checkinstall syntax:

```
sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes --pkgname vlc \
	--pkgversion "1.1.0-`date +%Y%m%d`" --deldesc=yes --delspec=yes --default
```

which will hopefully remove old version and install new, I have not tested it much yet.

All the best,

Andrew

---

### Post by mc4man on 2009-12-30
> Have you managed to use a 'local' copy of FFmpeg rather than the system one
you can't use a tree option for ffmpeg, but you can use a PKG_CONFIG_PATH=

I've never done so. have seen examples so shouldn't be hard to sort out, though I think it still needs to be installed somewhere

The reason I just build static to /usr/local  - 

My approach is that a static ffmpeg build isn't the system ffmpeg ( equating that with the shared ffmpeg libs in /usr)
So using a static ffmpeg build for vlc does the same thing as what you might call local, it can stay installed, be removed,  up or downgraded after the build with no effect on vlc. (Basically what mplayer does, only they provide the source on checkout.

Considering the ease of installing/changing a checkinstalled ffmpeg package it makes sense to do that way. ( for me that is, meaning I already may have it built and installed, or stored with a matching x264 as small packages..

So vlc can either be built off of the current installed ffmpeg or in a few sec's it can be replaced with another one.

For other libs that won't have any value to already installed or repo apps than the --with-tree option is ideal, though again a build/install as static achieves the same thing (in most cases

In terms of a how to I'd think what is the most straightforward way  that doesn't represent any chance of breaking repo apps and possibly also other builds that may use some of the same libs. ( but may or may not benefit from the versions used.






 .

---

### Post by dr_latino999 on 2009-12-30
> **andrew.46 said:**
> 

Have you checked that your copy of FFmpeg *definitely* supports aac encoding? 

```
ffmpeg -codecs | grep 'aac'
```BTW keep up the good work, a fully featured vlc is a difficult one to compile :).

Andrew


Andrew, I checked FFmpeg and the output was the following:

```

edwin@US904-32:~/Desktop$ ffmpeg -codecs|grep 'aac'
FFmpeg version SVN-r20969, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Dec 29 2009 17:55:32 with gcc 4.3.3
  configuration: --prefix=/usr/local --enable-gpl --enable-nonfree --enable-shared --enable-postproc --enable-avfilter --enable-avfilter-lavf --enable-pthreads --enable-x11grab --enable-bzlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libmp3lame --enable-libnut --enable-libschroedinger --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib
  libavutil     50. 7. 0 / 50. 7. 0
  libavcodec    52.45. 0 / 52.45. 0
  libavformat   52.44. 0 / 52.44. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.12. 0 /  1.12. 0
  libswscale     0. 7. 2 /  0. 7. 2
  libpostproc   51. 2. 0 / 51. 2. 0
 DEA    aac             Advanced Audio Coding
  EA    libfaac         libfaac AAC (Advanced Audio Codec)

```[quote=mc4man]dr_latino999 - While I'm not at a loss as what to say it's a bit late and I think many of my posts are too long anyway.

I think your making something that's ultimately not that complicated way too much so.
I'd venture to think you could eliminate at least 6 of your steps ( 1, 10-13, 15) and some of the others done a bit differently. [/quote]
I don't doubt I am doing it the hard way currently, but I guess its the way I learn. If I do it the right way even if it is long I can learn how to pull what is unneeded later. Don't get me wrong though, if an easy "do it this way" manual existed for a full and complete VLC install I would gladly tip my hat to it and use it. #15 is commented out because I believe the warning message about qt needing updated is just an arbitrary message.

[quote=mc4man]Another thing you may want to keep in mind, - there is no guarantee the current versions of some libs, particularly actively updated ones like x264 and ffmpeg will work correctly with any one version of vlc, vlc 1.0.0 was released quite some time ago.[/quote] Noted, I will move up the version back to 1.0.3 and report back my findings. The UDP portion is just why I am wanting the transcode feature to work, as I am looking to catch a network stream (multicast) and then transcode it down in bandwidth for another lower bandwidth multicast. Rinse and repeat 63 times and I would have a full IPTV solution that doesn't fully saturate a 1-Gig network.

[quote=Andrew.46]A quick question, at the risk of hijacking this thread...[/quote] Never a concern, the more information that starts flowing the better.


[SIZE=3]Report: Build 1.0.0 Results
[/SIZE]
[LIST=1]
[*]Installed into the apps menu, sans icon. Link in menu works
[*]Tested Avi file, colors came out just plain wrong
[*] [IMG]http://farm5.static.flickr.com/4004/4228479778_6b3174d4a2_o.png[/IMG]
[*]Transcoding failed as before.
[*][img]http://farm3.static.flickr.com/2521/4225983379_b82de7aec9_o.png[/img]
[*]Will report back with 1.0.1, 1.0.2, 1.0.3, and 1.0.4. Tedious but it's research that occurs in ESX so I can just flip back and forth.
[/LIST]

---

### Post by dr_latino999 on 2009-12-30
My results:

1.0.1
1. Will not open from link on apps
2. Crashes when asked to play .avi locally
3. VLC Could not open the encoder.

1.0.2
1 . Same as 1.0.1

1.0.3
1. Will not open from link on apps
2. Crashes when asked to play .avi locally
3. VLC crashes when asked to stream

1.0.4
1. Same as 1.0.3

I want to solve this before next year, but it's doubtful.

---

### Post by andrew.46 on 2009-12-30
Hi mc4man,

> **mc4man said:**
> you can't use a tree option for ffmpeg, but you can use a PKG_CONFIG_PATH=

I've never done so. have seen examples so shouldn't be hard to sort out, though I think it still needs to be installed somewhere

After some investigation I have managed to get this working although the fine details still need a bit of work. I compiled FFmpeg as follows:

```

$ ./configure --prefix=$HOME/vlc_build/ffmpeg-build \
--enable-gpl --enable-version3 --enable-nonfree --enable-postproc \
--enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame \
--enable-libopencore-amrnb --enable-libopencore-amrwb \
--disable-ffmpeg --disable-ffplay --disable-ffserver --disable-doc
$ make jobs=2
$ make install-libs install-headers

```

and then ran the vlc configure as follows:

```

$ export PKG_CONFIG_PATH="$HOME/vlc_build/ffmpeg-build/lib/pkgconfig"
$ ./bootstrap
$ ./configure --prefix=/usr \
	--with-live555-tree=../live \
         --with-x264-tree=../x264 etc etc

```

This works well and has a definite 'neat' factor to it I think :).

Andrew

---

### Post by mc4man on 2009-12-30
> 
1.0.4
1. Same as 1.0.3

Maybe start vlc from the terminal with just this and see what it says. ( you could also add /path/to/a/file to the command. Note the output is potentially very large but anything relevant will probably show up early

```
vlc -vvv
```
You could also try the same eliminating qt by 

```
cvlc -vvv /path/to/a/file
```


> 
This works well....

looks good, what users of the how to can keep in mind, if you can build the 1.1-git, then one could also build a release using the same method. May be of interest to some you aren't 'interested' in the ups and downs of 1.1

Though 1.1 has alot going for it and there's always the next days git..

---

### Post by dr_latino999 on 2010-01-04
> **mc4man said:**
> 
```
vlc -vvv
```You could also try the same eliminating qt by


Test 1: VLC 1.0.0
Opening 30 Rock test file to play locally.

```
edwin@US904-32:/usr/local/bin$ vlc -vvv
VLC media player 1.0.0 Goldeneye
[0x9a69140] main libvlc debug: VLC media player - version 1.0.0 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x9a69140] main libvlc debug: libvlc was configured with ./configure  '--prefix=/usr/local' '--with-x264-tree=extras/x264' '--with-live555-tree=extras/live' '--enable-release' '--enable-switcher' '--enable-shout' '--enable-dc1394' '--enable-dv' '--enable-dvdread' '--enable-v4l' '--enable-pvr' '--enable-vcdx' '--enable-faad' '--enable-twolame' '--enable-real' '--enable-realrtsp' '--enable-flac' '--enable-tremor' '--enable-tarkin' '--enable-theora' '--enable-ogg' '--enable-vorbis' '--enable-a52' '--enable-gnomevfs' '--enable-dca'
[0x9a69140] main libvlc debug: translation test: code is "C"
[0x9a69140] main libvlc debug: checking plugin modules
[0x9a69140] main libvlc debug: loading plugins cache file /home/edwin/.cache/vlc/plugins-04041e.dat
[0x9a69140] main libvlc debug: recursively browsing `/usr/local/lib/vlc'
[0x9a69140] main libvlc warning: cannot load module `/usr/local/lib/vlc/demux/liblive555_plugin.so' (/usr/local/lib/vlc/demux/liblive555_plugin.so: undefined symbol: _Z6strDupPKc)
[0x9a69140] main libvlc debug: module bank initialized (374 modules)
[0x9a69140] main libvlc debug: opening config file (/home/edwin/.config/vlc/vlcrc)
[0x9a69140] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU
[0x9a69140] main libvlc debug: looking for memcpy module: 3 candidates
[0x9a69140] main libvlc debug: using memcpy module "memcpymmxext"
[0x9b08210] main input debug: Creating an input for 'Media Library'
[0x9b08210] main input debug: Input is a meta file: disabling unneeded options
[0x9b08210] main input debug: using timeshift granularity of 50 MBytes
[0x9b08210] main input debug: using timeshift path '/tmp'
[0x9b08210] main input debug: `file/xspf-open:///home/edwin/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/edwin/.local/share/vlc/ml.xspf'
[0x9b08210] main input debug: creating demux: access='file' demux='xspf-open' path='/home/edwin/.local/share/vlc/ml.xspf'
[0x9b19380] main demux debug: looking for access_demux module: 1 candidate
[0x9b19380] main demux warning: no access_demux module matching "file" could be loaded
[0x9b19380] main demux debug: TIMER module_need() : 2.012 ms - Total 2.012 ms / 1 intvls (Avg 2.012 ms)
[0x9b08210] main input debug: creating access 'file' path='/home/edwin/.local/share/vlc/ml.xspf'
[0x9b199f8] main access debug: looking for access module: 3 candidates
[0x9b199f8] access_file access debug: opening file `/home/edwin/.local/share/vlc/ml.xspf'
[0x9b199f8] main access debug: using access module "access_file"
[0x9b199f8] main access debug: TIMER module_need() : 14.398 ms - Total 14.398 ms / 1 intvls (Avg 14.398 ms)
[0x9b1a248] main stream debug: Using AStream*Stream
[0x9b1a248] main stream debug: pre buffering
[0x9b1a248] main stream debug: received first data after 0 ms
[0x9b1a248] main stream debug: pre-buffering done 296 bytes in 0s - 4817 kbytes/s
[0x9b0af98] main stream debug: looking for stream_filter module: 4 candidates
[0x9b0af98] main stream debug: TIMER module_need() : 1.824 ms - Total 1.824 ms / 1 intvls (Avg 1.824 ms)
[0x9b0d0f8] main stream debug: looking for stream_filter module: 1 candidate
[0x9b0d0f8] main stream debug: using stream_filter module "stream_filter_record"
[0x9b0d0f8] main stream debug: TIMER module_need() : 0.637 ms - Total 0.637 ms / 1 intvls (Avg 0.637 ms)
[0x9b08210] main input debug: creating demux: access='file' demux='xspf-open' path='/home/edwin/.local/share/vlc/ml.xspf'
[0x9b0c140] main demux debug: looking for demux module: 1 candidate
[0x9b0c140] playlist demux debug: using XSPF playlist reader
[0x9b0c140] main demux debug: using demux module "playlist"
[0x9b0c140] main demux debug: TIMER module_need() : 1.097 ms - Total 1.097 ms / 1 intvls (Avg 1.097 ms)
[0x9b08210] main input debug: `file/xspf-open:///home/edwin/.local/share/vlc/ml.xspf' successfully opened
[0x9b0db20] main xml debug: looking for xml module: 2 candidates
[0x9b0db20] main xml debug: using xml module "xml"
[0x9b0db20] main xml debug: TIMER module_need() : 1.783 ms - Total 1.783 ms / 1 intvls (Avg 1.783 ms)
[0x9b0c140] playlist demux debug: parsed 0 tracks successfully
[0x9b0db20] main xml debug: removing module "xml"
[0x9b08210] main input debug: EOF reached
[0x9b0c140] main demux debug: removing module "playlist"
[0x9b0d0f8] main stream debug: removing module "stream_filter_record"
[0x9b199f8] main access debug: removing module "access_file"
[0x9b08210] main input debug: TIMER input launching for 'Media Library' : 52.483 ms - Total 52.483 ms / 1 intvls (Avg 52.483 ms)
[0x9b08070] main playlist debug: rebuilding array of current - root Playlist
[0x9b08070] main playlist debug: rebuild done - 0 items, index -1
[0x9b08070] main playlist debug: Activated
[0x9b08210] main interface debug: looking for interface module: 1 candidate
[0x9b08210] main interface debug: using interface module "hotkeys"
[0x9b08210] main interface debug: TIMER module_need() : 1.592 ms - Total 1.592 ms / 1 intvls (Avg 1.592 ms)
[0x9b08210] main interface debug: thread started
[0x9b08210] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9b0c120] main interface debug: looking for interface module: 1 candidate
[0x9b0c120] main interface debug: using interface module "inhibit"
[0x9b0c120] main interface debug: TIMER module_need() : 10.830 ms - Total 10.830 ms / 1 intvls (Avg 10.830 ms)
[0x9b0c120] main interface debug: thread started
[0x9b0c120] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9b1a5e0] main interface debug: looking for interface module: 1 candidate
[0x9b1a5e0] main interface debug: using interface module "screensaver"
[0x9b1a5e0] main interface debug: TIMER module_need() : 0.145 ms - Total 0.145 ms / 1 intvls (Avg 0.145 ms)
[0x9b1a5e0] main interface debug: thread started
[0x9b1a5e0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9b09fc8] main interface debug: looking for interface module: 1 candidate
[0x9b09fc8] main interface debug: using interface module "signals"
[0x9b09fc8] main interface debug: TIMER module_need() : 1.238 ms - Total 1.238 ms / 1 intvls (Avg 1.238 ms)
[0x9b09fc8] main interface debug: thread started
[0x9b09fc8] main interface debug: thread ended
[0x9b09fc8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9b0f118] main interface debug: looking for interface module: 1 candidate
[0x9b0f118] main interface debug: using interface module "globalhotkeys"
[0x9b0f118] main interface debug: TIMER module_need() : 137.844 ms - Total 137.844 ms / 1 intvls (Avg 137.844 ms)
[0x9b0f118] main interface debug: thread started
[0x9b0f118] main interface debug: thread ended
[0x9b0f118] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9a69140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9b11450] main interface debug: looking for interface module: 3 candidates
[0x9b11450] main interface debug: using interface module "qt4"
[0x9b11450] main interface debug: TIMER module_need() : 641.325 ms - Total 641.325 ms / 1 intvls (Avg 641.325 ms)
[0x9b11450] main interface debug: thread started
[0x9b11450] main interface debug: thread ended
[0x9b11450] qt4 interface debug: Error while initializing qt-specific localization
[0x9b11450] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9b08070] main playlist debug: adding item `30.Rock.avi' ( /home/edwin/Desktop/30.Rock.avi )
[0x9b08070] main playlist debug: rebuilding array of current - root Playlist
[0x9b08070] main playlist debug: rebuild done - 1 items, index -1
[0x9b08070] main playlist debug: processing request item 30.Rock.avi node null skip 0
[0x9b08070] main playlist debug: resyncing on 30.Rock.avi
[0x9b08070] main playlist debug: 30.Rock.avi is at 0
[0x9b08070] main playlist debug: starting new item
[0x9b08070] main playlist debug: creating new input thread
[0x9e04ac0] main input debug: Creating an input for '30.Rock.avi'
[0x9e04ac0] main input debug: thread started
[0x9e04ac0] main input debug: using timeshift granularity of 50 MBytes
[0x9e04ac0] main input debug: using timeshift path '/tmp'
[0x9b11450] qt4 interface debug: Adding a new MRL to recent ones: /home/edwin/Desktop/30.Rock.avi
[0x9e04ac0] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0x9e04ac0] main input debug: `/home/edwin/Desktop/30.Rock.avi' gives access `' demux `' path `/home/edwin/Desktop/30.Rock.avi'
[0x9e04ac0] main input debug: creating demux: access='' demux='' path='/home/edwin/Desktop/30.Rock.avi'
[0x9f7a678] main demux debug: looking for access_demux module: 7 candidates
[0x9f7a678] main demux debug: TIMER module_need() : 8.548 ms - Total 8.548 ms / 1 intvls (Avg 8.548 ms)
[0x9e04ac0] main input debug: creating access '' path='/home/edwin/Desktop/30.Rock.avi'
[0x9e1b770] main access debug: looking for access module: 8 candidates
[0x9e1b770] vcd access debug: trying .cue file: /home/edwin/Desktop/30.Rock.cue
[0x9e1b770] vcd access debug: could not find .cue file
[0x9b11450] qt4 interface debug: IM: Setting an input
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9e1b770] access_file access debug: opening file `/home/edwin/Desktop/30.Rock.avi'
[0x9e1b770] main access debug: using access module "access_file"
[0x9e1b770] main access debug: TIMER module_need() : 16.466 ms - Total 16.466 ms / 1 intvls (Avg 16.466 ms)
[0x9e339a8] main stream debug: Using AStream*Stream
[0x9e339a8] main stream debug: pre buffering
[0x9e339a8] main stream debug: received first data after 0 ms
[0x9e339a8] main stream debug: pre-buffering done 1024 bytes in 0s - 5649 kbytes/s
[0x9f90488] main stream debug: looking for stream_filter module: 4 candidates
[0x9f90488] main stream debug: TIMER module_need() : 0.446 ms - Total 0.446 ms / 1 intvls (Avg 0.446 ms)
[0x9f90488] main stream debug: looking for stream_filter module: 1 candidate
[0x9f90488] main stream debug: using stream_filter module "stream_filter_record"
[0x9f90488] main stream debug: TIMER module_need() : 0.604 ms - Total 0.604 ms / 1 intvls (Avg 0.604 ms)
[0x9e04ac0] main input debug: creating demux: access='' demux='' path='/home/edwin/Desktop/30.Rock.avi'
[0x9dd3638] main demux debug: looking for demux module: 47 candidates
[0x9f90488] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:183253236 pos:0
[0x9f90488] avi stream debug: found LIST chunk: 'AVI '
[0x9f90488] avi stream debug: <list 'AVI '>
[0x9f90488] avi stream debug: found Chunk fourcc:5453494c (LIST) size:306 pos:12
[0x9f90488] avi stream debug: found LIST chunk: 'hdrl'
[0x9f90488] avi stream debug: <list 'hdrl'>
[0x9f90488] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24
[0x9f90488] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 624x352
[0x9f90488] avi stream debug: found Chunk fourcc:5453494c (LIST) size:116 pos:88
[0x9f90488] avi stream debug: found LIST chunk: 'strl'
[0x9f90488] avi stream debug: <list 'strl'>
[0x9f90488] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100
[0x9f90488] avi stream debug: strh: type:vids handler:0x44495658 samplesize:0 23.98fps
[0x9f90488] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164
[0x9f90488] avi stream debug: strf: video:XVID 624x352 planes:1 24bpp
[0x9f90488] avi stream debug: </list 'strl'>
[0x9f90488] avi stream debug: found Chunk fourcc:5453494c (LIST) size:106 pos:212
[0x9f90488] avi stream debug: found LIST chunk: 'strl'
[0x9f90488] avi stream debug: <list 'strl'>
[0x9f90488] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:224
[0x9f90488] avi stream debug: strh: type:auds handler:0x00000000 samplesize:0 41.67fps
[0x9f90488] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:288
[0x9f90488] avi stream debug: strf: audio:0x0055 channels:2 48000Hz 16bits/sample 125kb/s
[0x9f90488] avi stream debug: </list 'strl'>
[0x9f90488] avi stream debug: </list 'hdrl'>
[0x9f90488] avi stream debug: found Chunk fourcc:5453494c (LIST) size:28 pos:326
[0x9f90488] avi stream debug: found LIST chunk: 'INFO'
[0x9f90488] avi stream debug: <list 'INFO'>
[0x9f90488] avi stream debug: found Chunk fourcc:54465349 (ISFT) size:16 pos:338
[0x9f90488] avi stream debug: ISFT: software : transcode-1.0.2
[0x9f90488] avi stream debug: </list 'INFO'>
[0x9f90488] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1666 pos:362
[0x9f90488] avi stream debug: found Chunk fourcc:5453494c (LIST) size:181960936 pos:2036
[0x9f90488] avi stream debug: skipping movi chunk
[0x9f90488] avi stream debug: found Chunk fourcc:31786469 (idx1) size:1290256 pos:181962980
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9f90488] avi stream debug: idx1: index entry:80641
[0x9f90488] avi stream debug: </list 'AVI '>
[0x9f90488] avi stream debug: * LIST-root size:183253244 pos:0
[0x9f90488] avi stream debug:      + RIFF-AVI  size:183253236 pos:0
[0x9f90488] avi stream debug:      |    + LIST-hdrl size:306 pos:12
[0x9f90488] avi stream debug:      |    |    + avih size:56 pos:24
[0x9f90488] avi stream debug:      |    |    + LIST-strl size:116 pos:88
[0x9f90488] avi stream debug:      |    |    |    + strh size:56 pos:100
[0x9f90488] avi stream debug:      |    |    |    + strf size:40 pos:164
[0x9f90488] avi stream debug:      |    |    + LIST-strl size:106 pos:212
[0x9f90488] avi stream debug:      |    |    |    + strh size:56 pos:224
[0x9f90488] avi stream debug:      |    |    |    + strf size:30 pos:288
[0x9f90488] avi stream debug:      |    + LIST-INFO size:28 pos:326
[0x9f90488] avi stream debug:      |    |    + ISFT size:16 pos:338
[0x9f90488] avi stream debug:      |    + JUNK size:1666 pos:362
[0x9f90488] avi stream debug:      |    + LIST-movi size:181960936 pos:2036
[0x9f90488] avi stream debug:      |    + idx1 size:1290256 pos:181962980
[0x9dd3638] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED
[0x9dd3638] avi demux debug: stream[0] rate:23976024 scale:1000000 samplesize:0
[0x9dd3638] avi demux debug: stream[0] video(XVID) 624x352 24bpp 23.976024fps
[0x9e04ac0] main input debug: selecting program id=0
[0x9dd3638] avi demux debug: stream[1] rate:48000 scale:1152 samplesize:0
[0x9dd3638] avi demux debug: stream[1] audio(0x55) 2 channels 48000Hz 16bits
[0x9dd3638] avi demux debug: stream[0] created 29454 index entries
[0x9dd3638] avi demux debug: stream[1] created 51187 index entries
[0x9dd3638] avi demux debug: stream[0] length:1228 (based on index)
[0x9dd3638] avi demux debug: stream[1] length:1228 (based on index)
[0x9dd3638] main demux debug: using demux module "avi"
[0x9dd3638] main demux debug: TIMER module_need() : 294.265 ms - Total 294.265 ms / 1 intvls (Avg 294.265 ms)
[0x9e04ac0] main input debug: looking for a subtitle file in /home/edwin/Desktop/
[0xa013a98] main decoder debug: looking for decoder module: 31 candidates
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9b11450] qt4 interface debug: Updating the geometry
[0xa013a98] avcodec decoder debug: libavcodec initialized (interface 0x342d00)
[0xa013a98] avcodec decoder debug: using direct rendering
[0xa013a98] avcodec decoder debug: ffmpeg codec (MPEG-4 Video) started
[0xa013a98] main decoder debug: using decoder module "avcodec"
[0xa013a98] main decoder debug: TIMER module_need() : 200.393 ms - Total 200.393 ms / 1 intvls (Avg 200.393 ms)
[0xa013a98] main decoder debug: thread started
[0xa013a98] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9b11450] qt4 interface debug: Updating the geometry
[0xa00f730] main decoder debug: looking for decoder module: 31 candidates
[0xa00f730] main decoder debug: using decoder module "mpeg_audio"
[0xa00f730] main decoder debug: TIMER module_need() : 0.883 ms - Total 0.883 ms / 1 intvls (Avg 0.883 ms)
[0xa00f730] main decoder debug: thread started
[0xa00f730] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9b11450] qt4 interface debug: Updating the geometry
[0x9e04ac0] main input debug: `/home/edwin/Desktop/30.Rock.avi' successfully opened
[0x9b11450] qt4 interface debug: New caching: 0
[0x9b11450] qt4 interface debug: New caching: 0
[0x9e04ac0] main input debug: Buffering 0%
[0x9e04ac0] main input debug: no usable vout present, spawning one
[0xa16aca8] main spu text debug: looking for text renderer module: 2 candidates
[0xa173e60] main generic debug: thread started
[0xa173e60] freetype generic debug: Building font database...
[0xa173e60] freetype generic debug: Finished building font database.
[0xa173e60] freetype generic debug: Took 1057 microseconds
[0x9b11450] qt4 interface debug: New caching: 8
[0x9b11450] qt4 interface debug: New caching: 8
[0x9e04ac0] main input debug: Buffering 8%
[0xa00f730] mpeg_audio decoder debug: MPGA channels:2 samplerate:48000 bitrate:32
[0x9b11450] qt4 interface debug: New caching: 16
[0x9b11450] qt4 interface debug: New caching: 16
[0x9e04ac0] main input debug: Buffering 16%
[0x9b11450] qt4 interface debug: New caching: 25
[0x9b11450] qt4 interface debug: New caching: 25
[0x9e04ac0] main input debug: Buffering 25%
[0x9e04ac0] main input debug: Buffering 33%
[0x9e04ac0] main input debug: Buffering 41%
[0x9e04ac0] main input debug: Buffering 50%
[0x9e04ac0] main input debug: Buffering 58%
[0x9e04ac0] main input debug: Buffering 66%
[0x9e04ac0] main input debug: Buffering 75%
[0x9e04ac0] main input debug: Buffering 83%
[0x9e04ac0] main input debug: Buffering 91%
[0x9e04ac0] main input debug: Buffering 100%
[0x9e04ac0] main input debug: Stream buffering done (325 ms in 203 ms)
[0x9b11450] qt4 interface debug: New caching: 100
[0x9b11450] qt4 interface debug: New caching: 100
[0xa173e60] main generic debug: thread (fontlist builder) created at priority 0 (freetype.c:473)
[0xa16aca8] freetype spu text debug: using fontsize: 2
[0xa16aca8] main spu text debug: using text renderer module "freetype"
[0xa16aca8] main spu text debug: TIMER module_need() : 199.936 ms - Total 199.936 ms / 1 intvls (Avg 199.936 ms)
[0xa16bbd8] main scale debug: looking for video filter2 module: 20 candidates
[0xa16bbd8] swscale scale debug: 32x32 chroma: YUVA -> 16x16 chroma: YUVA with scaling using Bicubic (good quality)
[0xa16bbd8] main scale debug: using video filter2 module "swscale"
[0xa16bbd8] main scale debug: TIMER module_need() : 8.030 ms - Total 8.030 ms / 1 intvls (Avg 8.030 ms)
[0xa174698] main scale debug: looking for video filter2 module: 20 candidates
[0xa173e60] main generic debug: thread ended
[0xa174698] yuvp scale debug: YUVP to YUVA converter
[0xa174698] main scale debug: using video filter2 module "yuvp"
[0xa174698] main scale debug: TIMER module_need() : 16.402 ms - Total 16.402 ms / 1 intvls (Avg 16.402 ms)
[0xa1674a8] main video output debug: window size: 624x352
[0xa1674a8] main video output debug: looking for video output module: 5 candidates
[0xa1674a8] xvideo video output warning: no free XVideo port found for format 0x30323449 (I420)
[0xa1674a8] xvideo video output warning: no free XVideo port found for format 0x32595559 (YUY2)
[0xa1674a8] xvideo video output warning: no free XVideo port found for format 0x36315652 (RV16)
[0xa23dbd8] main window debug: looking for xwindow module: 3 candidates
[0xa23dbd8] qt4 window debug: requesting video...
[0x9b11450] qt4 interface debug: Video was requested -1, -1
[0x9b11450] qt4 interface debug: Video is resizing to: 624 352
[0x9b11450] qt4 interface debug: Updating the geometry
[0xa23dbd8] main window debug: using xwindow module "qt4"
[0xa23dbd8] main window debug: TIMER module_need() : 10.585 ms - Total 10.585 ms / 1 intvls (Avg 10.585 ms)
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0xa1674a8] x11 video output debug: XShm video extension v1.1 (with pixmaps, opcode: 141)
[0xa1674a8] x11 video output debug: Window manager supports NetWM
[0xa1674a8] x11 video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[0xa1674a8] x11 video output debug: Window manager supports _NET_WM_STATE_ABOVE
[0xa1674a8] x11 video output debug: Window manager supports _NET_WM_STATE_BELOW
[0xa1674a8] main video output debug: using video output module "x11"
[0xa1674a8] main video output debug: TIMER module_need() : 438.508 ms - Total 438.508 ms / 1 intvls (Avg 438.508 ms)
[0xa1674a8] main video output debug: Deinterlacing available
[0xa1674a8] x11 video output debug: x11 image size 624x352 (0,0,624x352)
[0xa1674a8] main video output debug: got 2 direct buffer(s)
[0xa1674a8] main video output debug: pic render sz 624x352, of (0,0), vsz 624x352, 4cc I420, ar 382909:216000, sar 1:1, msk r0x0 g0x0 b0x0
[0xa1674a8] main video output debug: pic in sz 624x352, of (0,0), vsz 624x352, 4cc I420, ar 382909:216000, sar 1:1, msk r0x0 g0x0 b0x0
[0xa1674a8] main video output debug: pic out sz 624x352, of (0,0), vsz 624x352, 4cc RV16, ar 382909:216000, sar 1:1, msk r0xf800 g0x7e0 b0x1f
[0xa23edb0] main chroma debug: looking for video filter2 module: 20 candidates
[0xa23edb0] swscale chroma debug: 624x352 chroma: I420 -> 624x352 chroma: RV16 with scaling using Bicubic (good quality)
[0xa23edb0] main chroma debug: using video filter2 module "swscale"
[0xa23edb0] main chroma debug: TIMER module_need() : 0.717 ms - Total 0.717 ms / 1 intvls (Avg 0.717 ms)
[0xa1674a8] main video output debug: indirect render, mapping render pictures 0-15 to system pictures 2-17
[0x9e04ac0] main input debug: creating aout
[0xa23e920] main audio output debug: looking for audio output module: 3 candidates
[0xa23e920] oss audio output error: cannot open audio device (/dev/dsp)
[0xa23e920] pulse audio output: No. of Audio Channels: 2
[0xa23edb0] main chroma debug: removing module "swscale"
[0xa1674a8] qt4 video output debug: Qt: Entering Fullscreen
[0xa1674a8] x11 video output debug: x11 image size 624x352 (0,0,624x352)
[0xa230e10] main chroma debug: looking for video filter2 module: 20 candidates
[0xa230e10] swscale chroma debug: 624x352 chroma: I420 -> 624x352 chroma: RV16 with scaling using Bicubic (good quality)
[0xa230e10] main chroma debug: using video filter2 module "swscale"
[0xa230e10] main chroma debug: TIMER module_need() : 0.763 ms - Total 0.763 ms / 1 intvls (Avg 0.763 ms)
[0xa013a98] main decoder debug: End of video preroll
[0xa013a98] main decoder debug: Received first picture
[0xa1674a8] main video output debug: Post-processing available
[0xa23e920] pulse audio output debug: Pulse mainloop started
[0xa23e920] pulse audio output debug: Pulse stream connected
[0xa23e920] pulse audio output debug: Pulse initialized successfully
[0xa23e920] pulse audio output debug: Buffer metrics: maxlength=153600, tlength=46080, prebuf=38400, minreq=7680
[0xa23e920] pulse audio output debug: Using sample spec 'float32le 2ch 48000Hz', channel map 'front-left,front-right'.
[0xa23e920] pulse audio output debug: Connected to device auto_null (0, not suspended).
[0xa23e920] main audio output debug: using audio output module "pulse"
[0xa23e920] main audio output debug: TIMER module_need() : 222.180 ms - Total 222.180 ms / 1 intvls (Avg 222.180 ms)
[0xa23e920] main audio output debug: output 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[0xa23e920] main audio output debug: mixer 'fl32' 48000 Hz Stereo frame=1 samples/8 bytes
[0xa23e920] main audio output debug: no need for any filter
[0xa23e920] main audio output debug: looking for audio mixer module: 3 candidates
[0xa16aca8] freetype spu text debug: using fontsize: 22
[0xa40c600] main blend debug: looking for video blending module: 1 candidate
[0xa40c600] blend blend debug: chroma: YUVA -> RV16
[0xa40c600] main blend debug: using video blending module "blend"
[0xa40c600] main blend debug: TIMER module_need() : 1.512 ms - Total 1.512 ms / 1 intvls (Avg 1.512 ms)
[0xa23e920] main audio output debug: using audio mixer module "float32_mixer"
[0xa23e920] main audio output debug: TIMER module_need() : 5.227 ms - Total 5.227 ms / 1 intvls (Avg 5.227 ms)
[0xa23e920] main audio output debug: input 'mpga' 48000 Hz Stereo frame=1152 samples/969 bytes
[0xa189218] main audio filter debug: looking for audio filter module: 1 candidate
[0xa189218] scaletempo audio filter warning: bad input or output format
[0xa189218] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0xa189218] main audio filter debug: TIMER module_need() : 1.244 ms - Total 1.244 ms / 1 intvls (Avg 1.244 ms)
[0xa189218] main audio filter debug: looking for audio filter module: 1 candidate
[0xa189218] scaletempo audio filter debug: format: 48000 rate, 2 nch, 4 bps, fl32
[0xa189218] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0xa189218] scaletempo audio filter debug: 1.000 scale, 1440.000 stride_in, 1440 stride_out, 1152 standing, 288 overlap, 672 search, 2400 queue, fl32 mode
[0xa189218] main audio filter debug: using audio filter module "scaletempo"
[0xa189218] main audio filter debug: TIMER module_need() : 0.714 ms - Total 0.714 ms / 1 intvls (Avg 0.714 ms)
[0xa23e920] main audio output debug: filter(s) 'mpga'->'fl32' 48000 Hz->48000 Hz Stereo->Stereo
[0xa189630] main audio output debug: looking for audio filter module: 24 candidates
[0xa189630] main audio output debug: using audio filter module "mpgatofixed32"
[0xa189630] main audio output debug: TIMER module_need() : 3.413 ms - Total 3.413 ms / 1 intvls (Avg 3.413 ms)
[0xa23e920] main audio output debug: found a filter for the whole conversion
[0xa23e920] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz Stereo->Stereo
[0xa24f4a0] main audio output debug: looking for audio filter module: 24 candidates
[0xa24f4a0] main audio output debug: using audio filter module "bandlimited_resampler"
[0xa24f4a0] main audio output debug: TIMER module_need() : 25.425 ms - Total 25.425 ms / 1 intvls (Avg 25.425 ms)
[0xa23e920] main audio output debug: found a filter for the whole conversion
[0xa00f730] main decoder debug: End of audio preroll
[0x9e04ac0] main input debug: Decoder buffering done in 798 ms
[0xa23e920] main audio output warning: PTS is out of range (-9452), dropping buffer
[0xa23e920] main audio output warning: PTS is out of range (-33370), dropping buffer
[0xa23e920] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0xa23e920] pulse audio output debug: Pulse stream started
[0xa23e920] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0xa23e920] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0xa23e920] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0xa23e920] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0xa23e920] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0xa23e920] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0xa23e920] main audio output debug: audio output is too slow (234327), trashing 20000us
[0xa23e920] main audio output debug: audio output is too slow (214416), trashing 20000us
[0xa23e920] main audio output debug: audio output is too slow (194442), trashing 20000us

```

Opening 30 Rock file to stream and transcode.
```
edwin@US904-32:/usr/local/bin$ vlc -vvv
VLC media player 1.0.0 Goldeneye
[0x942d140] main libvlc debug: VLC media player - version 1.0.0 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x942d140] main libvlc debug: libvlc was configured with ./configure  '--prefix=/usr/local' '--with-x264-tree=extras/x264' '--with-live555-tree=extras/live' '--enable-release' '--enable-switcher' '--enable-shout' '--enable-dc1394' '--enable-dv' '--enable-dvdread' '--enable-v4l' '--enable-pvr' '--enable-vcdx' '--enable-faad' '--enable-twolame' '--enable-real' '--enable-realrtsp' '--enable-flac' '--enable-tremor' '--enable-tarkin' '--enable-theora' '--enable-ogg' '--enable-vorbis' '--enable-a52' '--enable-gnomevfs' '--enable-dca'
[0x942d140] main libvlc debug: translation test: code is "C"
[0x942d140] main libvlc debug: checking plugin modules
[0x942d140] main libvlc debug: loading plugins cache file /home/edwin/.cache/vlc/plugins-04041e.dat
[0x942d140] main libvlc debug: recursively browsing `/usr/local/lib/vlc'
[0x942d140] main libvlc warning: cannot load module `/usr/local/lib/vlc/demux/liblive555_plugin.so' (/usr/local/lib/vlc/demux/liblive555_plugin.so: undefined symbol: _Z6strDupPKc)
[0x942d140] main libvlc debug: module bank initialized (374 modules)
[0x942d140] main libvlc debug: opening config file (/home/edwin/.config/vlc/vlcrc)
[0x942d140] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU
[0x942d140] main libvlc debug: looking for memcpy module: 3 candidates
[0x942d140] main libvlc debug: using memcpy module "memcpymmxext"
[0x94cc210] main input debug: Creating an input for 'Media Library'
[0x94cc210] main input debug: Input is a meta file: disabling unneeded options
[0x94cc210] main input debug: using timeshift granularity of 50 MBytes
[0x94cc210] main input debug: using timeshift path '/tmp'
[0x94cc210] main input debug: `file/xspf-open:///home/edwin/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/edwin/.local/share/vlc/ml.xspf'
[0x94cc210] main input debug: creating demux: access='file' demux='xspf-open' path='/home/edwin/.local/share/vlc/ml.xspf'
[0x94dd380] main demux debug: looking for access_demux module: 1 candidate
[0x94dd380] main demux warning: no access_demux module matching "file" could be loaded
[0x94dd380] main demux debug: TIMER module_need() : 2.311 ms - Total 2.311 ms / 1 intvls (Avg 2.311 ms)
[0x94cc210] main input debug: creating access 'file' path='/home/edwin/.local/share/vlc/ml.xspf'
[0x94dd9f8] main access debug: looking for access module: 3 candidates
[0x94dd9f8] access_file access debug: opening file `/home/edwin/.local/share/vlc/ml.xspf'
[0x94dd9f8] main access debug: using access module "access_file"
[0x94dd9f8] main access debug: TIMER module_need() : 29.581 ms - Total 29.581 ms / 1 intvls (Avg 29.581 ms)
[0x94de248] main stream debug: Using AStream*Stream
[0x94de248] main stream debug: pre buffering
[0x94de248] main stream debug: received first data after 0 ms
[0x94de248] main stream debug: pre-buffering done 296 bytes in 0s - 1513 kbytes/s
[0x94cef98] main stream debug: looking for stream_filter module: 4 candidates
[0x94cef98] main stream debug: TIMER module_need() : 2.921 ms - Total 2.921 ms / 1 intvls (Avg 2.921 ms)
[0x94d10f8] main stream debug: looking for stream_filter module: 1 candidate
[0x94d10f8] main stream debug: using stream_filter module "stream_filter_record"
[0x94d10f8] main stream debug: TIMER module_need() : 5.946 ms - Total 5.946 ms / 1 intvls (Avg 5.946 ms)
[0x94cc210] main input debug: creating demux: access='file' demux='xspf-open' path='/home/edwin/.local/share/vlc/ml.xspf'
[0x94d0140] main demux debug: looking for demux module: 1 candidate
[0x94d0140] playlist demux debug: using XSPF playlist reader
[0x94d0140] main demux debug: using demux module "playlist"
[0x94d0140] main demux debug: TIMER module_need() : 1.017 ms - Total 1.017 ms / 1 intvls (Avg 1.017 ms)
[0x94cc210] main input debug: `file/xspf-open:///home/edwin/.local/share/vlc/ml.xspf' successfully opened
[0x94d1b20] main xml debug: looking for xml module: 2 candidates
[0x94d1b20] main xml debug: using xml module "xml"
[0x94d1b20] main xml debug: TIMER module_need() : 2.009 ms - Total 2.009 ms / 1 intvls (Avg 2.009 ms)
[0x94d0140] playlist demux debug: parsed 0 tracks successfully
[0x94d1b20] main xml debug: removing module "xml"
[0x94cc210] main input debug: EOF reached
[0x94d0140] main demux debug: removing module "playlist"
[0x94d10f8] main stream debug: removing module "stream_filter_record"
[0x94dd9f8] main access debug: removing module "access_file"
[0x94cc210] main input debug: TIMER input launching for 'Media Library' : 64.988 ms - Total 64.988 ms / 1 intvls (Avg 64.988 ms)
[0x94cc070] main playlist debug: rebuilding array of current - root Playlist
[0x94cc070] main playlist debug: rebuild done - 0 items, index -1
[0x94cc070] main playlist debug: Activated
[0x94cc210] main interface debug: looking for interface module: 1 candidate
[0x94cc210] main interface debug: using interface module "hotkeys"
[0x94cc210] main interface debug: TIMER module_need() : 1.409 ms - Total 1.409 ms / 1 intvls (Avg 1.409 ms)
[0x94cc210] main interface debug: thread started
[0x94cc210] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x94d0120] main interface debug: looking for interface module: 1 candidate
[0x94d0120] main interface debug: using interface module "inhibit"
[0x94d0120] main interface debug: TIMER module_need() : 10.653 ms - Total 10.653 ms / 1 intvls (Avg 10.653 ms)
[0x94d0120] main interface debug: thread started
[0x94d0120] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x94de5e0] main interface debug: looking for interface module: 1 candidate
[0x94de5e0] main interface debug: using interface module "screensaver"
[0x94de5e0] main interface debug: TIMER module_need() : 0.907 ms - Total 0.907 ms / 1 intvls (Avg 0.907 ms)
[0x94de5e0] main interface debug: thread started
[0x94de5e0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x94cdfc8] main interface debug: looking for interface module: 1 candidate
[0x94cdfc8] main interface debug: using interface module "signals"
[0x94cdfc8] main interface debug: TIMER module_need() : 0.979 ms - Total 0.979 ms / 1 intvls (Avg 0.979 ms)
[0x94cdfc8] main interface debug: thread started
[0x94cdfc8] main interface debug: thread ended
[0x94cdfc8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x94d3118] main interface debug: looking for interface module: 1 candidate
[0x94d3118] main interface debug: using interface module "globalhotkeys"
[0x94d3118] main interface debug: TIMER module_need() : 143.580 ms - Total 143.580 ms / 1 intvls (Avg 143.580 ms)
[0x94d3118] main interface debug: thread started
[0x94d3118] main interface debug: thread ended
[0x94d3118] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x942d140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x94d3e28] main interface debug: looking for interface module: 3 candidates
[0x94d3e28] main interface debug: using interface module "qt4"
[0x94d3e28] main interface debug: TIMER module_need() : 652.021 ms - Total 652.021 ms / 1 intvls (Avg 652.021 ms)
[0x94d3e28] main interface debug: thread started
[0x94d3e28] main interface debug: thread ended
[0x94d3e28] qt4 interface debug: Error while initializing qt-specific localization
[0x94d3e28] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x94d3e28] qt4 interface debug: MRL passed to the Sout: /home/edwin/Desktop/30.Rock.avi
[0x94d3e28] qt4 interface debug: Adding option: :sout=#transcode{vcodec=mp4v,vb=800,fps=30,scale=1,acodec=mp4a,ab=128,channels=2,samplerate=44100}:std{access=udp,mux=ts,dst=239.255.12.12:1234}
[0x94cc070] main playlist debug: adding item `Streaming' ( /home/edwin/Desktop/30.Rock.avi )
[0x94d3e28] qt4 interface debug: Adding a new MRL to recent ones: /home/edwin/Desktop/30.Rock.avi
[0x94cc070] main playlist debug: rebuilding array of current - root Playlist
[0x94cc070] main playlist debug: rebuild done - 1 items, index -1
[0x94cc070] main playlist debug: processing request item Streaming node null skip 0
[0x94cc070] main playlist debug: resyncing on Streaming
[0x94cc070] main playlist debug: Streaming is at 0
[0x94cc070] main playlist debug: starting new item
[0x94cc070] main playlist debug: creating new input thread
[0x9a8d6a0] main input debug: Creating an input for 'Streaming'
[0x9a8d6a0] main input debug: thread started
[0x9a903a0] main stream output debug: stream=`transcode'
[0x9949930] main stream out debug: looking for sout stream module: 1 candidate
[0x9a903a0] main stream output debug: stream=`std'
[0x994a880] main stream out debug: looking for sout stream module: 1 candidate
[0x994a880] main stream out debug: set config option: sout-standard-access to udp
[0x9a8d6a0] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0x94d3e28] qt4 interface debug: IM: Setting an input
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x994a880] main stream out debug: set config option: sout-standard-mux to ts
[0x994a880] main stream out debug: set config option: sout-standard-dst to 239.255.12.12:1234
[0x994a880] stream_out_standard stream out debug: creating `udp/ts://239.255.12.12:1234'
[0x994a880] stream_out_standard stream out debug: extension is 12:1234
[0x994a880] stream_out_standard stream out debug: extension -> mux=(null)
[0x994a880] stream_out_standard stream out debug: using `udp/ts://239.255.12.12:1234'
[0x9a63d28] main access out debug: looking for sout access module: 1 candidate
[0x9a63d28] main access out debug: net: connecting to [239.255.12.12]:1234
[0x9a63d28] access_output_udp access out debug: source: 10.37.32.242 port 36671
[0x9a63d28] access_output_udp access out debug: destination: 239.255.12.12 port 1234
[0x9a63d28] main access out debug: using sout access module "access_output_udp"
[0x9a63d28] main access out debug: TIMER module_need() : 81.883 ms - Total 81.883 ms / 1 intvls (Avg 81.883 ms)
[0x994a880] stream_out_standard stream out debug: access opened
[0x989c580] main mux debug: looking for sout mux module: 1 candidate
[0x989c580] mux_ts mux debug: shaping=200000 pcr=70000 dts_delay=400000
[0x989c580] main mux debug: using sout mux module "mux_ts"
[0x989c580] main mux debug: TIMER module_need() : 26.071 ms - Total 26.071 ms / 1 intvls (Avg 26.071 ms)
[0x9a903a0] main stream output debug: muxer support adding stream at any time
[0x9a903a0] main stream output debug: muxer prefers to wait for all ES before starting to mux
[0x994a880] stream_out_standard stream out debug: mux opened
[0x994a880] main stream out debug: using sout stream module "stream_out_standard"
[0x994a880] main stream out debug: TIMER module_need() : 148.303 ms - Total 148.303 ms / 1 intvls (Avg 148.303 ms)
[0x9949930] main stream out debug: set config option: sout-transcode-vcodec to mp4v
[0x9949930] main stream out debug: set config option: sout-transcode-vb to 800
[0x9949930] main stream out debug: set config option: sout-transcode-fps to 30
[0x9949930] main stream out debug: set config option: sout-transcode-scale to 1
[0x9949930] main stream out debug: set config option: sout-transcode-acodec to mp4a
[0x9949930] main stream out debug: set config option: sout-transcode-ab to 128
[0x9949930] main stream out debug: set config option: sout-transcode-channels to 2
[0x9949930] main stream out debug: set config option: sout-transcode-samplerate to 44100
[0x9949930] stream_out_transcode stream out debug: codec audio=mp4a 44100Hz 2 channels 128Kb/s
[0x9949930] stream_out_transcode stream out debug: codec video=mp4v 0x0 scaling: 1.000000 800kb/s
[0x9949930] main stream out debug: using sout stream module "stream_out_transcode"
[0x9949930] main stream out debug: TIMER module_need() : 215.046 ms - Total 215.046 ms / 1 intvls (Avg 215.046 ms)
[0x9a8d6a0] main input debug: using timeshift granularity of 50 MBytes
[0x9a8d6a0] main input debug: using timeshift path '/tmp'
[0x94d3e28] qt4 interface debug: New caching: 0
[0x94d3e28] qt4 interface debug: New caching: 0
[0x9a8d6a0] main input debug: `/home/edwin/Desktop/30.Rock.avi' gives access `' demux `' path `/home/edwin/Desktop/30.Rock.avi'
[0x9a8d6a0] main input debug: creating demux: access='' demux='' path='/home/edwin/Desktop/30.Rock.avi'
[0x98c7480] main demux debug: looking for access_demux module: 7 candidates
[0x98c7480] main demux debug: TIMER module_need() : 7.262 ms - Total 7.262 ms / 1 intvls (Avg 7.262 ms)
[0x9a8d6a0] main input debug: creating access '' path='/home/edwin/Desktop/30.Rock.avi'
[0x9a5f1b0] main access debug: looking for access module: 8 candidates
[0x9a5f1b0] vcd access debug: trying .cue file: /home/edwin/Desktop/30.Rock.cue
[0x9a5f1b0] vcd access debug: could not find .cue file
[0x9a5f1b0] access_file access debug: opening file `/home/edwin/Desktop/30.Rock.avi'
[0x9a5f1b0] main access debug: using access module "access_file"
[0x9a5f1b0] main access debug: TIMER module_need() : 13.157 ms - Total 13.157 ms / 1 intvls (Avg 13.157 ms)
[0x99e8220] main stream debug: Using AStream*Stream
[0x99e8220] main stream debug: pre buffering
[0x99e8220] main stream debug: received first data after 0 ms
[0x99e8220] main stream debug: pre-buffering done 1024 bytes in 0s - 5464 kbytes/s
[0x95344b8] main stream debug: looking for stream_filter module: 4 candidates
[0x95344b8] main stream debug: TIMER module_need() : 0.574 ms - Total 0.574 ms / 1 intvls (Avg 0.574 ms)
[0x97a28d0] main stream debug: looking for stream_filter module: 1 candidate
[0x97a28d0] main stream debug: using stream_filter module "stream_filter_record"
[0x97a28d0] main stream debug: TIMER module_need() : 0.649 ms - Total 0.649 ms / 1 intvls (Avg 0.649 ms)
[0x9a8d6a0] main input debug: creating demux: access='' demux='' path='/home/edwin/Desktop/30.Rock.avi'
[0x95344b8] main demux debug: looking for demux module: 47 candidates
[0x97a28d0] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:183253236 pos:0
[0x97a28d0] avi stream debug: found LIST chunk: 'AVI '
[0x97a28d0] avi stream debug: <list 'AVI '>
[0x97a28d0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:306 pos:12
[0x97a28d0] avi stream debug: found LIST chunk: 'hdrl'
[0x97a28d0] avi stream debug: <list 'hdrl'>
[0x97a28d0] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24
[0x97a28d0] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED 624x352
[0x97a28d0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:116 pos:88
[0x97a28d0] avi stream debug: found LIST chunk: 'strl'
[0x97a28d0] avi stream debug: <list 'strl'>
[0x97a28d0] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100
[0x97a28d0] avi stream debug: strh: type:vids handler:0x44495658 samplesize:0 23.98fps
[0x97a28d0] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164
[0x97a28d0] avi stream debug: strf: video:XVID 624x352 planes:1 24bpp
[0x97a28d0] avi stream debug: </list 'strl'>
[0x97a28d0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:106 pos:212
[0x97a28d0] avi stream debug: found LIST chunk: 'strl'
[0x97a28d0] avi stream debug: <list 'strl'>
[0x97a28d0] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:224
[0x97a28d0] avi stream debug: strh: type:auds handler:0x00000000 samplesize:0 41.67fps
[0x97a28d0] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:288
[0x97a28d0] avi stream debug: strf: audio:0x0055 channels:2 48000Hz 16bits/sample 125kb/s
[0x97a28d0] avi stream debug: </list 'strl'>
[0x97a28d0] avi stream debug: </list 'hdrl'>
[0x97a28d0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:28 pos:326
[0x97a28d0] avi stream debug: found LIST chunk: 'INFO'
[0x97a28d0] avi stream debug: <list 'INFO'>
[0x97a28d0] avi stream debug: found Chunk fourcc:54465349 (ISFT) size:16 pos:338
[0x97a28d0] avi stream debug: ISFT: software : transcode-1.0.2
[0x97a28d0] avi stream debug: </list 'INFO'>
[0x97a28d0] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1666 pos:362
[0x97a28d0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:181960936 pos:2036
[0x97a28d0] avi stream debug: skipping movi chunk
[0x97a28d0] avi stream debug: found Chunk fourcc:31786469 (idx1) size:1290256 pos:181962980
[0x97a28d0] avi stream debug: idx1: index entry:80641
[0x97a28d0] avi stream debug: </list 'AVI '>
[0x97a28d0] avi stream debug: * LIST-root size:183253244 pos:0
[0x97a28d0] avi stream debug:      + RIFF-AVI  size:183253236 pos:0
[0x97a28d0] avi stream debug:      |    + LIST-hdrl size:306 pos:12
[0x97a28d0] avi stream debug:      |    |    + avih size:56 pos:24
[0x97a28d0] avi stream debug:      |    |    + LIST-strl size:116 pos:88
[0x97a28d0] avi stream debug:      |    |    |    + strh size:56 pos:100
[0x97a28d0] avi stream debug:      |    |    |    + strf size:40 pos:164
[0x97a28d0] avi stream debug:      |    |    + LIST-strl size:106 pos:212
[0x97a28d0] avi stream debug:      |    |    |    + strh size:56 pos:224
[0x97a28d0] avi stream debug:      |    |    |    + strf size:30 pos:288
[0x97a28d0] avi stream debug:      |    + LIST-INFO size:28 pos:326
[0x97a28d0] avi stream debug:      |    |    + ISFT size:16 pos:338
[0x97a28d0] avi stream debug:      |    + JUNK size:1666 pos:362
[0x97a28d0] avi stream debug:      |    + LIST-movi size:181960936 pos:2036
[0x97a28d0] avi stream debug:      |    + idx1 size:1290256 pos:181962980
[0x95344b8] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED
[0x95344b8] avi demux debug: stream[0] rate:23976024 scale:1000000 samplesize:0
[0x95344b8] avi demux debug: stream[0] video(XVID) 624x352 24bpp 23.976024fps
[0x9a8d6a0] main input debug: selecting program id=0
[0x95344b8] avi demux debug: stream[1] rate:48000 scale:1152 samplesize:0
[0x95344b8] avi demux debug: stream[1] audio(0x55) 2 channels 48000Hz 16bits
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x95344b8] avi demux debug: stream[0] created 29454 index entries
[0x95344b8] avi demux debug: stream[1] created 51187 index entries
[0x95344b8] avi demux debug: stream[0] length:1228 (based on index)
[0x95344b8] avi demux debug: stream[1] length:1228 (based on index)
[0x95344b8] main demux debug: using demux module "avi"
[0x95344b8] main demux debug: TIMER module_need() : 142.087 ms - Total 142.087 ms / 1 intvls (Avg 142.087 ms)
[0x9a8d6a0] main input debug: looking for a subtitle file in /home/edwin/Desktop/
[0x9a6ef98] main packetizer debug: looking for packetizer module: 21 candidates
[0x9a6ef98] main packetizer debug: using packetizer module "packetizer_mpeg4video"
[0x9a6ef98] main packetizer debug: TIMER module_need() : 10.926 ms - Total 10.926 ms / 1 intvls (Avg 10.926 ms)
[0x9a6ef98] main packetizer debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x9a6ef98] main packetizer debug: thread started
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x9a6dca8] main packetizer debug: looking for packetizer module: 21 candidates
[0x9a6dca8] main packetizer debug: using packetizer module "mpeg_audio"
[0x9a6dca8] main packetizer debug: TIMER module_need() : 18.461 ms - Total 18.461 ms / 1 intvls (Avg 18.461 ms)
[0x9a6dca8] main packetizer debug: thread started
[0x9a6dca8] main packetizer debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x94d3e28] qt4 interface debug: Updating the geometry
[0x9a8d6a0] main input debug: starting in async mode
[0x9a8d6a0] main input debug: `/home/edwin/Desktop/30.Rock.avi' successfully opened
[0x9a8d6a0] main input debug: Buffering 0%
[0x9a8d6a0] main input debug: switching to sync mode
[0x9a6ef98] packetizer_mpeg4video packetizer warning: waiting for VOL
[0x9a6ef98] packetizer_mpeg4video packetizer warning: waiting for VOL
[0x9a8d6a0] main input debug: Buffering 8%
[0x9a6dca8] mpeg_audio packetizer debug: MPGA channels:2 samplerate:48000 bitrate:32
[0x9a903a0] main stream output debug: adding a new sout input (sout_input:0x9a6fe70)
[0x9949930] stream_out_transcode stream out debug: creating audio transcoding from fcc=`mpga' to fcc=`mp4a'
[0x9b08158] main decoder debug: looking for decoder module: 31 candidates
[0x9b08158] main decoder debug: using decoder module "mpeg_audio"
[0x9b08158] main decoder debug: TIMER module_need() : 4.992 ms - Total 4.992 ms / 1 intvls (Avg 4.992 ms)
[0x9ab71f8] main encoder debug: looking for encoder module: 10 candidates
[0x9a8d6a0] main input debug: Buffering 16%
[0x9a903a0] main stream output debug: adding a new sout input (sout_input:0x98c6ec8)
[0x9a8d6a0] main input debug: Buffering 25%
[0x9a8d6a0] main input debug: Buffering 33%
[0x9a8d6a0] main input debug: Buffering 41%
[0x9a8d6a0] main input debug: Buffering 50%
[0x9a8d6a0] main input debug: Buffering 58%
[0x9a8d6a0] main input debug: Buffering 66%
[0x9a8d6a0] main input debug: Buffering 75%
[0x9a8d6a0] main input debug: Buffering 83%
[0x9a8d6a0] main input debug: Buffering 91%
[0x9a8d6a0] main input debug: Buffering 100%
[0x9a8d6a0] main input debug: Stream buffering done (325 ms in 22 ms)
[0x94d3e28] qt4 interface debug: New caching: 100
[0x94d3e28] qt4 interface debug: New caching: 100
[0x9ab71f8] avcodec encoder debug: libavcodec initialized (interface 0x342d00)
[0x9ab71f8] avcodec encoder debug: found encoder MPEG AAC Audio
[0x9ab71f8] main encoder debug: using encoder module "avcodec"
[0x9ab71f8] main encoder debug: TIMER module_need() : 143.798 ms - Total 143.798 ms / 1 intvls (Avg 143.798 ms)
[0x9949930] stream_out_transcode stream out debug: Looking for filter (mpga->s16l, channels 2->2, rate 48000->44100)
[0x9ab8608] main filter debug: looking for audio filter2 module: 8 candidates
[0x9ab8608] mpgatofixed32 filter debug: mpga->fl32, bits per sample: 0
[0x9ab8608] main filter debug: using audio filter2 module "mpgatofixed32"
[0x9ab8608] main filter debug: TIMER module_need() : 3.489 ms - Total 3.489 ms / 1 intvls (Avg 3.489 ms)
[0x9949930] main stream out debug: Filter 'mpgatofixed32' (0x9ab8608) appended to chain
[0x9a61c88] main filter debug: looking for audio filter2 module: 8 candidates
[0x9a61c88] bandlimited_resampler filter debug: fl32/48000KHz/2->fl32/44100KHz/2
[0x9a61c88] main filter debug: using audio filter2 module "bandlimited_resampler"
[0x9a61c88] main filter debug: TIMER module_need() : 2.831 ms - Total 2.831 ms / 1 intvls (Avg 2.831 ms)
[0x9949930] main stream out debug: Filter 'bandlimited_resampler' (0x9a61c88) appended to chain
[0x9a8fbd8] main filter debug: looking for audio filter2 module: 8 candidates
[0x9a8fbd8] audio_format filter debug: fl32->s16l, bits per sample: 32->16
[0x9a8fbd8] main filter debug: using audio filter2 module "audio_format"
[0x9a8fbd8] main filter debug: TIMER module_need() : 45.455 ms - Total 45.455 ms / 1 intvls (Avg 45.455 ms)
[0x9949930] main stream out debug: Filter 'audio_format' (0x9a8fbd8) appended to chain
[0x9949930] stream_out_transcode stream out debug: Got complete audio filter chain
[0x989c580] main mux debug: adding a new input
[0x989c580] mux_ts mux debug: adding input codec=mp4a pid=68
[0x989c580] mux_ts mux debug: new PCR PID is 68
[0x9949930] stream_out_transcode stream out debug: creating video transcoding from fcc=`mp4v' to fcc=`mp4v'
[0x9ac0ab8] main decoder debug: looking for decoder module: 31 candidates
[0x9ac0ab8] avcodec decoder debug: libavcodec already initialized
[0x9ac0ab8] avcodec decoder debug: using direct rendering
[0x9ac0ab8] avcodec decoder debug: ffmpeg codec (MPEG-4 Video) started
[0x9ac0ab8] main decoder debug: using decoder module "avcodec"
[0x9ac0ab8] main decoder debug: TIMER module_need() : 6.918 ms - Total 6.918 ms / 1 intvls (Avg 6.918 ms)
[0x9afef10] main encoder debug: looking for encoder module: 10 candidates
[0x9afef10] avcodec encoder debug: libavcodec already initialized
[0x9afef10] avcodec encoder debug: found encoder MPEG-4 Video
[0x9afef10] main encoder debug: using encoder module "avcodec"
[0x9afef10] main encoder debug: TIMER module_need() : 12.538 ms - Total 12.538 ms / 1 intvls (Avg 12.538 ms)
[0x9afef10] main encoder debug: removing module "avcodec"
[0x9a8d6a0] main input debug: Decoder buffering done in 232 ms
[0x9b08158] mpeg_audio decoder debug: MPGA channels:2 samplerate:48000 bitrate:32
[0x9949930] stream_out_transcode stream out debug: drift is too high, resetting master sync
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9ab8608] mpgatofixed32 filter debug: libmad error: bad main_data_begin pointer
[0x9949930] stream_out_transcode stream out debug: late picture skipped (90555)
[0x9949930] stream_out_transcode stream out debug: late picture skipped (51465)
[0x9949930] stream_out_transcode stream out debug: late picture skipped (54072)
[0x9949930] stream_out_transcode stream out debug: drift is too high, resetting master sync
[0x9949930] stream_out_transcode stream out debug: decoder aspect is 765818:432000
[0x9949930] stream_out_transcode stream out debug: source pixel aspect is 1.000000:1
[0x9949930] stream_out_transcode stream out debug: scaled pixel aspect is 1.000000:1
[0x9949930] stream_out_transcode stream out debug: source 624x352, destination 624x352
[0x9949930] stream_out_transcode stream out debug: encoder aspect is 765818:432000
[0x9949930] stream_out_transcode stream out debug: destination (after video filters) 624x352
[0x9afef10] main encoder debug: looking for encoder module: 10 candidates
[0x9afef10] avcodec encoder debug: libavcodec already initialized
Invalid pixel aspect ratio 4211999/4212000, limit is 255/255
[0x9afef10] avcodec encoder error: cannot open encoder
[0x9afef10] main encoder debug: TIMER module_need() : 10.363 ms - Total 10.363 ms / 1 intvls (Avg 10.363 ms)
[0x9949930] stream_out_transcode stream out error: cannot find video encoder (module:any fourcc:mp4v)
[0x9ac0ab8] avcodec decoder debug: ffmpeg codec (MPEG-4 Video) stopped
[0x9ac0ab8] main decoder debug: removing module "avcodec"
[0x9a63d28] access_output_udp access out debug: late packet for UDP input (670582)
[0x9a63d28] access_output_udp access out debug: packet has been sent too late (672816)
[0x9a63d28] access_output_udp access out warning: putting two PCRs at once
[0x9a63d28] access_output_udp access out debug: late packet for UDP input (540685)
[0x9a63d28] access_output_udp access out debug: packet has been sent too late (541608)


```

---

### Post by andrew.46 on 2010-01-30
Hi dr_latino999,

If you are still interested in building vlc perhaps you could test the following:

Some assistance with writing a guide for building the git vlc under Ubuntu?
[http://ubuntuforums.org/showthread.php?p=8746949](http://ubuntuforums.org/showthread.php?p=8746949)

Still a few holes in it particularly with the 64bit installation but I would welcome as many people as possible to try it out. I aim to publish it on these forums as an actual guide in 'Tutorials and Tips' in April/May.

Andrew

---

### Post by dr_latino999 on 2010-02-01
> **andrew.46 said:**
> Hi dr_latino999,

If you are still interested in building vlc perhaps you could test the following:

Some assistance with writing a guide for building the git vlc under Ubuntu?
[http://ubuntuforums.org/showthread.php?p=8746949](http://ubuntuforums.org/showthread.php?p=8746949)

Still a few holes in it particularly with the 64bit installation but I would welcome as many people as possible to try it out. I aim to publish it on these forums as an actual guide in 'Tutorials and Tips' in April/May.

Andrew

Took a shot at it, and posted my results.

---

