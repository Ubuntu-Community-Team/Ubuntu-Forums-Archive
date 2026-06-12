---
title: "Script to create android (480x320) compatible mp4 video using ffmpeg"
date: 2009-08-18
forum: Multimedia Software
---

### Post by kaivalagi on 2009-08-18
If you're interested I created a python script to create compatible mp4 video for android G1/Dream/Hero from any video file using ffmpeg. It will figure out the padding top and bottom to fit the screen and keep the original video aspect ratio, see attached. To install and use:

To install:
[LIST=1]
[*]save attached file to /tmp/
[*]put the file into a folder in your PATH, in this case /usr/bin: "sudo cp /tmp/android-video.py /usr/bin"
[*]give the file exec rights: "sudo chmod +x /usr/bin/android-video.py"
[*]install ffmpeg with mp4 etc support, try using the following (works for Jaunty and Intrepid):
```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```
A full set of methods can be found in this thread: [_[COLOR="Blue"]HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1117283")
[/LIST]

To use:
[LIST=1]
[*]go to the terminal and cd to the directory where video exists
[*]run "android-video.py videofile1 videofile2..."
[*]new gnome-terminals will be spawned for each video conversion required
[*]New files with the same name as originals will be created but with a .mp4 extension added
[/LIST]

Note: you'll need ffmpeg installed...

If you want to change the video conversion settings they are all set at the top of the script as follows:

```
TEMP_INFO_PATH = "/tmp/android-video.info"
TARGET_VIDEO_WIDTH = 480
TARGET_VIDEO_HEIGHT = 320
TARGET_AUDIO_CHANNELS = 2
TARGET_AUDIO_SAMPLING_RATE = 16000
TARGET_AUDIO_BIT_RATE = 64000
TARGET_FRAME_RATE = 23.976
TARGET_VIDEO_BIT_RATE = 500000
NO_PADDING = False
```

In theory it could be used for future devices with other screen sizes and requirements...

Hope you find it useful..I do

[COLOR="Blue"]Edit: I've updated the script to handle input video aspect ratio's lower than what the android offers, this will result in left and right padding of the output video rather than the usual top and bottom padding as seen with modern day films.[/COLOR]

---

### Post by FakeOutdoorsman on 2009-08-18
FFmpeg from the repository will need restricted encoders, such as mpeg4 and libfaac, to be enabled:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by kaivalagi on 2009-08-18
> **FakeOutdoorsman said:**
> FFmpeg from the repository will need restricted encoders, such as mpeg4 and libfaac, to be enabled:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

I can't recall compiling ffmpeg before now, I think I am using the one from the standard repos just fine...I'll take a look though, thanks for the heads up.

[COLOR="Blue"]Edit: The below looks likely though (thanks for the ffmpeg thread link!):

```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```[/COLOR]

---

### Post by kaivalagi on 2009-08-18
I've updated the script to handle input video aspect ratio's lower than what the android offers, this will result in left and right padding of the output video rather than the usual top and bottom padding as seen with modern day films.

New script attached to the first post :)

---

### Post by tribaal on 2009-08-20
Awesome, works wonders.

I confirm that this works with any need for compilation or whatnot, the command-line provided is the only thing you need to make it work (tested on Jaunty, playback on my new HTC Hero :) ).

Small tip: instead of installing the script to /usr/bin, I like to create a ~/bin folder, and put it here. This way it's automagically in my PATH without making it available to other users. You might need to logout/login again for this to work (adding ~/bin to the path is done on login by the ~/.profile script).

Thanks a lot!

- Trib'

---

### Post by FakeOutdoorsman on 2009-08-20
> **kaivalagi said:**
> I can't recall compiling ffmpeg before now, I think I am using the one from the standard repos just fine...I'll take a look though, thanks for the heads up.

[COLOR="Blue"]Edit: The below looks likely though (thanks for the ffmpeg thread link!):

```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```[/COLOR]

Compiling FFmpeg is just one option to enable restricted encoders.  You can also install *ubuntu-restricted-extras* as you pointed out, but I prefer to recommend installing *libavcodec-unstripped-51* (Intrepid) or *libavcodec-unstripped-52* (Jaunty) which is what you really need if you want to use the repository FFmpeg.  The *ubuntu-restricted-extras* metapackage automatically includes these packages, but it also installs a bunch of other packages and I think it is a little bloated.

---

### Post by jvaudrey on 2009-08-24
Hello

Just a quick message to say thanks for this script, i have installed as a Nautilus script so that i can just right click the avi choose scripts and then android-video.py and it works perfectly

thanks again:popcorn:

---

### Post by tost_ts on 2009-09-14
i cant get this to work


*******************************************************
* android-video.py                                    *
* Description: Converts any video to MP4 suitable for *
*              viewing on Google Android (480x320)    *
*      Author: Kaivalagi                              *
*     Created: 2009-08-16                             *
*******************************************************

****************************
* PROCESSING: /home/ts/zzz
****************************

*** Retrieving file info from ffmpeg using this:
ffmpeg -i '/home/ts/too' 2> /tmp/android-video.info.328db59e-a17e-11de-9f26-0030056aa91e

*** ERROR: input width and height were not found/used - bug in code needs fixing...!!!
*** ERROR: Failed to process input file:
/home/ts/zzz

Traceback (most recent call last):
  File "/usr/bin/android-video.py", line 150, in <module>
    requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding = getPadding(inputwidth, inputheight)
  File "/usr/bin/android-video.py", line 106, in getPadding
    return requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding
UnboundLocalError: local variable 'requiredwidth' referenced before assignment

*******************************
* PROCESSING: /home/ts/zzz *
*******************************

*** Retrieving file info from ffmpeg using this:
ffmpeg -i '/home/ts/Smooth' 2> /tmp/android-video.info.328db59f-a17e-11de-9f26-0030056aa91e

*** ERROR: input width and height were not found/used - bug in code needs fixing...!!!
*** ERROR: Failed to process input file:
/home/ts/zzzz

Traceback (most recent call last):
  File "/usr/bin/android-video.py", line 150, in <module>
    requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding = getPadding(inputwidth, inputheight)
  File "/usr/bin/android-video.py", line 106, in getPadding
    return requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding
UnboundLocalError: local variable 'requiredwidth' referenced before assignment

*******************************
* PROCESSING: /home/ts/zzz *
*******************************

*** Retrieving file info from ffmpeg using this:
ffmpeg -i '/home/ts/[DivX]' 2> /tmp/android-video.info.328db5a0-a17e-11de-9f26-0030056aa91e

*** ERROR: input width and height were not found/used - bug in code needs fixing...!!!
*** ERROR: Failed to process input file:
/home/ts/[zzz]

Traceback (most recent call last):
  File "/usr/bin/android-video.py", line 150, in <module>
    requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding = getPadding(inputwidth, inputheight)
  File "/usr/bin/android-video.py", line 106, in getPadding
    return requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding
UnboundLocalError: local variable 'requiredwidth' referenced before assignment

***********************************
* PROCESSING: /home/ts/dvdrip.avi *
***********************************

*** Retrieving file info from ffmpeg using this:
ffmpeg -i '/home/ts/dvdrip.avi' 2> /tmp/android-video.info.328db5a1-a17e-11de-9f26-0030056aa91e

*** ERROR: input width and height were not found/used - bug in code needs fixing...!!!
*** ERROR: Failed to process input file:
/home/ts/dvdrip.avi

Traceback (most recent call last):
  File "/usr/bin/android-video.py", line 150, in <module>
    requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding = getPadding(inputwidth, inputheight)
  File "/usr/bin/android-video.py", line 106, in getPadding
    return requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding
UnboundLocalError: local variable 'requiredwidth' referenced before assignment

**************************
* PROCESSING: /home/ts/1 *
**************************

*** Retrieving file info from ffmpeg using this:
ffmpeg -i '/home/ts/1' 2> /tmp/android-video.info.328db5a2-a17e-11de-9f26-0030056aa91e

*** ERROR: input width and height were not found/used - bug in code needs fixing...!!!
*** ERROR: Failed to process input file:
/home/ts/1

Traceback (most recent call last):
  File "/usr/bin/android-video.py", line 150, in <module>
    requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding = getPadding(inputwidth, inputheight)
  File "/usr/bin/android-video.py", line 106, in getPadding
    return requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding
UnboundLocalError: local variable 'requiredwidth' referenced before assignment

---

### Post by kaivalagi on 2009-09-15
@tost_ts - do you actually have ffmpeg installed? e.g. run:

```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```

or compile and install, see the first post for info on this.

It looks like my script is failing to get video dimensions which it does so using "ffmpeg -i <filepath>"

Hope that helps

---

### Post by heldal on 2009-09-16
Shouldn't the script be able to handle aspect-ratio separate from resolution? Widescreen DVB SD-recordings are stored in 720x576, even though they are targeting a 16:9 AR. 

Sample ffmpeg info from a SD-recording in mythtv:
```
Input #0, mpegts, from '2520_20090916000501.mpg':
  Duration: 00:41:30.06, start: 9431.566544, bitrate: 6443 kb/s
  Program 1 
    Stream #0.0[0x200]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 10000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x280](nor): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s

```

There could be an option to use x264, although that adds another SW requirement. It may give slightly better video quality, at the cost of longer conversion time.

Conversion-time could also be slightly improved by using ffmpegs -threads option on multi-core machines.

---

### Post by kaivalagi on 2009-09-17
> **heldal said:**
> Shouldn't the script be able to handle aspect-ratio separate from resolution? Widescreen DVB SD-recordings are stored in 720x576, even though they are targeting a 16:9 AR. 

Sample ffmpeg info from a SD-recording in mythtv:
```
Input #0, mpegts, from '2520_20090916000501.mpg':
  Duration: 00:41:30.06, start: 9431.566544, bitrate: 6443 kb/s
  Program 1 
    Stream #0.0[0x200]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 10000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x280](nor): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s

```

There could be an option to use x264, although that adds another SW requirement. It may give slightly better video quality, at the cost of longer conversion time.

Conversion-time could also be slightly improved by using ffmpegs -threads option on multi-core machines.

If you could detail what ffmpeg command line options would be required for the type of movie conversion you are talking about them I could see whether I can accommodate them in the script. Any script update may be some time off though...I've started a job new job this week and am extremely busy at the moment.

---

### Post by heldal on 2009-09-17
> **kaivalagi said:**
> If you could detail what ffmpeg command line options would be required for the type of movie conversion you are talking about them I could see whether I can accommodate them in the script. Any script update may be some time off though...I've started a job new job this week and am extremely busy at the moment.

Don't think of my post as anything else than recommendations for future version. A couple more things come to mind:

Is it really worth the truble to pad the clips to 480x320 size? The player's that I've got on my android phone handles "letterbox" or fullscreen just fine, and maximising either horizontally or vertically depending on the aspect-ratio of the original clip seems to be good enough.

I've struggled quite a bit with AV sync on many video-clips, especially DVB-captures and flash-videos. The best results seems to be with a 2-pass-encoding approach. Here's an example script that I've used to convert widescreen (16:9) videos. Maybe there are some ffmpeg-options in it that you could use:

```
#/bin/sh
# Convert widescreen-clips to mp4 for android
#

INPUT="$1"
WIDTH_HEIGHT="480x272"
ASPECT="16:9"
BITRATE="500k"

ffmpeg -i "$INPUT" -threads 0 -an -pass 1 \
   -s $WIDTH_HEIGHT -aspect $ASPECT \
   -vcodec libx264 -b 500k -flags +loop -cmp +chroma \
   -partitions 0 -me_method epzs -subq 1 -trellis 0 -refs 1 \
   -coder 0 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 \
   -i_qfactor 0.71 -bt $BITRATE -maxrate 768k -bufsize 2M \
   -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 \
   -qdiff 4 -level 13 -f rawvideo -y /dev/null && \
ffmpeg -i "$INPUT" -threads 0 -acodec libfaac -ab 128k -pass 2 \
   -s $WIDTH_HEIGHT -aspect $ASPECT -vcodec libx264 \
   -b $BITRATE -flags +loop -cmp +chroma \
   -partitions +parti4x4+partp8x8+partb8x8 \
   -flags2 +mixed_refs -me_method umh -subq 5 \
   -trellis 1 -refs 5 -coder 0 -me_range 16 \
   -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 \
   -bt $BITRATE -maxrate 768k -bufsize 2M \
   -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 \
   -qmax 51 -qdiff 4 -level 13 "$INPUT".mp4

# Clean up logfiles from multi-pass runs
rm ffmpeg2pass-0.log
rm x264_2pass.log
```

---

### Post by FakeOutdoorsman on 2009-09-17
> **heldal said:**
> 
...

```
#/bin/sh
# Convert widescreen-clips to mp4 for android
#

INPUT="$1"
WIDTH_HEIGHT="480x272"
ASPECT="16:9"
BITRATE="500k"

ffmpeg -i "$INPUT" -threads 0 -an -pass 1 \
   -s $WIDTH_HEIGHT -aspect $ASPECT \
   -vcodec libx264 -b 500k -flags +loop -cmp +chroma \
   -partitions 0 -me_method epzs -subq 1 -trellis 0 -refs 1 \
   -coder 0 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 \
   -i_qfactor 0.71 -bt $BITRATE -maxrate 768k -bufsize 2M \
   -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 \
   -qdiff 4 -level 13 -f rawvideo -y /dev/null && \
ffmpeg -i "$INPUT" -threads 0 -acodec libfaac -ab 128k -pass 2 \
   -s $WIDTH_HEIGHT -aspect $ASPECT -vcodec libx264 \
   -b $BITRATE -flags +loop -cmp +chroma \
   -partitions +parti4x4+partp8x8+partb8x8 \
   -flags2 +mixed_refs -me_method umh -subq 5 \
   -trellis 1 -refs 5 -coder 0 -me_range 16 \
   -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 \
   -bt $BITRATE -maxrate 768k -bufsize 2M \
   -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 \
   -qmax 51 -qdiff 4 -level 13 "$INPUT".mp4

# Clean up logfiles from multi-pass runs
rm ffmpeg2pass-0.log
rm x264_2pass.log
```

You're using the old method of encoding to H.264 video.  What version of Ubuntu are you using?  Jaunty and above can use the libx264 presets which can make life much easier, but first you'll need to enable restricted encoders:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

If you're using an older version of Ubuntu, or just want to use the latest FFmpeg and libx264 improvements, you can compile FFmpeg yourself fairly easily:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

Here's an example from the above guide.  You can see how much easier it is to use the presets:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 22 -threads 0 output.mp4
```

I recommend reading the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for more info.

---

### Post by kaivalagi on 2009-09-17
@heldal - does it do any harm putting left/right padding in? Atleast that way any possible players will work as expected right? I could well be wrong about all of this, if you think so then set me straight :) 

@FakeOutdoorsman - thanks for the useful info, do you think it worth while to update my script to use libx264 - I am by no means an encoding expert...I assume I would just need to ensure that the following switches are in place:
```
-vcodec libx264 -vpre hq -crf 22
```
Thanks for any help to improve the script.
K

---

### Post by heldal on 2009-09-18
> **FakeOutdoorsman said:**
> You're using the old method of encoding to H.264 video.  What version of Ubuntu are you using?  

I'm aware of the presets. They're just sets of options contained in individual files. That's fine, but not awfully helpful when they're not already optimised for the device at hand. Then the choice is either make and maintain your own preset, or maintain options is custom conversion-scripts. 

Someone with more detailed knowledge of the video&audio capabilities of android devices should create optimised presets for android handsets to be included with the ffmpeg code like the existing ones for ipods.

---

### Post by kaivalagi on 2009-09-18
> **heldal said:**
> Someone with more detailed knowledge of the video&audio capabilities of android devices should create optimised presets for android handsets to be included with the ffmpeg code like the existing ones for ipods.

Yes please =P~

---

### Post by FakeOutdoorsman on 2009-09-18
> **kaivalagi said:**
> 
@FakeOutdoorsman - thanks for the useful info, do you think it worth while to update my script to use libx264 - I am by no means an encoding expert...
Thanks for any help to improve the script.
K

I have no experience with Android, so I'm unsure of it's capabilities or if it has any sort of playback limitations.  Using libx264 will give better quality/file size, but it will make your script more complicated due to the multiple and incompatible versions of Ubuntu repository FFmpeg.  I assume the screen size of these Android devices is small and some may not notice the improvements offered by libx264, but if people use the Android device to output video to a bigger screen there will be a big difference (compared to similar bitrate mpeg4).  I don't encode to mpeg4 anymore, so I'm biased towards libx264.

I suppose you can to a check to see if the user has a recent enough FFmpeg to support libx264 presets and then allow this option.  Perhaps if the user has *libavcodec 52.20.0* and above, then encode with libx264 instead.  FFmpeg outputs the version at each command.  There are probably better and easier ways to do this, for example just see if they have any presets installed in */usr/share/ffmpeg/*.

> I assume I would just need to ensure that the following switches are in place:
```
-vcodec libx264 -vpre hq -crf 22
```

Also add **-threads 0**.  The **0** tells libx264 to automatically choose the correct number of threads.  Other encoders with threads support can not use 0 and the user must choose the appropriate number of threads.

> **heldal said:**
> I'm aware of the presets. They're just sets of options contained in individual files. That's fine, but not awfully helpful when they're not already optimised for the device at hand. Then the choice is either make and maintain your own preset, or maintain options is custom conversion-scripts.

If you compile recent FFmpeg and x264, an advantage of using presets is to easily keep up with any changes or additions.  Otherwise you'll have to comb the changelogs, read error messages, or subscribe to mailing lists to keep up.

You can still use the presets and then add your customizations to override the preset defaults.  Just declare them after your preset.  This is just an example of adding overrides (this particular command would probably result in low quality):
```
ffmpeg -i input -an -vcodec libx264 -vpre hq [color=#FF0000]-flags -loop -refs 5[/color] -crf 26 -threads 0 output.mp4
```

There are also some secondary presets used to conform to certain profiles.  More info at the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

---

### Post by jackhynes on 2009-09-20
When I execute the code, a separate console window opens and closes quickly and the job appears to be done. I can't see any error messages. No new files seem to be created however, and obviously a long video would not be re-encoded in half a second.

---

### Post by kaivalagi on 2009-09-21
> **jackhynes said:**
> When I execute the code, a separate console window opens and closes quickly and the job appears to be done. I can't see any error messages. No new files seem to be created however, and obviously a long video would not be re-encoded in half a second.

Something went wrong, the main window you ran the command in will display what the output used to run in the second terminal window was. Take the ffmpeg command text between the double quotes (after the gnome-terminal bit) and run that in isolation to see what might be wrong.

---

### Post by jackhynes on 2009-09-21
> **kaivalagi said:**
> Something went wrong, the main window you ran the command in will display what the output used to run in the second terminal window was. Take the ffmpeg command text between the double quotes (after the gnome-terminal bit) and run that in isolation to see what might be wrong.

Okay, I did that and then installed libavcodec-unstripped-52 and then tried again and I think the same error occured:
```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
[NULL @ 0x98ec1d0]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '**rmfilename**':
  Duration: 00:46:52.82, start: 0.000000, bitrate: 1045 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 160 kb/s
Unknown encoder 'libfaac'
```

---

### Post by kaivalagi on 2009-09-21
> **jackhynes said:**
> Unknown encoder 'libfaac'

Looks like the ffmpeg you have just doesn't support the required encoder for the conversion.

If you are happy to compile it from scratch I use this (in a shell script) to build and deploy ffmpeg (change the text in green and look at the text in red):

```
#!/bin/sh

BASEDIR=**[COLOR="DarkGreen"]/home/mark/Installs/Video[/COLOR]**

sudo apt-get purge ffmpeg x264

cd $BASEDIR/x264
make distclean
git pull
./configure
make
sudo checkinstall --fstrans=no --install=yes --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" --default

cd $BASEDIR/ffmpeg
make distclean
svn update
./configure --enable-gpl --enable-nonfree --enable-pthreads **[COLOR="Red"]--enable-libfaac[/COLOR]** --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
make
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --default

```

Hope that helps

---

### Post by jackhynes on 2009-09-26
Thanks for the help, in the end I followed [these instructions]("http://ubuntuforums.org/showthread.php?t=786095") and now my videos are currently encoding. :)

---

### Post by kaivalagi on 2009-09-27
> **jackhynes said:**
> Thanks for the help, in the end I followed [these instructions]("http://ubuntuforums.org/showthread.php?t=786095") and now my videos are currently encoding. :)

I think that's where I got my above script from :)

---

### Post by nekr0z on 2009-11-04
A great script, thanks a lot! I can't just express how much it helps me live!

May I point out just one minor inconvenience? I have one video file (just one, so it's not much of a problem) that has strange picture size, and the script calculates the desired framesize to be 391x320. And then ffmpeg refuses to work with it saying that "Frame size must be a multiple of 2" (I believe it's what libx264 requires.

I only know a little bash-scripting and couldn't comprehend Python to save my life, so I cannot figure out how to fix this myself. Can anyone help, please?

---

### Post by kaivalagi on 2009-11-05
> **nekr0z said:**
> A great script, thanks a lot! I can't just express how much it helps me live!

May I point out just one minor inconvenience? I have one video file (just one, so it's not much of a problem) that has strange picture size, and the script calculates the desired framesize to be 391x320. And then ffmpeg refuses to work with it saying that "Frame size must be a multiple of 2" (I believe it's what libx264 requires.

I only know a little bash-scripting and couldn't comprehend Python to save my life, so I cannot figure out how to fix this myself. Can anyone help, please?

Can you post the terminal output from the python script and the subsequently spawned terminal which runs the conversion. And could I have a little more info on the video properties? Can't promise anything but there something useful in the info I've asked for...

---

### Post by nekr0z on 2009-11-05
> **kaivalagi said:**
> Can you post the terminal output from the python script and the subsequently spawned terminal which runs the conversion. And could I have a little more info on the video properties? Can't promise anything but there something useful in the info I've asked for...

Here you go! This is what I have in terminal running the script:
```
~/music$ ~/script/android-video.py Robbie\ Williams\ -\ Supreme.avi 
*******************************************************
* android-video.py                                    *
* Description: Converts any video to MP4 suitable for *
*              viewing on Google Android (480x320)    *
*      Author: Kaivalagi                              *
*     Created: 2009-08-16                             *
*******************************************************

****************************************************************
* PROCESSING: /home/evgeny/music/Robbie Williams - Supreme.avi *
****************************************************************

*** Retrieving file info from ffmpeg using this:
ffmpeg -i '/home/evgeny/music/Robbie Williams - Supreme.avi' 2> /tmp/android-video.info.b3f7e296-ca53-11de-827c-001b7741260b

*** Summary of video information:
Input File:/home/evgeny/music/Robbie Williams - Supreme.avi
Input Width:352
Input Height:288
Output Width:480
Output Height:320
Output Top Padding:0
Output Bottom Padding:0
Output Left Padding:44
Output Right Padding:45

*** Opening new terminal for processing:
gnome-terminal -t '/home/evgeny/music/Robbie Williams - Supreme.avi' -e "ffmpeg -i '/home/evgeny/music/Robbie Williams - Supreme.avi' -s 391x320 -vcodec mpeg4 -acodec libfaac -ac 2 -ar 16000 -r 23.976 -vb 500000 -ab 128000 -aspect 4:3 -padtop 0 -padbottom 0 -padleft 44 -padright 45 '/home/evgeny/music/Robbie Williams - Supreme.avi.mp4'"

```

I have no time to even see the spawned window, it closes instantly, but here's what I get trying to run the script's command in a spare terminal"
```
~$ ffmpeg -i '/home/evgeny/music/Robbie Williams - Supreme.avi' -s 391x320 -vcodec mpeg4 -acodec libfaac -ac 2 -ar 16000 -r 23.976 -vb 500000 -ab 128000 -aspect 4:3 -padtop 0 -padbottom 0 -padleft 44 -padright 45 '/home/evgeny/music/Robbie Williams - Supreme.avi.mp4'
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1
Input #0, avi, from '/home/evgeny/music/Robbie Williams - Supreme.avi':
  Duration: 00:04:12.96, start: 0.000000, bitrate: 740 kb/s
    Stream #0.0: Video: msmpeg4, yuv420p, 352x288, 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
Frame size must be a multiple of 2
```

The whole thing is running on Ubuntu 9.10 with ffmpeg-extra package recompiled to enable AAC encoding support (nothing but that changed, the package is a stock one otherwise). That is, in case this information is of any value.

---

### Post by kaivalagi on 2009-11-05
> **nekr0z said:**
> 
```
...
Frame size must be a multiple of 2
```

The whole thing is running on Ubuntu 9.10 with ffmpeg-extra package recompiled to enable AAC encoding support (nothing but that changed, the package is a stock one otherwise). That is, in case this information is of any value.

I think the error is because of the calculated video width being an odd number "391", I've made some tweaks to the script so it shouldn't have this issue again. Can you give the attached a try, if it works I'll update the first post script. I can't test it myself unless I transform some video to those dimensions :)

Cheers

---

### Post by nekr0z on 2009-11-06
> **kaivalagi said:**
> Can you give the attached a try, if it works I'll update the first post script.

This one works seamlessly, thanks a lot!

---

### Post by kaivalagi on 2009-11-06
> **nekr0z said:**
> This one works seamlessly, thanks a lot!

No worries, have fun ;)

---

### Post by LukePH on 2009-11-11
big thanks for this script, works perfectly with my android samsung galaxy.

---

### Post by kaivalagi on 2009-11-11
> **LukePH said:**
> big thanks for this script, works perfectly with my android samsung galaxy.

No worries, glad I can help :)

---

### Post by Ekril on 2009-12-14
thanks for your efforts..
the first script was working 1 1/2 week ago but now it does not.. i just write down the command "android-video.py somemoviename.extension" and it says opening new terminal window but nothing happens.. no new terminal window no more output from script.. than i tried the second script (the one you have created fo r odd numbered dimensions) it made the same. i have got ffmpeg and restricted extras but it doesn't work.. 

upss.. i just realized that i have got a small space left in my hdd can this be the reason? i will test it..

[Edit]
no it was not the reason.. it did not work again..
[/Edit]

---

### Post by kaivalagi on 2009-12-14
> **Ekril said:**
> thanks for your efforts..
the first script was working 1 1/2 week ago but now it does not.. i just write down the command "android-video.py somemoviename.extension" and it says opening new terminal window but nothing happens.. no new terminal window no more output from script.. than i tried the second script (the one you have created fo r odd numbered dimensions) it made the same. i have got ffmpeg and restricted extras but it doesn't work.. 

upss.. i just realized that i have got a small space left in my hdd can this be the reason? i will test it..

[Edit]
no it was not the reason.. it did not work again..
[/Edit]

Do you have gnome-terminal installed? It needs it to spawn the process. If it was working and isn't now it suggests a dependency is not in place, either ffmpeg is not compiled with the right options or the terminal is not available. Try copying the command it generates and running it in the terminal separately maybe.

---

### Post by Ekril on 2009-12-14
> **kaivalagi said:**
> Do you have gnome-terminal installed? It needs it to spawn the process. If it was working and isn't now it suggests a dependency is not in place, either ffmpeg is not compiled with the right options or the terminal is not available. Try copying the command it generates and running it in the terminal separately maybe.

I am just trying to root my phone and change the rom.. i will try it asap and make you know.. 

thanks for the quick reply...

Ekrem

---

### Post by Schappenberg on 2010-01-07
Hi kaivalagi

Thanks for the great script, i've been sitting hours in front of my computer trying to find the right configuration for ffmpeg ...
But i have one problem:
most of my files have blanks in the filename, is there a trick to masquerade the blanks so the script can work with such files too?
it's a bit annoying to copying such files every time to an other location, rename the files, and so on.

Thanks for your help

Schappenberg

---

### Post by kaivalagi on 2010-01-07
> **Schappenberg said:**
> Hi kaivalagi

Thanks for the great script, i've been sitting hours in front of my computer trying to find the right configuration for ffmpeg ...
But i have one problem:
most of my files have blanks in the filename, is there a trick to masquerade the blanks so the script can work with such files too?
it's a bit annoying to copying such files every time to an other location, rename the files, and so on.

Thanks for your help

Schappenberg

There is a handy feature called auto completion in any linux terminal, if you start typing the command and then hit tab you will either get it completed or be provided with a list of files that match the partial pattern already typed.

For example, I have a music video called "Delphic - Doubt (Official).mp4", I can type this:
[LIST=1]
[*]android-v[TAB]

I then get this:
[*]android-video.py

then carry on typing this:
[*]android-video.py Delp[TAB]

I then get this:
[*]android-video.py Delphic\ -\ 

I then hit tab twice and get presented with all remaining files that match the current pattern, I can see then that a further "D" will get me there, so I type it:
[*]android-video.py Delphic\ -\ D[TAB]

which gives me this :) :
[*]android-video.py Delphic\ -\ Doubt\ \(Official\).mp4
[/LIST]

Note the back slash is the escape character for a lot of characters when it comes to the command line, incl space, ( etc

Hope that helps

---

### Post by Schappenberg on 2010-01-07
Thanks a lot for your help, it works!
I thought i've tried this too, but it seams i have not ...

Anyway, great script! Just one question: what Android phone do you use? On my HTC Magiic i see a stutter on a view videos, does you vids run smooth?

---

### Post by nekr0z on 2010-01-08
> **Schappenberg said:**
> Thanks a lot for your help, it works!
Just one question: what Android phone do you use? On my HTC Magiic i see a stutter on a view videos, does you vids run smooth?

All smooth on HTC Hero.

---

### Post by kaivalagi on 2010-01-08
> **Schappenberg said:**
> Thanks a lot for your help, it works!
I thought i've tried this too, but it seams i have not ...

Anyway, great script! Just one question: what Android phone do you use? On my HTC Magiic i see a stutter on a view videos, does you vids run smooth?

Maybe it is a particular movie that is causing issue? Give some more a try...

The script does have options at the top for bitrates etc so you could try tweaking it a little...e.g.:

```
TARGET_AUDIO_SAMPLING_RATE = 16000
TARGET_AUDIO_BIT_RATE = 64000
TARGET_FRAME_RATE = 23.976
TARGET_VIDEO_BIT_RATE = 500000

```

> **nekr0z said:**
> All smooth on HTC Hero.

+1

I too have a HTC Hero (non sprint version) and all is fine

---

### Post by JpMaxMan on 2010-03-29
Thanks for creating this!  Was very excited to see it.  Unfortunately, no matter what I do I can't get this or any other technique to play on my Android device.  When I link to the video, the media player opens and every time I get this message:

Warning

Media file type not supported.

Does anyone else experience the same thing?  any known fix?  What could possibly be wrong?  I assume since this script is in existence it has been used and video files have been played on numerous Android devices.

Very frustrated.  Any help appreciated.  

Thanks!

---

### Post by kaivalagi on 2010-03-29
> **JpMaxMan said:**
> Thanks for creating this!  Was very excited to see it.  Unfortunately, no matter what I do I can't get this or any other technique to play on my Android device.  When I link to the video, the media player opens and every time I get this message:

Warning

Media file type not supported.

Does anyone else experience the same thing?  any known fix?  What could possibly be wrong?  I assume since this script is in existence it has been used and video files have been played on numerous Android devices.

Very frustrated.  Any help appreciated.  

Thanks!

I assume you can play the converted output video in Linux fine? If so it's the device not the video created...

Try installing a free video player app from the Android Market maybe...?

---

### Post by summersab on 2010-07-06
Not really sure what happened here - I just downloaded the script, changed the permissions, and tried running it. I'm no Python guy, so I don't know what's up:

```
*******************************************************
* android-video.py                                    *
* Description: Converts any video to MP4 suitable for *
*              viewing on Google Android (480x320)    *
*      Author: Kaivalagi                              *
*     Created: 2009-08-16                             *
*******************************************************

*********************************************
* PROCESSING: /home/arthur/Videos/input.avi *
*********************************************

*** Retrieving file info from ffmpeg using this:
ffmpeg -i '/home/arthur/Videos/input.avi' 2> /tmp/android-video.info.7ea989ba-88de-11df-b0e5-001b778ca9a9

*** Summary of video information:
Input File:/home/arthur/Videos/input.avi
Input Width:664
Input Height:274
Output Width:480
Output Height:198
Output Top Padding:62
Output Bottom Padding:60
Output Left Padding:0
Output Right Padding:0

*** Opening new terminal for processing:
gnome-terminal -t '/home/arthur/Videos/input.avi' -e "ffmpeg -i '/home/arthur/Videos/input.avi' -s 480x198 -vcodec mpeg4 -acodec libfaac -ac 2 -ar 16000 -r 23.976 -vb 500000 -ab 64000 -aspect 4:3 -padtop 62 -padbottom 60 -padleft 0 -padright 0 '/home/arthur/Videos/input.avi.mp4'"

**********************************************
* PROCESSING: /home/arthur/Videos/output.mp4 *
**********************************************

*** Retrieving file info from ffmpeg using this:
ffmpeg -i '/home/arthur/Videos/output.mp4' 2> /tmp/android-video.info.7eb40a5c-88de-11df-b0e5-001b778ca9a9

*** ERROR: input width and height were not found/used - bug in code needs fixing...!!!
*** ERROR: Failed to process input file:
/home/arthur/Videos/output.mp4

Traceback (most recent call last):
  File "./android-video.py", line 153, in <module>
    requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding = getPadding(inputwidth, inputheight)
  File "./android-video.py", line 109, in getPadding
    return requiredwidth, requiredheight, top_padding, bottom_padding, left_padding, right_padding
UnboundLocalError: local variable 'requiredwidth' referenced before assignment
```

---

### Post by kaivalagi on 2010-07-08
What does this command return in the terminal window:
```
ffmpeg -i '/home/arthur/Videos/output.mp4'
```

---

### Post by summersab on 2010-07-09
Nix that. For some reason, it was protesting because of my recent install of ffmpeg from the current build (or, at least, that's what I can gather). I simply purged my recent installation and installed from the repositories. Nevermind - GREAT script!

---

### Post by FakeOutdoorsman on 2010-07-09
> **summersab said:**
> Nix that. For some reason, it was protesting because of my recent install of ffmpeg from the current build (or, at least, that's what I can gather). I simply purged my recent installation and installed from the repositories. Nevermind - GREAT script!

That's because recent FFmpeg SVN depreciated the pad* options and replaced them with:
```
-vf "pad=width:height:x:y:color"
```

From *doc/filters.texi* (unformatted output):
> @section pad

Add paddings to the input image, and places the original input at the
given coordinates @var{x}, @var{y}.

It accepts the following parameters:
@var{width}:@var{height}:@var{x}:@var{y}:@var{color}.

Follows the description of the accepted parameters.

@table @option
@item width, height

Specify the size of the output image with the paddings added. If the
value for @var{width} or @var{height} is 0, the corresponding input size
is used for the output.

The default value of @var{width} and @var{height} is 0.

@item x, y

Specify the offsets where to place the input image in the padded area
with respect to the top/left border of the output image.

The default value of @var{x} and @var{y} is 0.

@item color

Specify the color of the padded area, it can be the name of a color
(case insensitive match) or a 0xRRGGBB[AA] sequence.

The default value of @var{color} is ``black''.

---

