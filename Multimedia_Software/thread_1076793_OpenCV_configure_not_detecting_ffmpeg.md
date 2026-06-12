---
title: "OpenCV configure not detecting ffmpeg"
date: 2009-02-21
forum: Multimedia Software
---

### Post by darkzerox on 2009-02-21
I'm trying to build opencv with ffmpeg. I've tried both opencv-1.0.0 and 1.1.0, but it won't detect ffmpeg.

```

$ ffmpeg
FFmpeg version SVN-r17486, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-x11grab --enable-shared
  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.18. 0 / 52.18. 0
  libavformat   52.29. 2 / 52.29. 2
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 3. 0 /  0. 3. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb 21 2009 14:10:37, gcc: 4.3.2
At least one output file must be specified

~/Desktop/opencv-1.1.0$ ./configure | grep ffmpeg
checking ffmpeg/avcodec.h usability... no
checking ffmpeg/avcodec.h presence... no
checking for ffmpeg/avcodec.h... no
checking ffmpeg/swscale.h usability... no
checking ffmpeg/swscale.h presence... no
checking for ffmpeg/swscale.h... no
    Use ffmpeg:               no

```

Shouldn't --enable-shared with ffmpeg have put the libraries somewhere where opencv could find them?

---

### Post by FakeOutdoorsman on 2009-02-21
First install FFmpeg with --enable-shared: [ffmpeg on ubuntu 8.10 w/ enable-shared](http://ubuntuforums.org/showthread.php?t=1075835).  I know you did this already.

Now deal with OpenCV.  I looked at the Arch Linux [OpenCV PKGBUILD](http://aur.archlinux.org/packages/opencv/opencv/PKGBUILD) script which basically does the following:
```
wget http://superb-west.dl.sourceforge.net/sourceforge/opencvlibrary/opencv-1.1pre1.tar.gz
tar xzvf opencv-1.1pre1.tar.gz
cd opencv-1.1.0/
wget http://aur.archlinux.org/packages/opencv/opencv/ffmpeg.diff
patch -p1 < ffmpeg.diff
sed -e 's/ffmpeg\/avcodec.h/libavcodec\/avcodec.h/' -e 's/ffmpeg\/swscale.h/libswscale\/swscale.h/' -i configure
./configure
make
sudo checkinstall
```

---

### Post by darkzerox on 2009-02-23
Well no wonder I was having troubles. Did ffmpeg recently change their file structure or what? Doesn't seem like a good idea when other programs depend on it.

Thank you for coming to my rescue again FakeOutdoorsman! I really appreciate this. You're my hero :)

---

### Post by FakeOutdoorsman on 2009-02-23
I blame OpenCV for not keeping up.  I'm not sure why it would look for avcodec.h and such in /usr/(local)/include/ffmpeg/ instead of /usr/(local)/include/libavcodec/.

---

### Post by darkzerox on 2009-02-23
This... words can no longer express my frustration.

If anyone else is having the same problems I've been having, I have a little treat for you. I think I've actually managed to figure something out.

"cvCreateVideoWriter" has a bug, at least when running on ubuntu 8.10. It just crashes. No error message, nothing, just poof, seg fault. Unless you use CV_FOURCC_DEFAULT for the codec, then ffmpeg complains and says the codec doesn't exist.

There is a fix for this, supposedly. Furthermore, it has been applied to SVN.

```
svn co https://opencvlibrary.svn.sourceforge.net/svnroot/opencvlibrary/trunk opencvlibrary
```

But, this new version still doesn't know where to look for the ffmpeg headers. Of course, the patch FakeOutdoorsman was kind enough to share with us no longer works. Funnily enough (in a very painful way), it appears the lovely OpenCV authors fixed it for GENTOO and left UBUNTU to rot. But don't fret! The fix is easy enough.

Open opencvlibrary/opencv/src/highgui/cvcap_ffmpeg.cpp (yes, the moved the file just to screw with us) and just change all instances

#include <ffmpeg/avformat.h> --> #include <libavformat/avformat.h>
#include <ffmpeg/avcodec.h> --> #include <libavcodec/avcodec.h>
#include <ffmpeg/swscale.h> --> #include <libswscale/swscale.h>

Wonderful! Now the code is fixed, but you still have to tell "configure" where to look so it doesn't complain too. This patch still seems to work:

```
sed -e 's/ffmpeg\/avcodec.h/libavcodec\/avcodec.h/' -e 's/ffmpeg\/swscale.h/libswscale\/swscale.h/' -i configure
```

Now ./configure runs happily, but make doesn't seem to like `cxcore/cxjacobieigens.cpp'. Let's check the INSTALL file...

Looks like you can only build SVN snapshots with cmake anyway. Oops.

```
cmake .
make
```

Now it makes it to 86% before crying that 'img_convert' was not declared. Time to dig through some code again...

```
[ 86%] Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o
.../opencvlibrary/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;virtual IplImage* CvCapture_FFMPEG::retrieveFrame(int)&#8217;:
.../opencvlibrary/opencv/src/highgui/cvcap_ffmpeg.cpp:537: error: &#8216;img_convert&#8217; was not declared in this scope
```

Edit: Digging through the source code of cvcap_ffmpeg, it seems HAVE_FFMPEG_SWSCALE is not defined, and OpenCVs alternative doesn't work. I didn't configure ffmpeg to enable that, so maybe that's the problem. Let's try again...

Edit2: Disregard everything above. Read the post below. I shall leave this post here so that other newbies can learn about "problem solving" like I did.

---

### Post by darkzerox on 2009-02-23
*sigh* I lied. Forget everything I said above. Here are the new (very simple) instructions:

1. Install the latest ffmpeg svn snapshot. You need --enable-shared and --enable-swscale. This configuration seems to work good:
```
configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-x11grab --enable-shared --enable-swscale
```
You may need to 'sudo apt-get install' each of those libraries if you don't already have them (and maybe their dev's for good measure?). Try 'apt-cache search <library_name>' if you can't find it. Make sure you 'apt-get update' first. x264 might be a bit more tricky (you don't need it), read [this]("http://ubuntuforums.org/showthread.php?t=786095") if you want it. Run 'ffmpeg' to make sure its working. If it whines about av_gcd, then 'sudo apt-get remove libavutil49'.

2. Download the latest opencv svn snapshot. cd into the opencv directory
```
cmake .
make
sudo make install
```
You don't actually need any of the above hacks I mentioned. cmake and the latest opencv build will take care of it nicely. You can get cmake with 'sudo apt-get cmake' if you don't already have it.

3. One more bug, when creating a project that actually uses highgui.
```
/usr/local/lib/libhighgui.so: undefined reference to `img_convert'
```
Open opencv/src/highgui/cvcap_ffmpeg.cpp in your favorite text editor. Find and replace 'img_convert' with 'sws_scale' ("whole word" and "case sensitive" worked for me).

---

### Post by gijzelaerr on 2009-05-03
hi everyone,

I think I have an other solution that also works.

Bug report:
* [https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/311188](https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/311188)

patch:
* [http://launchpadlibrarian.net/26284558/400_fix_latest_ffmpeg.diff](http://launchpadlibrarian.net/26284558/400_fix_latest_ffmpeg.diff)

PPA with working packages:
* [https://launchpad.net/~gijzelaar/+archive/opencv](https://launchpad.net/~gijzelaar/+archive/opencv)

Easy installation instructions
* [http://gijs.pythonic.nl/blog/2009/may/3/getting-video-io-working-opencv-and-ubuntu-jaunty-/](http://gijs.pythonic.nl/blog/2009/may/3/getting-video-io-working-opencv-and-ubuntu-jaunty-/)


If you have any questions or remarks let me know,

--
Gijs Molenaar
[http://gijs,pythonic.nl](http://gijs,pythonic.nl)

---

### Post by dhalbert on 2009-05-20
I have a jaunty x86_64 system. I successfully built and tested OpenCV from its SVN trunk, as of 2009-05-18 (1765). I did not have to apply any patches to get it to build. I used the latest ffmpeg -dev libraries from the jaunty repository, not ffmpeg svn.

I didn't have any #include problems. I originally got the img_convert() undeclared error, but fixed it by installing libswscale-dev from the jaunty repositories. I also needed various other ffmpeg libraries to get all the features to be included.

I built using cmake, not autoconf. Later I tried to get autoconf to work, and got errors doing the "autoreconf -i --force" step. If I skipped that, then I got architecture mismatch problems in the build. So cmake is the way to go.

---

### Post by sayyeah on 2009-05-25
dhalbert// have you tried both reading and writing a video file ?
What kind of codec did you use for "FOURCC" when writing?

I installed opencv SVN 1765 using cmake and installed all additional ffmpeg-related dev packages(libavcodec-dev, libavdevice-dev, libavfilter-dev, libavformat-dev, libavutil-dev, libswscale-dev, and ffmpeg as default)

I found that reading video file and showing to the screen works fine but only writing does not work.

```
Output #0, avi, to 'out.avi':
    Stream #0.0: Video: 0x0000, yuv420p, 720x480, q=2-31, 22118 kb/s, 90k tbn, 3 tbc
OpenCV Error: Bad argument (codec not found) in CvVideoWriter_FFMPEG::open, file cvcap_ffmpeg.cpp, line 1250

```

Should I have installed more ffmpeg package? :(
I'm using Jaunty 9.04 32bit system, but I don't think this would make a big difference.

---

### Post by dhalbert on 2009-05-26
> **sayyeah said:**
> dhalbert// have you tried both reading and writing a video file ?
What kind of codec did you use for "FOURCC" when writing?
I was mostly just reporting build success with the OpenCV SVN version.

After seeing your query, I tried some examples, and have had success reading .MPG files and writing to FOURCC "MJPG" .AVI's. Oddly, when I do this, I get the error **(ERROR)icvOpenAVI_XINE(): Unable to open source 'foo.mpg'** but it still works (!). However, I cannot read most files, such as the same MJPG I just produced, or an MP42 file. Some produce segmentation faults, and some just produce error messages. I am mostly working with still images and so haven't spent much time trying to debug the video issues. Sorry I can't be more helpful.

---

### Post by DanyUP on 2009-06-04
I followed all the instructions above but I got this error while opening an avi file:
```
/home/daniele/workspace/OpenCV/Debug/OpenCV: symbol lookup error: /usr/local/lib/libhighgui.so.1.1: undefined symbol: av_free_packet
```

What's wrong?

---

### Post by tsgates on 2009-07-19
Hi, all. After I spent a couple of hours to work with ffmpeg, cvCreateVideoWriter in Ubuntu 9.04, I completed to record video with python-opencv binding. To see an example using pygame, python-opencv, visit [http://blog.taesoo.org/?p=210](http://blog.taesoo.org/?p=210) . Thanks.

---

### Post by jacasoj on 2009-08-03
> **DanyUP said:**
> I followed all the instructions above but I got this error while opening an avi file:
```
/home/daniele/workspace/OpenCV/Debug/OpenCV: symbol lookup error: /usr/local/lib/libhighgui.so.1.1: undefined symbol: av_free_packet
```What's wrong?
Hi DanyUP! Just wanted to ask you if you managed to solve:
> symbol lookup error: /usr/local/lib/libhighgui.so.1.1: undefined symbol: av_free_packetI'm having the same problem and have no key on how to solve it.

---

### Post by gary29 on 2009-08-18
> **FakeOutdoorsman said:**
> First install FFmpeg with....

Thanks VERY much for this explanation.  Am new to linux packages and open source, but was banging my head against everything when it refused to work before.  I think the ffmpeg diff patch was the step that tied it all together at last.  

You and **darkzerox** seem to have sorted a lot of the problems I'm experiencing, so I'm reading your posts with great interest.  :)

Cheers
Gary

---

### Post by Jesus on 2009-10-03
> **DanyUP said:**
> I followed all the instructions above but I got this error while opening an avi file:
```
/home/daniele/workspace/OpenCV/Debug/OpenCV: symbol lookup error: /usr/local/lib/libhighgui.so.1.1: undefined symbol: av_free_packet
```

What's wrong?

> **jacasoj said:**
> Hi DanyUP! Just wanted to ask you if you managed to solve:
I'm having the same problem and have no key on how to solve it.

You need to make sure /usr/local/lib/ is in $LD_LIBRARY_PATH. Do the following:

```
export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
```

Then run the binary. Should work. Add the above to your .bashrc so you don't need to do it every time you start a new shell.

---

### Post by Odoacer on 2009-11-20
> **Jesus said:**
> You need to make sure /usr/local/lib/ is in $LD_LIBRARY_PATH. Do the following:

```
export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
```

Then run the binary. Should work. Add the above to your .bashrc so you don't need to do it every time you start a new shell.

ffmpeg (from svn) broke when I upgraded to karmic. This fix worked for me.

---

### Post by pratik069 on 2010-01-03
I'm a newbie to Ubuntu and have recently upgraded from 9.04 to 9.10 karmic version of ubuntu.
I'm trying to install opencv on this version but i'm getting the following error after executing the make command

make[2]: *** [lib_highgui_la-cvcap_ffmpeg.lo] Error 1
make[2]: Leaving directory `/home/jani/opencv/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jani/opencv'
make: *** [all] Error 2

please reply as my project is on hold
thank you in advance...

---

### Post by T0MA on 2010-07-01
I found this thread particularly useful in getting OpenCV 1.0 (pretty obsolete) running on Lucid just now with ffmpeg.

I followed this thread for the most part to compile ffmpeg:
[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

Only difference is with the configuration where you should add --enable-shared and don't forget to export

To get opencv 1.0 to compile i followed these steps:
[http://shankhs4u.blogspot.com/2009/01/how-to-install-opencv-in-ubuntu-804810.html]("http://shankhs4u.blogspot.com/2009/01/how-to-install-opencv-in-ubuntu-804810.html")

Even if you compile ffmpeg with --enable-swscale it still won't help, you should still install libswscale-dev from the repository.

As for just changing img_convert to sws_scale, that won't do the trick, as sws_scale takes different inputs then img_convert (at least now it does). I copied the part out of OpenCV 2.1 to get it running, but since the structures changes quite a bit I'm not sure if I got it right.

If you get errors with INT64_C not being defined, add:
#ifndef INT64_C
#define INT64_C
#endif

Include problems, do what the thread says #include <ffmpeg/..> -> #include<avcodec/..>

and #include <libswscale/..>

Around line 240, I commented out the part with #if LIBAVFORMAT.. #endif and rewrote the code from 2.1 to fit into the 1.0 structure:

```
struct SwsContext *img_convert_ctx = sws_getContext(capture->frame.width,
			             capture->frame.height,
			             PIX_FMT_BGR24,
			             capture->video_st->codec->width,
			             capture->video_st->codec->height,
			             capture->video_st->codec->pix_fmt,
			             SWS_BICUBIC,
			             NULL, NULL, NULL);

			    sws_scale(img_convert_ctx, (const uint8_t* const*)capture->picture,
			    		 capture->picture->linesize, 0,
			             capture->video_st->codec->height,
			             capture->rgb_picture.data, capture->rgb_picture.linesize);

			    sws_freeContext(img_convert_ctx);

```

It compiles now but not sure if actually opens video files. I haven't bothered with the write function as I'm not planning on using that, so I just uncommented the whole img_convert section there.

Hope that helps for someone in the future.. I spent a solid 20 hours debugging it so far..

EDIT: Also, when you configure opencv, add CPPFLAGS="-D__STDC_CONSTANT_MACROS" as you will get problems with the INT64_C in other places too..

---

### Post by zeee on 2010-09-08
Hi!

I'm new to Ubuntu and I've tried to follow this [guide]("http://helpforlinux.blogspot.com/2010/07/install-opencv-in-ubuntu-1004.html") (Install OpenCV in Ubuntu 10.04).

I "think" I've installed it properly since I did not encounter any error. I've tried opening MPEG video files and it worked okay. But when I tried to access my ip camera that has MJPEG output, I encountered errors saying something like "MJPEG codec not found".

I use this code to access the MJPEG video stream

```
CvCapture* capture = cvCaptureFromFile("http://admin:admin@192.168.0.30:80/cgi/mjpg/mjpg.cgi");
```

I opened it before using chrome and VLC player which turned out okay. I've read articles from the opencv group but still I can't make it work..


Any help is greatly appreciated.. ;)

---

