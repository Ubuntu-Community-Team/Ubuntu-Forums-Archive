---
title: "ffmpeg segmentation fault"
date: 2010-08-22
forum: Multimedia Software
---

### Post by ilna on 2010-08-22
Up to date Kubuntu Lucid is in use with medibuntu sources being added. The problem doesn't depend on X environment (the same problem taked place before X starting at all).

Console output is below. **The file is playing back by gxine without any problems!**

```
$ ffmpeg -i 1.mp4 
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
Segmentation fault
```

With mplayer: 

```
$ mplayer 1.mp4 
MPlayer 1.0rc3-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not open config files /home/anli/.lircrc and /etc/lirc//lirc/lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.

Playing 1.mp4.
libavformat file format detected.


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]
```

Trying to install mplayer dbg symbols:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libavcodec-extra-52 libavdevice-extra-52 libavformat-extra-52 libavutil-extra-49 libpostproc-extra-51 libswscale-extra-0 
The following NEW packages will be installed:
  ffmpeg-dbg{a} libavcodec52{a} libavdevice52{a} libavformat52{a} libavutil49{a} libpostproc51{a} libswscale0{a} mplayer-dbg 
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.4MB of archives. After unpacking 38.3MB will be used.
The following packages have unmet dependencies:
  libavformat-extra-52: Conflicts: libavformat52 but 4:0.5.1-1ubuntu1 is to be installed.
  libavdevice-extra-52: Conflicts: libavdevice52 but 4:0.5.1-1ubuntu1 is to be installed.
  libavutil-extra-49: Conflicts: libavutil49 but 4:0.5.1-1ubuntu1 is to be installed.
  libpostproc-extra-51: Conflicts: libpostproc51 but 4:0.5.1-1ubuntu1 is to be installed.
  libswscale-extra-0: Conflicts: libswscale0 but 4:0.5.1-1ubuntu1 is to be installed.
  libavcodec-extra-52: Conflicts: libavcodec52 but 4:0.5.1-1ubuntu1 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
libavdevice-extra-52

Keep the following packages at their current version:
ffmpeg-dbg [Not Installed]
libavcodec52 [Not Installed]
libavformat52 [Not Installed]
libavutil49 [Not Installed]
libpostproc51 [Not Installed]
libswscale0 [Not Installed]

Leave the following dependencies unresolved:
mplayer-dbg recommends ffmpeg-dbg
Score is -25
```

The same for ffmpeg-dbg:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libavcodec-extra-52 libavdevice-extra-52 libavformat-extra-52 libavutil-extra-49 libpostproc-extra-51 libswscale-extra-0 
The following NEW packages will be installed:
  ffmpeg-dbg libavcodec52{a} libavdevice52{a} libavformat52{a} libavutil49{a} libpostproc51{a} libswscale0{a} 
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,289kB of archives. After unpacking 25.3MB will be used.
The following packages have unmet dependencies:
  libavformat-extra-52: Conflicts: libavformat52 but 4:0.5.1-1ubuntu1 is to be installed.
  libavdevice-extra-52: Conflicts: libavdevice52 but 4:0.5.1-1ubuntu1 is to be installed.
  libavutil-extra-49: Conflicts: libavutil49 but 4:0.5.1-1ubuntu1 is to be installed.
  libpostproc-extra-51: Conflicts: libpostproc51 but 4:0.5.1-1ubuntu1 is to be installed.
  libswscale-extra-0: Conflicts: libswscale0 but 4:0.5.1-1ubuntu1 is to be installed.
  libavcodec-extra-52: Conflicts: libavcodec52 but 4:0.5.1-1ubuntu1 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
devede
dvd-slideshow
dvdstyler
libavcodec-extra-52
libavdevice-extra-52
libavfilter-extra-0
libavformat-extra-52
libavutil-extra-49
libpostproc-extra-51
libswscale-extra-0
mandvd

Install the following packages:
libavfilter0 [4:0.5.1-1ubuntu1 (lucid)]

Leave the following dependencies unresolved:
kubuntu-restricted-extras recommends libavcodec-extra-52
ubuntu-restricted-extras recommends libavcodec-extra-52
Score is -1400
```



**Where to dig in??** Must I reject medibuntu as being broken and try to reinstall something (what?) "more official"?

---

### Post by ilna on 2010-08-22
Have tried to:

- remove medibuntu and reinstall all related packages,
- replace all xyz-extra packages with xyz approriate packages

with the same result.

---

### Post by andrew.46 on 2010-08-22
Hi ilna,

Can you post the troublesome file somewhere?

Andrew

---

### Post by ilna on 2010-08-23
andrew.46,

Yes, it's here (about 14 MB):

[http://krishnamurti.su/tmp/1.mp4](http://krishnamurti.su/tmp/1.mp4)

---

### Post by andrew.46 on 2010-08-23
Hi ilna,

I have a slightly different version of MPlayer but it plays this file without error, I attach a screenshot to demonstrate this. FFmpeg shows:

```

andrew@skamandros~/Desktop$ ffmpeg -i 1.mp4 
FFmpeg version SVN-r24865, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 22 2010 20:39:38 with gcc 4.4.4
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc 
--enable-avfilter --enable-pthreads --enable-shared --disable-static 
--disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libfaac 
--enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3
 --enable-zlib --enable-libvpx --enable-libgsm --enable-nonfree 
--enable-gpl
  libavutil     50.24. 0 / 50.24. 0
  libavcore      0. 6. 0 /  0. 6. 0
  libavcodec    52.85. 1 / 52.85. 1
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.37. 0 /  1.37. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf52.40.0
  Duration: 00:06:10.28, start: 0.000000, bitrate: 308 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 320x246, 176 kb/s, 25 fps, 25 tbr, 25 tbn, 50 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 127 kb/s
At least one output file must be specified

```

Perhaps reinstall your copy of FFmpeg and MPlayer, or better still look on these forums for a suitable guide to upgrade both to current svn. Looks like you have some broken packages in there too which could very well be at the root of the problem...

Andrew

---

### Post by ilna on 2010-08-23
Andrew, do you use ffmpeg, mplayer/mencoder and all those related libs from SVN? Have you followed some concrete instructions?

OTOH, I'm not a big video user, and "official software update way" would be preferrable - at case it is possible to resolve the issue keeping this way :) 

It is interesting, I have not found any related bugs, so I suppose, there is something wrong with my configuration (there were occasions of adding and removing different ppas, probably some trails still exist). There are plenty video files causing segfault - not uploaded one only.

---

### Post by ilna on 2010-08-23
And - yes, I have tried to reinstall plenty of packages listed by apt-rdepends for ffmpeg.

---

### Post by andrew.46 on 2010-08-23
Hi ilna,

> **ilna said:**
> Andrew, do you use ffmpeg, mplayer/mencoder and all those related libs from SVN? Have you followed some concrete instructions?

One I followed, one I wrote:

HOWTO: Install and use the latest FFmpeg and x264 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Howto: Build the svn MPlayer under the latest release version of Ubuntu 
[http://ubuntuforums.org/showthread.php?t=1542240&](http://ubuntuforums.org/showthread.php?t=1542240&)

> OTOH, I'm not a big video user, and "official software update way" would be preferrable - at case it is possible to resolve the issue keeping this way :) 

Well to tell the truth there is nothing special about the makeup of that particular video: h264 video + aac sound in an mp4 container, it should not segfault the repository MPlayer + FFmpeg. But I am not sure of the best way to diagnose the exact fault with your libav* packages, for which my apologies :(.

Andrew

---

### Post by endotherm on 2010-08-23
not sure if this helps, but i and several of my colleagues have been having trouble with mplayer/smplayer (from the ppa's) since receiving the LibAVCodec52 upgrade a few weeks ago.

---

### Post by ilna on 2010-08-23
> **andrew.46 said:**
> But I am not sure of the best way to diagnose the exact fault with your libav* packages, for which my apologies :(.Andrew, apologies are not approriate here :) Thanks for your compassion!

---

### Post by ilna on 2010-08-23
> **endotherm said:**
> not sure if this helps, but i and several of my colleagues have been having trouble with mplayer/smplayer (from the ppa's) since receiving the LibAVCodec52 upgrade a few weeks ago.

endotherm, which ppas do you mean? I have proposed and backports (besides of standard ones). And this one lib's package is installed:

libavcodec-extra-52  4:0.5.1-1ubuntu1

---

### Post by endotherm on 2010-08-23
> **ilna said:**
> endotherm, which ppas do you mean? I have proposed and backports (besides of standard ones). And this one lib's package is installed:

libavcodec-extra-52  4:0.5.1-1ubuntu1


these repos are maintained by RVM the smplayer lead:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

thats the package. everything started getting slowly out of wack after getting that update.

---

### Post by ilna on 2010-08-23
> **endotherm said:**
> these repos are maintained by RVM the smplayer lead:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

thats the package. everything started getting slowly out of wack after getting that update.No, I have not used these ppas.

---

### Post by mc4man on 2010-08-23
A couple of things - 
I wouldn't use the proposed repo, it's mainly for testing proposed updates and can sometimes cause issues, so I'd disable it and then run a sudo apt-get update.

What you may want to do is remove all the effected packages and re-install, if so, being on kubuntu I'd install synaptic,
It's easier to see what's going on and will keep a history for you under the 'file' tab.
```
sudo apt-get install synaptic
```

You can leave medibuntu as a source for the moment, though the website seems to have a few issues atm.


If you want to do so then open synaptic, search ffmpeg and mark for complete removal ffmpeg and all the libs starting with libavcodecXX (up to 7 in all, scroll down

You'll lose some players, apps and plugins, no matter, you can re-install.
(you can also remove kubuntu and ubuntu-restricted-extras - they are just meta packages and not needed

Then go back into synaptic and install the extra versions of libavcodec, libavformat ect. When done install ffmpeg and test it.
If all is well then re-install anything else that was removed or you want. (file -history in synaptic will show you

edit

atm I'd also use apt-get instead of aptitude when needed

---

### Post by ilna on 2010-08-23
mc4man,

I have tried to remove 'proposed', delete all mplayer and ffmpeg with all related chain ('extra' variants were replaced with 'extra'-less ones, among other deletions) and install again ffmpeg and Ko. Have got the same result.

BTW, I use aptitude. Why do you prefer apt-get?

---

### Post by mc4man on 2010-08-23
Not sure where your problem lies..

i use maverick but have a lucid install I'm not using. So I removed all my related packages (ffmpeg, all the ffmpeg libs, mplayer, ect.

Then I added proposed, fully updated and rebooted.
After adding medibuntu as a source (there where some issues there, got some 404 not found messages, any way got it added.

Then using your preferred method ran this - (shows why I don't like aptitude - it removes all packages marked as auto installed, sometimes I don't want them removed.
```
sudo aptitude install ffmpeg libavcodec-extra-52 mplayer
```

> doug@doug-desktop:~$ sudo aptitude install ffmpeg libavcodec-extra-52 mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following [COLOR="Blue"]NEW packages[/COLOR] will be installed:
  ffmpeg libavcodec-extra-52 libavdevice52{a} libavfilter0{a} 
  libavformat52{a} libavutil-extra-49{a} libpostproc51{a} libswscale0{a} 
  mplayer 
The following packages will be REMOVED:
  dvdrip-doc{u} dvdrip-utils{u} fping{u} gocr{u} libevent-execflow-perl{u} 
  libevent-perl{u} libevent-rpc-perl{u} libfftw3-dev{u} 
  libgtk2-ex-formfactory-perl{u} libintl-perl{u} libio-socket-ssl-perl{u} 
  libjpeg-progs{u} libmysqlclient15off{u} libnet-libidn-perl{u} 
  libnet-ssleay-perl{u} libnetpbm10{u} libofa0-dev{u} libsox-fmt-mp3{u} 
  libsox-fmt-pulse{u} libva-x11-1{u} libva1{u} libvlc5{u} libvlccore4{u} 
  libwildmidi0{u} libx264-98{u} lsdvd{u} netpbm{u} ogmtools{u} 
  transcode-doc{u} transcode-utils{u} transfig{u} vlc-data{u} 
0 packages upgraded, 9 newly installed, 32 to remove and 1 not upgraded.
Need to get 0B/8,641kB of archives. After unpacking 34.7 will be freed.
Do you want to continue? [Y/n/?] 


> Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 368408 files and directories currently installed.)
...clipped all the removal stuff
...........
Selecting previously deselected package libavutil-extra-49.
(Reading database ... 366430 files and directories currently installed.)
[COLOR="Blue"]Unpacking libavutil-extra-49 (from .../libavutil-extra-49_4%3a0.5.1-1ubuntu1+medibuntu1_i386.deb) [/COLOR]...
Selecting previously deselected package libavcodec-extra-52.
[COLOR="Blue"]Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.5.1-1ubuntu1+medibuntu1_i386.deb) ...[/COLOR]
Selecting previously deselected package libavformat52.
Unpacking libavformat52 (from .../libavformat52_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libavdevice52.
Unpacking libavdevice52 (from .../libavdevice52_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libavfilter0.
Unpacking libavfilter0 (from .../libavfilter0_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libpostproc51.
Unpacking libpostproc51 (from .../libpostproc51_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libswscale0.
Unpacking libswscale0 (from .../libswscale0_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package ffmpeg.
Unpacking ffmpeg (from .../ffmpeg_4%3a0.5.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package mplayer.
[COLOR="Blue"]Unpacking mplayer (from .../mplayer_2%3a1.0~rc3+svn20090426-1ubuntu16+medibuntu1_i386.deb[/COLOR]) ...
Processing triggers for man-db ...
Setting up libavutil-extra-49 (4:0.5.1-1ubuntu1[COLOR="Blue"]+medibuntu1[/COLOR]) ...
Setting up libavcodec-extra-52 (4:0.5.1-1ubuntu1[COLOR="Blue"]+medibuntu1[/COLOR]) ...
Setting up libavformat52 (4:0.5.1-1ubuntu1) ...
Setting up libavdevice52 (4:0.5.1-1ubuntu1) ...
Setting up libavfilter0 (4:0.5.1-1ubuntu1) ...
Setting up libpostproc51 (4:0.5.1-1ubuntu1) ...
Setting up libswscale0 (4:0.5.1-1ubuntu1) ...
Setting up ffmpeg (4:0.5.1-1ubuntu1) ...
Setting up mplayer (2:1.0~rc3+svn20090426-1ubuntu16[COLOR="Blue"]+medibuntu1[/COLOR]) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
....ect.
Afterwards all work fine - notice the blue which are gotten from medibuntu
(I believe you said you where using medibuntu, but none of your posts indicates that.

( maybe try again but run this first
```
sudo apt-get clean
```


Edit: 
could you also just browse to /usr/local/lib and /usr/local/bin and make sure there are no ffmpeg related files

(at least here, on lucid, if I run this nothing is returned (i find lucid to be very inconsistent
locate libavcodec.so

when it should show this, as it does so  in maverick 
> doug@doug-laptop:~$ locate libavcodec.so
/usr/lib/libavcodec.so
/usr/lib/libavcodec.so.52
/usr/lib/libavcodec.so.52.85.1
/usr/lib/debug/usr/lib/libavcodec.so.52.85.1
/usr/lib/debug/usr/lib/i686/cmov/libavcodec.so.52.85.1
/usr/lib/i686/cmov/libavcodec.so
/usr/lib/i686/cmov/libavcodec.so.52
/usr/lib/i686/cmov/libavcodec.so.52.85.1

---

### Post by ilna on 2010-08-24
Have tried all variants without success. Probably the issue depends on architecture (amd64 at my case), and a key information is this one from mplayer output:

```
MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM
```

---

### Post by ilna on 2010-08-24
I am tired of the software war :), and have installed ffmpeg as decribed here:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

as well as mplayer from this ppa:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

All works. Hope, 10.10 will be more workable..

---

