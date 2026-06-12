---
title: "making a simple, 'flashing' video with two frames and FFmpeg"
date: 2013-09-15
forum: Multimedia Software
---

### Post by ZICODIAN on 2013-09-15
Hi *

I have two images that I would like to use to make a video of about 30 seconds in length with the frames alternating throughout. So, let's say I have one of the images a red colour and the other a yellow colour. I would want to combine these in a video in such a way that they alternated, each appearing for ~ 1/3 of a second, resulting in a video lasting ~ 30 seconds. How do you think I could try to do this using FFmpeg (or something else you would recommend)? Thanks!

---

### Post by qyot27 on 2013-09-16
Using an AviSynth script can accomplish this easily.

First, compile a recent version of FFmpeg, either 2.0.1 or from git (and use the --enable-avisynth option when you run ./configure).  Then compile FFMS2 from git, and finally, compile AvxSynth.  Instructions for this part are here:
[http://forum.doom9.org/showthread.php?p=1643184#post1643184](http://forum.doom9.org/showthread.php?p=1643184#post1643184)


For the example given in the OP of a red and yellow alternating video, solid color frames can be generated from within the script environment, so you don't even need external images:
```
#Generate solid red image, 8 frames long (1/3 second @ 24fps)
vid_red=BlankClip(8,color=$FF0000).KillAudio()

#Generate solid yellow image, 8 frames long (1/3 second @ 24fps)
vid_yellow=BlankClip(8,color=$FFFF00).KillAudio()

#Stitch them together into a 2-second loop
v=vid_red + vid_yellow + vid_red + vid_yellow + vid_red + vid_yellow

#Repeat loop for thirty seconds
v+v+v+v+v+v+v+v+v+v+v+v+v+v+v
```
You can adjust the width/height of the clip or the color used by changing the relevant parameters given to BlankClip.  See [http://avisynth.nl/index.php/BlankClip](http://avisynth.nl/index.php/BlankClip) for reference.  Also, [http://avisynth.nl/index.php/Color_presets](http://avisynth.nl/index.php/Color_presets) for the color presets in case you don't want pure red and pure yellow.

For the example of actual images,
```
#Generate solid red image, 8 frames long (1/3 second @ 24fps)
vid_red=FFVideoSource("image1.png")
vid_red2=vid_red+vid_red+vid_red+vid_red+vid_red+vid_red+vid_red+vid_red

#Generate solid yellow image, 8 frames long (1/3 second @ 24fps)
vid_yellow=FFVideoSource("image2.png")
vid_yellow2=vid_yellow+vid_yellow+vid_yellow+vid_yellow+vid_yellow+vid_yellow+vid_yellow+vid_yellow

#Stitch them together into a 2-second loop
v=vid_red2 + vid_yellow2 + vid_red2 + vid_yellow2 + vid_red2 + vid_yellow2

#Repeat loop for thirty seconds
v+v+v+v+v+v+v+v+v+v+v+v+v+v+v
```


Whichever one you choose, save the script with a name like alternating_color.avs or some such.  Then:
```
ffmpeg -i alternating_color.avs -vcodec ffvhuff alternating_color.avi
```
which will convert the output of the script to an ffvhuff-encoded AVI file.

---

### Post by ZICODIAN on 2013-09-16
Hi there. Thanks for your help.

Here's what I've done so far:

FFmpeg:

```

git clone git://source.ffmpeg.org/ffmpeg.git ffmpeg
cd ffmpeg
sudo apt-get install yasm
./configure --enable-avisynth
make
sudo make install

```

FFMS2:

```

git clone git://github.com/FFMS/ffms2.git
cd ffms2
libavcodec-dev libavformat-dev libswscale-dev libavutil-dev gawk
./configure --disable-shared --enable-static --with-pic
make
sudo make install

```

I was not sure the above worked, so I did the following:

```

sudo apt-get install libffms2-dev

```

AvxSynth:

```

git clone git://github.com/avxsynth/avxsynth.git
cd avxsynth
autoreconf -fiv
sudo apt-get install liblog4cpp5-dev
./configure --enable-silent-rules --with-pic
make
sudo make install

```

I set up the following script:

```
vid_black=FFVideoSource("side_bars_1_2.png")
vid_black2=vid_black+vid_black+vid_black+vid_black+vid_black+vid_black+vid_black+vid_black


vid_yellow=FFVideoSource("side_bars_1_1.png")
vid_yellow2=vid_yellow+vid_yellow+vid_yellow+vid_yellow+vid_yellow+vid_yellow+vid_yellow+vid_yellow


v=vid_black2 + vid_yellow2 + vid_black2 + vid_yellow2 + vid_black2 + vid_yellow2


v+v+v+v+v+v+v+v+v+v+v+v+v+v+v

```

In attempting to run this, I encountered difficulties:

```

ffmpeg -i test1.avs -vcodec ffvhuff test1.avi
ffmpeg version N-56304-ga444ddf Copyright (c) 2000-2013 the FFmpeg developers
  built on Sep 16 2013 11:59:03 with gcc 4.7 (Ubuntu/Linaro 4.7.3-1ubuntu1)
  configuration: --enable-avisynth
  libavutil      52. 43.100 / 52. 43.100
  libavcodec     55. 31.101 / 55. 31.101
  libavformat    55. 16.102 / 55. 16.102
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 84.100 /  3. 84.100
  libswscale      2.  5.100 /  2.  5.100
  libswresample   0. 17.103 /  0. 17.103
[avisynth @ 0x1a19880] Script error: there is no function named "FFVideoSource"
(test1.avs, line 2)
test1.avs: Unknown error occurred


```

Searching online, I downloaded the file ffms2.dll, included it in the images' directory and then added the following line to the head of the script:

```

loadplugin("ffms2.dll")

```

This resulted in the following error:

```

ffmpeg -i test1.avs -vcodec ffvhuff test1.avi
ffmpeg version N-56304-ga444ddf Copyright (c) 2000-2013 the FFmpeg developers
  built on Sep 16 2013 11:59:03 with gcc 4.7 (Ubuntu/Linaro 4.7.3-1ubuntu1)
  configuration: --enable-avisynth
  libavutil      52. 43.100 / 52. 43.100
  libavcodec     55. 31.101 / 55. 31.101
  libavformat    55. 16.102 / 55. 16.102
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 84.100 /  3. 84.100
  libswscale      2.  5.100 /  2.  5.100
  libswresample   0. 17.103 /  0. 17.103
nm: ffms2.dll: No symbols
[avisynth @ 0x2386880] LoadPlugin: unable to load "ffms2.dll"
(test1.avs, line 1)
test1.avs: Unknown error occurred

```

Would you have any suggestions on how to proceed? I have no idea what I'm doing.

---

### Post by qyot27 on 2013-09-18
The reason the .dll didn't work is because the .dll is for Windows.

You need to follow the instructions in the doom9 post exactly (for all of them, not just AvxSynth).  They can be copy-and-pasted - the ones that are indented span multiple lines, so make sure to copy the entire command with those.  I strongly urge the use of those checkinstall lines over plain sudo make install because checkinstall will register the packages against apt and this makes it easy to find them in Synaptic/Software Center/etc. (and if you ever need to remove them, you can with very little effort).

As a critique, though,
FFmpeg needs to be compiled with --enable-avresample.  FFMS2 depends on the avresample library to properly handle audio (even though this particular task doesn't require audio, but if you ever need to do something with audio, you would need to make sure that works).

If you're on 64-bit Ubuntu, FFmpeg needs --enable-pic; this is non-optional.  Whether FFMS2 and AvxSynth need --with-pic passed is questionable since their autotools-based build systems should pick up on that and do the right thing.  I included it strictly for paranoia reasons.

Since I'm guessing what you did was install a bunch of the libavcodec, et al. -dev libraries in the space between compiling FFmpeg but before trying to compile FFMS2, you basically undid all but one (having an FFmpeg that can use AviSynth scripts at all) of the benefits of compiling FFmpeg - the build of FFmpeg provides those libraries, removing the need for the -dev packages.  The same thing is true of FFMS2 - compiling from source will provide all of this, so the libffms2-dev package was unnecessary and probably also undid the work of building it as well.

AvxSynth may or may not have detected this problem and disabled avxffms2 because it could no longer work with the outdated version of libffms2-dev in the repositories, which lead to the plugin not being generated, which leads to the error you saw where it couldn't find the FFVideoSource function.


At best, FFMS2 really did find the libraries from the FFmpeg that was built first (although as I noted, it'd probably crap out on audio because of the lack of avresample), and AvxSynth may have found the proper version of FFMS2 and built/installed avxffms2.  If this is the case, then all you'd probably need to do is run 'sudo ldconfig' - any time a shared library is installed, that command must be run in order for the system to see it (although as AvxSynth got detected, it hints that avxffms2 isn't there and sudo ldconfig probably won't do anything meaningful).

---

