---
title: "mplayer: &quot;no stream found to handle url dvdnav://&quot;"
date: 2015-05-19
forum: Multimedia Software
---

### Post by George Heine on 2015-05-19
Since my upgrade to 14.04 LTS, mplayer with dvdnav option completely fails. Using the command I frequently used in the past to test iso images before writing them to disc, the result is now:

```
$ mplayer dvdnav:// iso-image/
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Loading protocol-related profile 'protocol.dvdnav'

Playing dvdnav://.
No stream found to handle url dvdnav://

Playing iso-image/.
libavformat version 54.20.4 (external)
Mismatching header version 54.20.3

Exiting... (End of file)

```

In case the syntax has changed, I also tried ```
mplayer -vo xv dvdnav:// -dvd-device iso-image
``` with identical results, i.e., "no stream found to handle url dvdnav://

mplayer itself works with ordinary videos as input, so something like ```
$ mplayer  -dvd-device iso-image/VIDEO_TS/VTS_01_1.VOB 
``` plays without problem.

Several months ago there was a  [ thread]("http://ubuntuforums.org/showthread.php?t=2265490") in this forum where another user reported mplayer with dvdnav failed (although their problem seemed entirely different than mine).   However, there seemed to be mention that 1) it might be necessary to download source and compile with dvdnav enabed; 2) the versions of mplayer and ffmpeg must be compatible.  In case it is relevant, here is my ffmpeg information:

```

$ ffmpeg -buildconf
ffmpeg version 2.4.git Copyright (c) 2000-2014 the FFmpeg developers
  built on Oct 23 2014 10:19:13 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --prefix=/home/gheine/ffmpeg_build --extra-cflags=-I/home/gheine/ffmpeg_build/include --extra-ldflags=-L/home/gheine/ffmpeg_build/lib --bindir=/home/gheine/bin --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      54. 10.100 / 54. 10.100
  libavcodec     56.  8.102 / 56.  8.102
  libavformat    56.  9.101 / 56.  9.101
  libavdevice    56.  1.100 / 56.  1.100
  libavfilter     5.  2.100 /  5.  2.100
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  3.100 / 53.  3.100

  configuration:
    --prefix=/home/gheine/ffmpeg_build
    --extra-cflags=-I/home/gheine/ffmpeg_build/include
    --extra-ldflags=-L/home/gheine/ffmpeg_build/lib
    --bindir=/home/gheine/bin
    --enable-gpl
    --enable-libass
    --enable-libfdk-aac
    --enable-libfreetype
    --enable-libmp3lame
    --enable-libopus
    --enable-libtheora
    --enable-libvorbis
    --enable-libvpx
    --enable-libx264
    --enable-nonfree
    --enable-x11grab

```

Any help here would be very much appreciated.

---

### Post by mc4man on 2015-05-19
If there is an iso file inside of iso-image, (assuming it's a folder),  then add it to command's path. If there is only a VIDEO_TS folder inside  then not sure why you say - 
> to test **iso images** before writing them to disc
How can you test or play  what isn't there?

(- on a VIDEO_TS folder itself various ways  - 
mplayer  -dvd-device iso-image/  dvd:// (- or ... dvd://1 or dvd://2 ect.
or
mplayer dvdnav://  -dvd-device iso-image/  
or  more variations of the 2 above...

If iso-image is an actual iso  then lose the / in your orig command, but then it should be a  .iso

---

### Post by George Heine on 2015-05-21
Thank you for your reply.

Created an actual image file with  ```
genisoimage -dvd-video -o image.iso iso-image/
```.
Using the first of your suggestions gives the same result as before:
```
$ mplayer dvdnav:// -dvd-device image.iso 
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Loading protocol-related profile 'protocol.dvdnav'

Playing dvdnav://.
No stream found to handle url dvdnav://

```

Using the second syntax you suggested:
```
$ mplayer  -dvd-device image.iso dvd://
```
 does play the video, but the top-level menu is missing. Isn't that what "dvdnav" is for?
Tried replacing "dvd://"  with "dvdnav://" and once again, got the "No stream found to handle" error.

Again, thanks for any assistance.

---

### Post by mc4man on 2015-05-21
Then maybe try a newer version of mplayer or test your .iso(s) with vlc instead. (14.04 ubuntu mplayer is quite old
Considering you've built your own ffmpeg (which is not used by mplayer at all), take a look here - 
[http://ubuntuforums.org/showthread.php?t=2149564](http://ubuntuforums.org/showthread.php?t=2149564)
Above will give you latest  svn mplayer with latest ffmpeg git

I use from here, because mplayer dev has slowed to a crawl isn't updated more than occasionally, currently  SVN-r37373, due for an update I guess..
[https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test](https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test)

---

### Post by andrew.46 on 2015-05-21
Hmmm... that guide now lags a little with the DVD section as newer libraries are all out...

---

### Post by George Heine on 2015-05-22
Thanks to both of you for your assistance.

> Hmmm... that guide now lags a little with the DVD section as newer libraries are all out...

Read to the end of the thread, and saw that Andrew.46 is now advising readers to go to a more up-to-date guide at [http://www.andrews-corner.org/ubuntu/mplayer.html](http://www.andrews-corner.org/ubuntu/mplayer.html). That guide is written for 15.04. Any problems foreseen in using it for 14.04 ?

---

### Post by mc4man on 2015-05-22
> **George Heine said:**
> Thanks to both of you for your assistance.



Read to the end of the thread, and saw that Andrew.46 is now advising readers to go to a more up-to-date guide at [http://www.andrews-corner.org/ubuntu/mplayer.html](http://www.andrews-corner.org/ubuntu/mplayer.html). That guide is written for 15.04. Any problems foreseen in using it for 14.04 ?
You should be fine using that guide in 14.04. If the apt-get  commands have issue then post back, easily resolved though I think it should be ok.

---

### Post by andrew.46 on 2015-05-22
> **George Heine said:**
> 
Read to the end of the thread, and saw that Andrew.46 is now advising readers to go to a more up-to-date guide at [http://www.andrews-corner.org/ubuntu/mplayer.html](http://www.andrews-corner.org/ubuntu/mplayer.html). That guide is written for 15.04. 

Well, not so much go to the website but just be aware that development has stalled a little on the Forum's mplayer guide while being still active on the website :)

---

### Post by George Heine on 2015-05-25
Thank you again.  Successfully used the guide in [http://www.andrews-corner.org/ubuntu/mplayer.html](http://www.andrews-corner.org/ubuntu/mplayer.html) to install and compile a version of mplayer that displays and interacts with dvd menus.  (Did not install the gui engine smplayer.)   Will mark this thread as "solved".  But I have two questions:

1) During the final compilation process (step 3 in the guide), system paused at one point and asked if I wanted to "check in" ffmpeg, or quit, so of course I answered "yes". Unfortunately, did not record the exact text of the message.  What was this about?

2) As a side effect of uninstalling the repository libdvdnav and libdvdread packages, the program "dvdauthor" was also removed.   Dvdauthor is the tool I use to create video images.  So I need to either find a dvdauthor source that uses the newer libraries, and presumably edit its makefile, or create symlinks to the libraries installed in $HOME/mplayer_build, or else (yuck) reinstall the repo packages.   Any ideas?

---

### Post by mc4man on 2015-05-25
1. is that mplayer now checks out the latest ffmpeg git in a fresh svn source build rather than include it in the mplayer source.
2. - well you could rebuild dvdauthor or let me take a look at that. I use libdvdread4 version 5.0.x here but it supplies libdvdread.so.4.x.x 
Or could you check & see did your build create  libdvdread.so.5.x.x  or  libdvdread.so.4.x.x

---

### Post by mc4man on 2015-05-25
> **mc4man said:**
> 
2. - well you could rebuild dvdauthor or let me take a look at that. I use libdvdread4 version 5.0.x here but it supplies libdvdread.so.4.x.x 
Or could you check & see did your build create  libdvdread.so.5.x.x  or  libdvdread.so.4.x.x

I just did a quick look. So Andrew needs to adjust this as it is still libdvdread4 & libdvdnav4 (ver. 5) but the .so is still 4
Ex. - for libdvdread the .so produced is libdvdread.so.4.2.0
So the checkinstall should be changed to - 
--pkgname libdvdread4
--pkgname libdvdnav4

It's possible y ou could simply cd back to both sources in turn & re-run the checkinstall command but add the 4 to both commands

---

### Post by mc4man on 2015-05-25
To Andrew - possibly some consideration to this still applicable patch. May have been towards corner cases & not any current value or maybe still useful ??

---

### Post by andrew.46 on 2015-05-26
Hmmm.... one of the reasons I am not so active in Ubuntu any more is this ghastly chain of dependencies that wraps Ubuntu like barbed wire. Sigh.....

---

### Post by mc4man on 2015-05-26
@ George 
You could also just re-install both libdvdread4 & libdvdnav4 from the repos. Not the best solution but would satisfy package deps & they install to a different location. 
Your apps that use these libs would use the ones you built as /usr/local is found first by ldconfig

Best is to just give your new builds    proper package names..

---

### Post by andrew.46 on 2015-05-26
> **mc4man said:**
> You could also just re-install both libdvdread4 & libdvdnav4 from the repos. Not the best solution but would satisfy package deps & they install to a different location. 

On my guide I have removed the compiling instructions for both and reverted to the older repository libraries. Exasperating...

---

### Post by George Heine on 2015-05-27
> 1. is that mplayer now checks out the latest ffmpeg git in a fresh svn  source build rather than include it in the mplayer source.
If I understand this, the new build of mplayer will use its own version of ffmpeg, which may be different than the version I previously built.  And if I had checked "no", it would have used the existing ffmpeg.

> 2. - well you could rebuild dvdauthor or let me take a look at that. I  use libdvdread4 version 5.0.x here but it supplies libdvdread.so.4.x.x 
Or could you check & see did your build create  libdvdread.so.5.x.x  or  libdvdread.so.4.x.x
It looks like the mplayer build actually created  so.4.2.0 versions:
```
ls -ltr /usr/local/lib
...
drwxr-xr-x 2 root root   12288 May 24 18:11 codecs
-rwxr-xr-x 1 root root   95632 May 24 18:21 libilbc.so.2.0.2
lrwxrwxrwx 1 root root      16 May 24 18:21 libilbc.so.2 -> libilbc.so.2.0.2
lrwxrwxrwx 1 root root      16 May 24 18:21 libilbc.so -> libilbc.so.2.0.2
-rwxr-xr-x 1 root root     950 May 24 18:21 libilbc.la
-rw-r--r-- 1 root root  631644 May 24 18:21 libilbc.a
-rwxr-xr-x 1 root root   30112 May 24 18:24 libdvdcss.so.2.2.0
lrwxrwxrwx 1 root root      18 May 24 18:24 libdvdcss.so.2 -> libdvdcss.so.2.2.0
lrwxrwxrwx 1 root root      18 May 24 18:24 libdvdcss.so -> libdvdcss.so.2.2.0
-rwxr-xr-x 1 root root     930 May 24 18:24 libdvdcss.la
-rw-r--r-- 1 root root  119950 May 24 18:24 libdvdcss.a
-rwxr-xr-x 1 root root  124556 May 24 18:25 libdvdread.so.4.2.0
lrwxrwxrwx 1 root root      19 May 24 18:25 libdvdread.so.4 -> libdvdread.so.4.2.0
lrwxrwxrwx 1 root root      19 May 24 18:25 libdvdread.so -> libdvdread.so.4.2.0
-rwxr-xr-x 1 root root     942 May 24 18:25 libdvdread.la
-rw-r--r-- 1 root root  513970 May 24 18:25 libdvdread.a
-rwxr-xr-x 1 root root   87640 May 24 18:26 libdvdnav.so.4.2.0
lrwxrwxrwx 1 root root      18 May 24 18:26 libdvdnav.so.4 -> libdvdnav.so.4.2.0
lrwxrwxrwx 1 root root      18 May 24 18:26 libdvdnav.so -> libdvdnav.so.4.2.0
-rwxr-xr-x 1 root root     991 May 24 18:26 libdvdnav.la
-rw-r--r-- 1 root root  519300 May 24 18:26 libdvdnav.a
drwxr-xr-x 2 root root    4096 May 24 18:26 pkgconfig

```

Being a little short of time at the moment, I just re-installed dvdauthor from the repos.  This put versions .so.4.1.2 in /usr/lib.  But, if I understand comments in this thread, these could actually be deleted, since dvdauthor will find the 4.2.0 versions in /usr/local/lib first.

---

### Post by mc4man on 2015-05-27
If you delete the repo dvdread & nav packages you'll lose dvdauthor again. The comment was dvdauthor will likely use the .so(s) you built & installed to /usr/local/
So you could just leave alone or as mentioned try redo the builds for dvdread & then dvdnav using the mentioned 4 edit, then remove the checkinstall libdvdread & libdvdnav packages from before
(- I'd just leave alone if you don't have the time..

---

