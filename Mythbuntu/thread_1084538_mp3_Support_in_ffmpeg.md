---
title: "mp3 Support in ffmpeg"
date: 2009-03-02
forum: Mythbuntu
---

### Post by igb on 2009-03-02
I have recently gone from using Hardy to the latest Mythbuntu 8.10. I am having a problem with mp3 support in ffmppeg:

```
ffmpeg -i "/home/mythmedia/19688_20090228210000.mpg" -y -ab 64 -ac 2 -acodec mp3 -f mp3 "/media/recordings/mythtv/radio/BBC_Radio_4_Classic_Serial:_Scoop_Scoop_20090228210000.mp3" 2>&1

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
Input #0, mpegts, from '/home/mythmedia/19688_20090228210000.mpg':
  Duration: 01:00:55.2, start: 9839.298444, bitrate: 1601 kb/s
  Program 1 
    Stream #0.0[0x1b7](eng): Audio: mp2, 48000 Hz, stereo, 192 kb/s
Unknown encoder 'mp3'

```

I have installed all the "unstripped" libs, which I though would fix this problem. I have alos enabled the "Proposed" repos as per [https://bugs.launchpad.net/ubuntu/intrepid/+source/mythexport/+bug/297019]("https://bugs.launchpad.net/ubuntu/intrepid/+source/mythexport/+bug/297019") . So what am I doing wrong?

Ian.

---

### Post by FakeOutdoorsman on 2009-03-02
You need to use "-acodec libmp3lame" instead of "-acodec mp3".  You also need to add a "k" after your bitrate.  Example:
```
ffmpeg -i 19688_20090228210000.mpg -ab 192k -acodec libmp3lame output.mp3
```

---

### Post by igb on 2009-03-03
Thank you, that worked. The ffmpeg developers seem to get a perverse pleasure in changing their command line switches with every release:(

Ian.

---

### Post by rhpot1991 on 2009-03-09
You should have a look at this:
[http://ubuntuforums.org/showthread.php?t=1085950](http://ubuntuforums.org/showthread.php?t=1085950)

If you install the latest from proposed, then this should work just fine.  Also please leave some comments in the bugs that way this can be pushed into Intrepid and people don't need to get the fixes from proposed.

---

### Post by prconnor@gmail.com on 2009-11-23
I still had problems with this.  My solution was found here: [HTML]https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/296922[/HTML]

Basically I had to:

```

sudo apt-get install libavcodec-unstripped-52 
```

Then it worked like a champ.  Thank you all for your help.

---

### Post by intuited on 2011-08-18
Having this problem under 10.10 -- getting the message "Unknown encoder 'mp3'" when trying to convert passing `-acodec mp3`. I get the same message if I pass `libmp3lame` or even `ogg`.

Attempting to install libavcodec-unstripped-52 gives

```
The following NEW packages will be installed:
  libavcodec-extra-52{ab} libavcodec-unstripped-52 libavutil-extra-50{ab} libdirac-encoder0{a} libopencore-amrnb0{a} libopencore-amrwb0{a} libopenjpeg2{a}
0 packages upgraded, 7 newly installed, 0 to remove and 4 not upgraded.
Need to get 3,278kB of archives. After unpacking 7,500kB will be used.
The following packages have unmet dependencies:
  libavutil-extra-50: Conflicts: libavutil50 but 4:0.6-2ubuntu6.1 is installed.
  libavcodec-extra-52: Conflicts: libavcodec52 but 4:0.6-2ubuntu6.1 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1) libavcodec52
2) libavutil50

Accept this solution? [Y/n/q/?] q

```

What's going on here? Why are there two different pairs of packages that seem to do the same thing?

Also: if I run `ffmpeg -codecs` it lists mp3 as one of the available codecs. Is that a different bug?

---

