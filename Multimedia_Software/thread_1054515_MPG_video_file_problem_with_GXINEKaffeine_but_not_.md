---
title: "MPG video file problem with GXINE/Kaffeine but not MPLAYER/SMPLAYER"
date: 2009-01-29
forum: Multimedia Software
---

### Post by merlot on 2009-01-29
Hello,

I am using Ubuntu 8.04 (hardy) with Kernel 2.6.24.23-generic GNOME 2.22.3

I mainly use Kaffeine to watch videos, but recently (after doing an update to new kernel along with video card driver(nvidia)) Kaffeine stopped playing MPG video files (Gxine also stopped). There were some other libraries that I updated along with the kernel update, but I don't remember the names. 

Here are the details:
-MPG files are from my digital camera, so there is no DRM thing.
-GXine and Kaffeine are not playing MPG files, but MPlayer, SMPlayer, Movie Player are working great.
-There is no error message popping up.
-Other files formats (AVI,DVD, etc) are working fine with all the players.
-I tried reinstalling old video card; didn't work.
-I ran the old kernel; didn't work.
-I reinstall most of the libraries; didn't work
(unless there is a library that I am missing which needs to be reinstalled)

Syptoms:
Kaffeine:
When I click on the file, kaffeine starts but the icons in the control pannel at the bottom enables/disables frequently; like if the file is 0 sec long and after it reaches the end, it rewinds and trys to play again. 

GXine (version: 0.5.901)
I open the GXine from console by typing "gxine". The output is 

bind: No such file or directory
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/merlot/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location
warning: configuration item media.dvd.raw_device points to a non-existent location /dev/rdvd
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0
warning: configuration item decoder.external.real_codecs_path points to a non-existent location
warning: configuration item decoder.external.win32_codecs_path points to a non-existent location /usr/lib/codecs
warning: configuration item subtitles.separate.font_freetype points to a non-existent location
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?

After choosing the MPG file from FILE/Open, nothing happens.

Any suggestion is greatly appreciated,
Thank you

---

### Post by merlot on 2009-01-29
New update:

I realized that for some reason, /usr/lib/win32 and /usr/lib/codec was removed. I reinstalled w32codecs, so now I do have those. However, the problem with Kaffeine and GXine is still not playing MPG files.

I did install Kaffeine-gstreamer package and by using that, Kaffeine is capable of playing MPG files. However, when I switch the player engine to Kaffeine-xine it doesn't play.

One wierd thing is that when I get the "Track info" with engine, kaffeine-gstreamer, it says 
Length:0:03:21
Audio: MPEG 1 Audio, Layer 2
Video: MPEG-1 video, 640x480

But when select kaffeine-xine engine, track info reads:
...
Length: 0:03:21
Mime: video/mpeg
Audio: 0kb/s
Video: MPEG (libmpeg2) 640x480 (640x480)

It looks like there is an audio decoder problem, though. But I couldn't find a solution. Any ideas?

---

### Post by merlot on 2009-01-30
I solved the problem by installing an older version of xine library from [https://launchpad.net/ubuntu/hardy/+source/xine-lib/1.1.11.1-1ubuntu3](https://launchpad.net/ubuntu/hardy/+source/xine-lib/1.1.11.1-1ubuntu3) 

By downgrading the xine library from 1.1.11.1-1ubuntu3.2 to  1.1.11.1-1ubuntu3, the problem is solved. Now I can watch MPG files with kaffeine and gxine perfectly. 

However, I do not understand why there is a problem with the most recent version!?, though. It is listed under important security update, but when I do the update, things get messy. Is this a xine-lib bug?

---

### Post by ager-wick on 2009-03-14
I can confirm this, had the exact same problem and solved it by installing the previous version of libxine (+ a lot of dependencies). Here is the exact command I used:
sudo apt-get install libxine1=1.1.11.1-1ubuntu3 libxine1-console=1.1.11.1-1ubuntu3 libxine1-plugins=1.1.11.1-1ubuntu3 libxine1-misc-plugins=1.1.11.1-1ubuntu3 libxine1-x=1.1.11.1-1ubuntu3 libxine1-bin=1.1.11.1-1ubuntu3 libxine1-ffmpeg=1.1.11.1-1ubuntu3

---

### Post by ager-wick on 2009-03-14
another related tip:
to prevent "sudo aptitude upgrade" upgrading to the broken version, you can issue this command:
sudo aptitude forbid-version libxine1=1.1.11.1-1ubuntu3.2 libxine1-console=1.1.11.1-1ubuntu3.2 libxine1-plugins=1.1.11.1-1ubuntu3.2 libxine1-misc-plugins=1.1.11.1-1ubuntu3.2 libxine1-x=1.1.11.1-1ubuntu3.2 libxine1-bin=1.1.11.1-1ubuntu3.2 libxine1-ffmpeg=1.1.11.1-1ubuntu3.2

This will only block this specific version. Once a new version is available, that version will automatically be installed when you run sudo aptitude upgrade again. Hopefully the problem has been solved then.

Note: this only prevents *aptitude* from upgrading the packages, but *apt-get* will ignore this and still upgrade it, so use aptitude instead :)

---

