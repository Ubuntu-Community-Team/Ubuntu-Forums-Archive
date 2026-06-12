---
title: "ffmpeg +x264  ogv &gt; mp4  beste conversion way?"
date: 2010-07-08
forum: Multimedia Software
---

### Post by Stoneface on 2010-07-08
I do several screen recordings using gtkrecordMyDesktop. Files are stored as .ogv. To store files @ Vimeo I need to convert them as Vimeo does not seem to accept .gv files. So I convert my files to mp4. Quality is OK, but mp4 quality is definitely less than the .ogv quality. Here is the command I use:```
ffmpeg -i file.ogv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 file.mp4
``` Does anyone here have any recommendations to improve the output?

During the conversion there is a warning:
```
FFmpeg version SVN-r23823, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 27 2010 07:31:33 with gcc 4.4.4
  configuration: --prefix=/usr --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.78. 0 / 52.78. 0
  libavformat   52.71. 0 / 52.71. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
**[ogg @ 0xa96d510] max_analyze_duration reached**
```
Does this cause quality loss?

Final note: mp4 is way smaller in size than the ogv, is this normal?

---

### Post by FakeOutdoorsman on 2010-07-08
> **Stoneface said:**
> Does anyone here have any recommendations to improve the output?

Going from one lossy format to another will show generational quality loss.  You can adjust the *crf* value to attempt to reduce the quality loss (*-crf 18* can be considered roughly visually lossless, but will create a large file).  You could also output to a lossless format, but then you would end up with a humongous file.

Did you try renaming your video to a .ogg for Vimeo?  This extension looks like it's [supported](http://vimeo.com/help/compression) by Vimeo.

> **Stoneface said:**
> During the conversion there is a warning:
```
  configuration: --prefix=/usr --enable-gpl --enable-version3 --enable-nonfree
```
Why did you install to */usr* instead of */usr/local*?  It's usually recommended to install compiled packages into */usr/local* to prevent interference with existing packages or anything from the official repository.

> **Stoneface said:**
> **[ogg @ 0xa96d510] max_analyze_duration reached**[/CODE]
Does this cause quality loss?

I'm not sure what that means.  If you can read C, then see the code that contains the warning: [libavformat/utils.c](http://git.ffmpeg.org/?p=ffmpeg;a=blob;f=libavformat/utils.c).  If it creates a working output then I don't think you'll need to worry about it.

> **Stoneface said:**
> Final note: mp4 is way smaller in size than the ogv, is this normal?
libx264 is a more efficient encoder than theora, but of course it all depends on your input file and the encoder settings.

Did you know you can use FFmpeg for recording screencasts?
[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)

---

### Post by Stoneface on 2010-07-09
> **FakeOutdoorsman said:**
> Going from one lossy format to another will show generational quality loss.  You can adjust the *crf* value to attempt to reduce the quality loss (*-crf 18* can be considered roughly visually lossless, but will create a large file).  You could also output to a lossless format, but then you would end up with a humongous file. Will read some more on loseless formats. Clearly missed that one.
> **FakeOutdoorsman said:**
> 
Did you try renaming your video to a .ogg for Vimeo?  This extension looks like it's [supported](http://vimeo.com/help/compression) by Vimeo. Really? Very interesting Thanks!

> **FakeOutdoorsman said:**
> 
Why did you install to */usr* instead of */usr/local*?  It's usually recommended to install compiled packages into */usr/local* to prevent interference with existing packages or anything from the official repository. See my replies on your ffmpeg tutorial from scratch [http://ubuntuforums.org/showthread.php?t=786095&page=108]("http://ubuntuforums.org/showthread.php?t=786095&page=108"). Something went wrong during the building and had to change a path somewhere. What to do to fix that? Rebuild I guess?


> **FakeOutdoorsman said:**
> 
I'm not sure what that means.  If you can read C, then see the code that contains the warning: [libavformat/utils.c](http://git.ffmpeg.org/?p=ffmpeg;a=blob;f=libavformat/utils.c).  If it creates a working output then I don't think you'll need to worry about it.

 OK, well I will leave that be then.
> **FakeOutdoorsman said:**
> 
Did you know you can use FFmpeg for recording screencasts?
[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)


No I did not. Will check it out!

---

### Post by FakeOutdoorsman on 2010-07-09
> **Stoneface said:**
> Something went wrong during the building and had to change a path somewhere. What to do to fix that? Rebuild I guess?

If it's working for you, then no reason to mess with it I guess...at least until you decide to update to the latest FFmpeg SVN.

---

### Post by Stoneface on 2010-07-12
> **FakeOutdoorsman said:**
> If it's working for you, then no reason to mess with it I guess...at least until you decide to update to the latest FFmpeg SVN.

Did your tutorial from scratch again and I got pretty far without the same error. The Maverick Meerkat note on X264 did the trick. Thanks for that. Only now when I want to get ffmpeg from SVN I am refused access:
```
~$ svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
svn: Can't connect to host 'svn.ffmpeg.org': Connection refused

```
Update: Downloaded it from another location, ftp-ed it to my laptop and now I have it as well. Only when I want to configure I get:```
~/ffmpeg$ ./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
bash: ./configure: Permission denied
```

Update 2 ```
$ chmod 777 -R ffmpeg
``` fixed that
After make I got ```
dpkg-deb - error: (upstream) version (`SVN-r') doesn't contain any digits
dpkg-deb: 1 errors in control file
``` doing ```
sudo checkinstall --pkgname=ffmpeg --pkgversion "4:SVN-r`svn info | grep Revision | awk '{ print $NF }'`" --backup=no --default
```

and ```
$ hash x264 ffmpeg ffplay
bash: hash: ffmpeg: not found
bash: hash: ffplay: not found
``` FFmpeg has not been installed because of this. Hard to say how this can be resolved..

---

### Post by Stoneface on 2010-07-12
Well I did a ```
make install
``` which worked. [s]I guess uninstalling will be much harder now? How would I do that if I ever wanted to? [/s] Never mind ```
sudo make uninstall
``` will do that. hopefully the next time I cann connect to FFmpeg SVN properly again.
Furthermore I got an error opening the ffmpeg man page ```
$ man ffmpeg
man: can't resolve /usr/share/man/man1/ffmpeg.1.gz: No such file or directory
``` even though it did open. Well Ffmpeg seems to be working - converting now . By the way, I did rename the .ogv to .ogg as you suggested, but it would not play after being uploaded to Vimeo. they mentioned that I had to work on the compression..?!

---

