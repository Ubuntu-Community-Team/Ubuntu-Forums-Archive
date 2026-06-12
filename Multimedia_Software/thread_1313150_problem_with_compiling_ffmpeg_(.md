---
title: "problem with compiling ffmpeg :("
date: 2009-11-03
forum: Multimedia Software
---

### Post by mibungu on 2009-11-03
ffmpeg: symbol lookup error: /usr/local/lib/libavdevice.so.52: undefined symbol: av_free_packet


I tried compiling ffmpeg like following the thread on the forum , but I keep on getting this error

I'm busy with a schoolproject got this cam today sony HDR-XR100 but only stressing with ffmpeg


:(

---

### Post by mc4man on 2009-11-03
If you followed this guide
[http://ubuntuforums.org/showthread.php?t=78609](http://ubuntuforums.org/showthread.php?t=78609)

then the 2 most likely causes of that error would be ...
you had --enabled-shared in your ffmpeg config

you have the repo ffmpeg package somehow still  installed (usr/bin/ffmpeg

---

### Post by mibungu on 2009-11-03
just frustrating

---

### Post by FakeOutdoorsman on 2009-11-03
> **mibungu said:**
> ffmpeg: symbol lookup error: /usr/local/lib/libavdevice.so.52: undefined symbol: av_free_packet


I tried compiling ffmpeg like following the thread on the forum , but I keep on getting this error

I'm busy with a schoolproject got this cam today sony HDR-XR100 but only stressing with ffmpeg


:(

Show your FFmpeg command and the complete FFmpeg output.  Which thread did you follow to compile FFmpeg?  There are some outdated ones floating around I think.  Also show the output of:
```
dpkg --get-selections | egrep "x264|libavcodec"
```
Are you using any third-party repositories?

---

### Post by mibungu on 2009-11-04
dpkg --get-selections | egrep "x264|libavcodec"
libavcodec52					install
libx264-65					install
libx264-78					install
libx264-dev					install
openshot-x264					install

> Are you using any third-party repositories? 

I have cinelerra installed that's it
And I enabled the two ubuntu third-party repo's

I now notice the --enabled-shared after I did 
sudo apt-get install ffmpeg libavcodec-unstripped-52

but No succes yet

---

### Post by mibungu on 2009-11-04
Is it best to remove ffmpeg and start anew
and make sure there is nothing left before starting with compiling it ?

Fakeoutdoorsman


mibungu

---

### Post by FakeOutdoorsman on 2009-11-04
Yes, it is best to remove ffmpeg, x264, and libx264-dev before compiling FFmpeg.  However, you have several third-party repositories enabled and I am unsure if they would interfere with the installation.  I am guessing that you have the openshot repository enabled and I have seen some users on these forums experience issues due to this repository.

---

### Post by mibungu on 2009-11-04
I installed openshot with the .deb files and didn't enable an openshot repo will that go by itself


should I follow your thread then on recompiling FFmpeg

---

### Post by FakeOutdoorsman on 2009-11-04
> **mibungu said:**
> should I follow your thread then on recompiling FFmpeg

Sure, try it:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by mibungu on 2009-11-04
> (Reading database ... 142116 files and directories currently installed.)
Unpacking x264 (from .../x264_1:0.svn20091104-0.0ubuntu1-1_i386.deb) ...
dpkg: error processing /home/ba/x264/x264_1:0.svn20091104-0.0ubuntu1-1_i386.deb (--install):
 trying to overwrite `/usr/local/bin/x264', which is also in package openshot-x264
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/ba/x264/x264_1:0.svn20091104-0.0ubuntu1-1_i386.deb
/var/tmp/tmp.nqnzlWrKiD/dpkginstall.log (END) 


Well does this mean that the openshot package is giving me the trouble. I deleted openshot but probably not everything has removed. What's best then?
mibungu

---

### Post by mibungu on 2009-11-04
Now I removed cinelerra too. it is getting worse. I have a clean kubuntu install I think I'll try it on that one recompile ffmpeg an then try installing cinelerra again 

oohnoo
This is like when I just started ubuntu 3 years ago 

:mad:

---

### Post by FakeOutdoorsman on 2009-11-04
> **mibungu said:**
> Well does this mean that the openshot package is giving me the trouble. I deleted openshot but probably not everything has removed. What's best then?
mibungu

You need to remove *openshot-x264*:
```
sudo apt-get remove openshot-x264
```

---

### Post by mibungu on 2009-11-04
Well thnx anyway. Went to synaptic and wrote openshot and removed whatever was still there and recompiled. I might install openshot again cause I use it too, hope nothing goes wrong . still need to decode and see whether everything goes 


Thnx:KS

---

