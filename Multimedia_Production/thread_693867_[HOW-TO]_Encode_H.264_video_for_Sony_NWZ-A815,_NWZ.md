---
title: "[HOW-TO] Encode H.264 video for Sony NWZ-A815, NWZ-A816 or NWZ-A818 players"
date: 2008-02-11
forum: Multimedia Production
---

### Post by descentspb on 2008-02-11
This guide is meant for the people who want to use their Sony-NWZ players using their maximum capabilities. This guide is identical to this one [http://ubuntuforums.org/showthread.php?t=593756](http://ubuntuforums.org/showthread.php?t=593756), with one big difference:

It offers **[SIZE="2"]H.264[/SIZE]**, which is of much more quality than mpeg4-sp, xvid one. Though the encoding process takes more time.

I will be using ffmpeg and x264 for video encoding, aac for audio.

[COLOR="Red"]**[SIZE="2"]Part 1. ffmpeg installation.[/SIZE]**[/COLOR]

We need to download and build a recent version of ffmpeg from SVN, so we need the packages to compile ffmeg, libraries for different codec support and SVN (subversion) system.

```
cd ~
mkdir sources
cd sources
sudo apt-get build-essential
sudo apt-get install liblame-dev libfaad-dev libvorbis-dev libfaac-dev \
 libxvidcore4-dev liba52-0.7.4-dev libx264-dev libogg-dev
sudo apt-get install subversion

```

Now, we should download the sources for ffmpeg. That's easy:

```
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg
```

and now we are going to compile it.

```
./configure --enable-gpl --enable-pthreads --enable-libvorbis \
 --enable-liba52 --enable-libmp3lame \
 --enable-libfaad --enable-libfaac --enable-libxvid --enable-libx264
make
sudo make install
```

if there are no errors we can go on with encoding itself.

[COLOR="Red"]**[SIZE="2"]Part 2. encoding.[/SIZE]**[/COLOR]

the command to encode any video file into Sony-NWZ compatible h.264 looks like this:

```
ffmpeg -y -i INPUT.avi -threads auto -vcodec libx264 -b 250k -maxrate 768k \
 -flags +loop  -cmp +chroma -partitions +parti4x4+partp4x4+parti8x8+partp8x8 -flags2 \
 +mixed_refs -level 13 -refs 3 -subq 7 -trellis 2 -me 6 -g 300 -s 320x240 -ab 128k -ar\
 44100 -ac 2 -acodec libfaac OUTPUT.mp4
```

where INPUT.avi and OUTPUT.mp4 are your filenames. You are not limited by **.avi** input file type here, and can use anything that ffmpeg can read, and that's a big deal. 
That's all of manual encoding.

[COLOR="Red"]**[SIZE="2"]Part 3. Automated encoding.[/SIZE]**[/COLOR]

I've modified Eric Hewitt's script for iPod video encoding, so that it matches our needs.
You can create a file named **walkman** with the following contents

```
#!/bin/bash

input_file=$1
input_x=`ffmpeg -i "${input_file}" 2>&1 | sed '/Video:/!d' | sed 's/.* \([0-9]\{3,4\}\)x\([0-9]\{3\}\).*/\1/'`
input_y=`ffmpeg -i "${input_file}" 2>&1 | sed '/Video:/!d' | sed 's/.* \([0-9]\{3,4\}\)x\([0-9]\{3\}\).*/\2/'`
echo $input_x
echo $input_y
output_dir=$PWD
declare -i crop_tmp
crop_tmp=-$input_y/3*2+$input_x/2
declare -i crop
crop=$crop_tmp+$crop_tmp%2
echo $crop

ffmpeg -y -i "${input_file}" -threads auto -vcodec libx264 -b 250k -cropleft "${crop}" -cropright "${crop}" -aspect 1.333 -maxrate 768k -flags +loop -cmp +chroma -partitions +parti4x4+partp4x4+parti8x8+partp8x8 -flags2 +mixed_refs -level 13 -refs 3 -subq 7 -trellis 2 -me 6 -g 300 -s 320x240 -ab 128k -ar 44100 -ac 2 -vol 768 -acodec libfaac "${output_dir}/${input_file}_walkman.mp4"
```

then do:

```
chmod +x walkman
sudo mv walkman /usr/bin
```

This script crops the video in the way it gets the Sony player aspect ratio (pan&scans it to 4:3), resizes it to 320x240 resolution and converts into NWZ-compatible mp4 videofile.

Use it like this:

```
walkman INPUT.avi
```

---

### Post by philc on 2008-02-12
Really nice tutorial, well done.

Just a couple of thoughts from me. 

It might be worth installing FFmpeg with a few more codec options. Although not needed for your tutorial, it would be useful later. So, for example:
```

sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libx264-dev libdts-dev checkinstall build-essential subversion

./configure --enable-gpl --enable-pp --enable-libvorbis --enable-libtheora --enable-liba52 --enable-libdc1394 --enable-libgsm --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-pthreads --enable-libx264 --enable-shared
```

[http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html](http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html)

This includes enabling Theora for video.

With regards to the x264 encoding, there was a thread on here previously discussing the best parameters to use. Here's my summary of it, which is not to say it is THE BEST, just something else to consider:

[http://stream0.org/2008/01/optimised-x264-encoding-with-f.html](http://stream0.org/2008/01/optimised-x264-encoding-with-f.html)

A summary of the command is as follows:

```
ffmpeg -y -i input_file -an -v 1 -threads auto -vcodec libx264 -deinterlace -b 5000k -bt 175k -flags +loop -coder ac -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me epzs -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 3 -b_strategy 1 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 5000k -bufsize 2M -cmp 1 -s 720x480 -f mp4 -pass 1 /dev/null

ffmpeg -y -i input_file -v 1 -threads auto -vcodec libx264 -deinterlace -b 5000k -bt 175k -flags +loop -coder ac -refs 5 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 3 -b_strategy 1 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 5000k -bufsize 2M -cmp 1 -s 720x480 -acodec libfaac -ab 256k -ar 48000 -ac 2 -f mp4 -pass 2 new_file.mp4
```

While the command line included there will create x264 files at way too high a bitrate for your needs, some things to consider includer:

[LIST]
[*]Deinterlacing the output file
[*]Using 2 pass encoding
[*]Using CABAC if your device supports it (-coder ac)
[/LIST]

---

### Post by descentspb on 2008-02-12
Well, i am pretty sure that these players do not support CABAC, and also B-frames. I can't check it out now, but isn't "-b_strategy 1" meant for using B-frames?

Why are you passing the first pass output to /dev/null without making any log files, is it normal?

---

### Post by descentspb on 2008-02-12
If anyone can help me in editing the walkman264 script so that you don't need any more to manually enter the X and Y resolution, that would be nice.

---

### Post by philc on 2008-02-12
On the first pass, FFmpeg will automatically write a log file in the current directory. This file is read during the second pass. So, you can output anywhere you like during the first pass - create a file if you want to, but I was just discarding the output.

From what I understand about b_strategy, it can always be set to 1 whether you are using B frames or not. Although I'm happy to take advice on this.

With regards to knowing the dimensions of the input file, without asking the user to enter them, you can read this from FFmpeg. If you just type:

> ffmpeg inputfile.avi

You'll see the input file properties.

I haven't done this with Bash, but if a Perl script helps you, here's how I do something similar:

[http://stream0.org/2008/01/find-and-extract-video-file-de.html](http://stream0.org/2008/01/find-and-extract-video-file-de.html)

---

### Post by descentspb on 2008-03-14
I modified the script for it to pan&scan the video automatically.

---

### Post by kennethmsmith on 2008-04-30
I tried to do this using your code above.  Here is what happened.

first I got error when I ran this part:

 sudo apt-get install liblame-dev libfaad2-dev libvorbis-dev libfaac-dev \
 libxvidcore4-dev liba52-0.7.4 libx264-dev

it said something about not finding libfaad2 but that there was a replacement or something like that so I asked it to get and install the suggested replacement.  sorry didnt capture this when it happened so I don't have the actual results to paste here.  

Then I kept moving down the chain because that replacement seemed to work for that step.  So then I got all the way to compiling and the following is what i got.  PLEASE HELP ME GET THIS WORKING... I REALLY WANT TO USE VIDEO ON MY WALKMAN S615F

my results:

kenneth@kenneth-desktop:~/sources/ffmpeg$ ls
Changelog    COPYING.LGPL  ffserver.h   libpostproc       tests
cmdutils.c   CREDITS       INSTALL      libswscale        tools
cmdutils.h   doc           libavcodec   MAINTAINERS       version.sh
common.mak   Doxyfile      libavdevice  Makefile          vhook
config.err   ffmpeg.c      libavfilter  output_example.c
configure    ffplay.c      libavformat  README
COPYING.GPL  ffserver.c    libavutil    subdir.mak
kenneth@kenneth-desktop:~/sources/ffmpeg$ ./configure --enable-gpl --enable-pp --enable-pthreads --enable-libvorbis \
>  --enable-liba52 -- enable-libdc1394 --enable-libgsm --disable-debug --enable-libmp3lame \
>  --enable-libfaad --enable-libfaac --enable-libxvid --enable-libx264
Unknown option "--enable-pp".
See ./configure --help for available options.
kenneth@kenneth-desktop:~/sources/ffmpeg$ ./configure --enable-gpl --enable-postproc --enable-pthreads --enable-libvorbis  --enable-liba52 -- enable-libdc1394 --enable-libgsm --disable-debug --enable-libmp3lame  --enable-libfaad --enable-libfaac --enable-libxvid --enable-libx264
Unknown option "--".
See ./configure --help for available options.
kenneth@kenneth-desktop:~/sources/ffmpeg$ ./configure --enable-gpl --enable-postproc --enable-pthreads --enable-libvorbis  --enable-liba52 --enable-libdc1394 --enable-libgsm --disable-debug --enable-libmp3lame  --enable-libfaad --enable-libfaac --enable-libxvid --enable-libx264
ERROR: liba52 not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

---

### Post by descentspb on 2008-05-01
Corrected a couple of mistakes. Should work now. Do the "sudo apt-get" part again, and the configure part again. If it complains about missing packages, search for it in Synaptic, and install a corresponding *-dev package, i.e. liba52-0.7.4-dev. But i think it should work flawlessly now.

---

### Post by kennethmsmith on 2008-05-01
Thanks.. I'll give it a shot when I get home tonight.  I'll let you know how it turns out.

---

### Post by kennethmsmith on 2008-05-01
Oh... do I need to run the "SVN" part again as well?

---

### Post by descentspb on 2008-05-01
No, you don't.

---

### Post by kennethmsmith on 2008-05-01
well.. i got through the install (i think).  now i'm going to try to convert a video and load it to my sony walkman.  i'll keep you posted on the results... p.s.  man the Make part took a long time.  I was worried I did something wrong but i guess i just didn't understand what "make" did.

---

### Post by descentspb on 2008-05-02
When you were doing "make", you compiled the ffmpeg application from source. Yes, it usually takes a long time, depending on your machine, and on the application. The main part is that you don't get any errors in the end of the make process. But with ffmpeg it should be successful.

---

### Post by kennethmsmith on 2008-05-02
Well.. the compile seemed to go fine, and the encoding of a video from avi to mp4 seemed to go well also.  I could play the new video inside ubuntu, but when I put it on my NWZ-S615F walkman, it didn't play.  Says the file is damaged, but I think that is the players standard response when it can't recognize something about the file.

I've played some m4v files on my player, but want to be able to convert avi's to play on it.  I'm close to just giving up though because this is so time consuming.

---

### Post by descentspb on 2008-05-02
As i can see in your player specifications, it supports H.264 baseline, the same as mine. So it should go fine. I've checked the ffmpeg encoder settings, which I posted, they are correct. All I have to do to encode a video is to write "walkan Name_of_the_file.avi" and it's done. Obviously, not much work.
Well, if it's not working, i can't really help much, sorry, cause i don't have such a player as you do. But giving up is always not the best solution. When you are done, your Sony becomes a great videoplayer, so it's worth trying.

---

### Post by kennethmsmith on 2008-05-02
is there any way to validate the resulting file (.mp4) to make sure it is in the right format and has no errors?  Or a way to list all the properties of the file so I can show them to you on here, and you can see if they are correct or not?

thanks

---

### Post by descentspb on 2008-05-02
> **kennethmsmith said:**
> is there any way to validate the resulting file (.mp4) to make sure it is in the right format and has no errors?  Or a way to list all the properties of the file so I can show them to you on here, and you can see if they are correct or not?

thanks

No, that's not needed. Try it on another file, any movie or trailer etc. can be useful. If it's not working again, the problem is in the ffmpeg commandline properties, which your player does not understand.

---

### Post by magawake on 2008-05-16
I have encoded my file correctly (atleast I think). I then moved it to /media/WALKMAN/VIDEO 

If I do a mplayer output.mp4

> Playing output.mp4.
Quicktime/MOV file format detected.
VIDEO:  [mp4v]  320x240  24bpp  10.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Xv: could not grab port 355
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 320x240 Planar YV12 
GNOME screensaver enabled 0.0% 0 0 

It plays the file fine. 

However, when I scroll to Videos section on my walkman I get, "NO Video files found".

Any ideas?

TIA

---

### Post by descentspb on 2008-05-16
That's strange, cause if the file was just corrupt, or couldn't be played, cause of any kind of incompatibility, my Walkman usually just told me that it can't read the file. There were no problems with the player listing the file in the "Videos" section.
Maybe you unmounted the device unsafely and it didn't record the file correctly? Try to make this again with a safe unmount. I really cannot imagine what the problem can be.

---

### Post by Anal on 2008-06-12
Hello, trying to compile ffmpeg from svn gives the following error:

```
libavcodec/libx264.c: In function ‘X264_init’:
libavcodec/libx264.c:224: error: ‘X264_ME_TESA’ undeclared (first use in this function)
libavcodec/libx264.c:224: error: (Each undeclared identifier is reported only once
libavcodec/libx264.c:224: error: for each function it appears in.)
libavcodec/libx264.c:256: warning: assignment discards qualifiers from pointer target type
make: *** [libavcodec/libx264.o] Error 1
```

Any hint?

Thank you so much.

---

### Post by Anal on 2008-06-12
Solved.
Installing these two packages: 

[http://www.brloh.eu/ubuntu/libx264-dev_0.svn20080408-0.0ubuntu1_i386.deb](http://www.brloh.eu/ubuntu/libx264-dev_0.svn20080408-0.0ubuntu1_i386.deb)
[http://www.brloh.eu/ubuntu/libx264-59_0.svn20080408-0.0ubuntu1_i386.deb](http://www.brloh.eu/ubuntu/libx264-59_0.svn20080408-0.0ubuntu1_i386.deb)

seems like a bug of the gutsy package of libx264-dev, though.

Thanks to this thread: [http://forum.ubuntu.cz/index.php?topic=23805.15](http://forum.ubuntu.cz/index.php?topic=23805.15)

(can't understand any single word, only the links :-)

---

### Post by descentspb on 2008-06-12
I'm not sure, but that seems like a mistake in the source code of ffmpeg. You are grabbing the latest sources from SVN always, and that is rare, but mistakes can happen there, it's not of production quality. I'll try to recompile it myself in the evening when i come home.

---

### Post by ekdahl on 2008-07-24
Very nice guide!

Here's a version of the script that doesn't crop the sides, but instead rounds the height to the next multiple of 16. The video bitrate is a little higher. It also uses constant quality audio instead of constant bitrate. "-threads auto" is changed to "-threads 0" to work with current ffmpeg.

```
#!/bin/bash

input_file=$1
output_dir=$PWD

input_x=`ffmpeg -i "${input_file}" 2>&1 | sed '/Video:/!d' | sed 's/.* \([0-9]\{3,4\}\)x\([0-9]\{3\}\).*/\1/'`
input_y=`ffmpeg -i "${input_file}" 2>&1 | sed '/Video:/!d' | sed 's/.* \([0-9]\{3,4\}\)x\([0-9]\{3\}\).*/\2/'`
echo $input_x
echo $input_y

declare -i height
height=$(($input_y*320/$input_x))
height=$(($height+$height%16))
echo $height

ffmpeg -y -i "${input_file}" -threads 0 -s 320x"${height}" -vcodec libx264 -b 300k -maxrate 768k \
-flags +loop -cmp +chroma -partitions +parti4x4+partp4x4+parti8x8+partp8x8 -flags2 +mixed_refs \
-level 13 -refs 3 -subq 7 -trellis 2 -me 6 -g 300 -aq 120 -ac 2 -vol 768 -acodec libfaac \
"${output_dir}/${input_file}_walkman.mp4"
```

Edit:
BTW. I needed to install libx264-dev & libx264-59 debs from Intrepid to make (current) ffmpeg build.

---

