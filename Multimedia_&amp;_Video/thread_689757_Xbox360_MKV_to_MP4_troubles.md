---
title: "Xbox360 MKV to MP4 troubles"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by m3_del on 2008-02-06
**_[COLOR="Red"]Jexxie has now made a script that does this for you! [CHECK IT OUT!]("http://ubuntuforums.org/showpost.php?p=4382989")[/COLOR]_**


Updated: 2/17/2008 8:00pm

Many Props to this post: 
[http://ubuntuforums.org/showthread.php?t=548547](http://ubuntuforums.org/showthread.php?t=548547)

Here is the process I use to conver MKV files (with AC3 audio) to MP4's that can play on an Xbox 360
I am still struggling with dts conversion. If someone could help me out on what options to use with FFMPEG or even using Mplayer and Nero that would be much obliged.

First we need to get and install gpac tools that actually work for files larger than 2gb.

```

cd ~
wget http://downloads.sourceforge.net/gpac/gpac-0.4.4.tar.gz
tar -xzf gpac-0.4.4.tar.gz

```

Now we want to get a patch file that will fix the 2gb limit in the linux MP4Box

The patch is located [HERE]("http://sourceforge.net/tracker/?func=detail&atid=571738&aid=1448512&group_id=84101")

Copy the following into a file named "gpac.patch" (without the quotes) in you home dir (outside of the dir named gpac
```

diff -rc gpac/src/Makefile gpac-0.4.4-os_drivers/src/Makefile
*** gpac/src/Makefile     2007-05-08 17:15:25.000000000 +0200
--- gpac-0.4.4-os_drivers/src/Makefile  2007-07-01 02:14:16.000000000
+0200
***************
*** 90,95 ****
--- 90,102 ----
  CFLAGS+=-DGPAC_BIG_ENDIAN
  endif

+ #4- flags used in utils/os_divers.c
+ ifeq ($(CONFIG_LINUX), yes)
+ CFLAGS+=-DCONFIG_LINUX
+ endif
+ ifeq ($(CONFIG_FREEBSD), yes)
+ CFLAGS+=-DCONFIG_FREEBSD
+ endif

  ## libgpac scenegraph compilation and linking options
  SCENEGRAPH_CFLAGS=

```

Next we want to apply the patch

```

patch -p0 < gpac.patch

```

Now that the makefile is patched lets continue on by installing the app

```

cd ~/gpac
chmod +x configure
./configure
make
sudo make install

```

Other apps to install

```

sudo apt-get install mkvtoolnix hexedit mplayer

```

Then you need neroAacEnc. You may download it for free here:
[http://www.nero.com/eng/nero-aac-codec.html](http://www.nero.com/eng/nero-aac-codec.html)
Unpack linux directory, chmod +x neroAacEnc and copy it to a location of your choice (whitin the path, like /usr/bin)

That should do it! Now go ahead with the steps below and make some stereo MP4's for your xbox from MKV's Lets hope soon Microsoft allows for 5.1 MP4's


I still would like to code this into a smart script (maybe in ruby?!?!?) to do all of this for you (determine what audio format, etc) Any help would be appreciated. I mention Ruby as that is what I am currently learning. But enough babble read on!

```

mkvinfo file.mkv  //This is to determine which track the video and audio is and what type of audio is being used (dts, ac3, etc)

mkvextract tracks file.mkv 1:video.h264 2:audio.ac3  //This varies, of course, depending on what tracks the audio/video is on. Also this example is for ac3 audio, If your audio happens to be DTS or any other format just replace the .ac3 with the appropriate extension.

hexedit video.h264 //I change the 67 64 00 33 byte to 67 64 00 29. This is to replace what h264info does to change the level from 5.1 to 4.1. According to MP4Box's analysis of the resulting mp4 the file is in fact seen as a 4.1 file.

mkfifo audiodump.wav //to create a dummy wav file for mplayer to dump the audio into

neroAacEnc -lc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -channels 2 -ao pcm:fast //This is converting the ac3 to aac in a m4a container using the low complexity stereo that the xbox 360 requires. If the audio is dts then just change the .ac3 to .dts

MP4Box -new fileoutput.mp4 -add video.h264 -add audio.m4a -fps 23.976 //re-mux your new and improved video (with 4.1 level) and audio (aac-lc stereo) into a mp4 container.

```

Interesting information about MP4Box and files larger than 2GB (FIXED with the patch above)
[http://sourceforge.net/tracker/?func=detail&atid=571738&aid=1448512&group_id=84101](http://sourceforge.net/tracker/?func=detail&atid=571738&aid=1448512&group_id=84101)

---

### Post by gsmanners on 2008-02-06
You might want to look at this thread:

[http://ubuntuforums.org/showthread.php?t=684780](http://ubuntuforums.org/showthread.php?t=684780)

---

### Post by m3_del on 2008-02-06
I actually do not want to convert, I just want to re-mux. This takes much less time than re-encoding. I have come across that thread in several of my searches.

---

### Post by m3_del on 2008-02-07
**THIS IS NO LONGER RELEVANT TO THE INITIAL POST**

So here is the process I am taking to try to find out which step is the culprit. I am using the process of elimination, I know that the process in windows works, So I am creating to sets of files (video-win.h264 and video-lin.h264 etc). The steps I am checking against are

1. mkvextract
2. hexedit of the video.h264
3. re-encode of the ac3 to aac
4. mux using mp4box

In that order. So far I have tested steps 1 and 2 being done on a Linux box and the remaining steps on a windows box. Both successful! When I get home from work I will do the remaining 2. I suspect the re-encode is the glitch in all this. So far the output of mediainfo and mp4box -info between a windows created mp4 and Linux/windows hybrid created mp4 are identical. I hope to high heaven that does not continue, otherwise I will be at a complete loss.

As always any insight or help would be greatly appreciated.

---

### Post by m3_del on 2008-02-07
**THIS IS NO LONGER RELEVANT TO THE INITIAL POST**

So editing all the files on the Linux box and joining them together on the windows box works just fine. The problem seems to lie in the joining together of the files in Linux. Below are the results and there are differences in both.

In windows we see the NAL warning and in Linux we see it Adjusting the AVC length. I am not sure what the differences are. MP4Box on windows is version 0.4.4 and the Linux version is 0.4.2

Windows results using MP4Box
```
C:\Documents and Settings\craig ctr smith\Desktop>mp4box -add video-lin.h264 -ad
d audio-lin.m4a -fps 23.976 4.mp4
AVC-H264 import - frame size 1280 x 720 at 23.976 FPS
WARNING: NAL Unit type 31 not handled - adding/100)
WARNING: NAL Unit type 31 not handled - adding
Import results: 31441 samples - Slices: 404 I 12415 P 18622 B - 1 SEI - 397 IDR
        Stream uses B-slice references - max frame delay 2
IsoMedia import - track ID 1 - Audio (SR 48000 - 2 channels)
Saving to 4.mp4: 0.500 secs Interleaving

```

Linux results using MP4Box
```

craig@Media:~/Videos/Arrested Development - 2x03 - Amigos$ MP4Box -add video.h264 -add audio.m4a -fps 23.976 arrested.mp4
AVC-H264 import - frame size 1280 x 720 at 23.9760 FPS
Adjusting AVC SizeLength to 16 bits
Adjusting AVC SizeLength to 24 bits
Import results: 31441 samples - Slices: 404 I 12415 P 18622 B - 1 SEI - 397 IDR
        Stream uses B-slice references - max frame delay 2
IsoMedia import - track ID 1 - Audio (SR 48000 - 2 channels)
Saving to arrested.mp4: 0.500 secs Interleaving

```

I am going to try and upgrade Linux to the 0.4.4 version and see if that makes a difference.

---

### Post by kentay01 on 2008-02-09
Any luck with this M3? I'm essentially trying the same thing (only on linux though). I can get the files to play on Mac/Windows/Linux, just not Xbox. :(

---

### Post by m3_del on 2008-02-10
So far I have found that it is definitely the MP4Box step that is causing the incompatibility. 

Now when I re-mux with MP4Box using

```

MP4Box -new filename.mp4 -add video.h264 -add audio.m4a -fps 23.976

```
Everything is just great. I am not sure why adding the -new tag makes this process work. Now I am going to have to learn to Bash script and make one for this. I have been waiting for a reason to learn, besides just learning. So I guess this is my sign to start.

Anyone have any quick and dirty's on a52 to aac LC stero.

---

### Post by s0larian on 2008-02-11
Thank you for the nice tutorial. I was looking for exactly something like this. 

But I have one problem: in the step with neroAacEnc it never stops and the audio.m4a is growing for ever. Here is what it says:

```
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1600MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Using SSE optimized IMDCT transform
Using MMX optimized resampler

```

I don't know if it has something to do with the two mplayer error messages above. I used exactly the same commands as mentioned in the first post. Does anyone have any ideas why this is not working for me?

---

### Post by m3_del on 2008-02-11
> **s0larian said:**
> 
mplayer: could not connect to socket
mplayer: No such file or directory


The second error has me wondering if something is not quite right with what you are doing. Before you encode the audio you should have a video.h264 audio.ac3(or whatever container the file uses)  and audiodump.wav file. These files all need to exist. Well, should exist, all that is needed is the audidump and the audio files for this step.

What is the audio container you are starting with?

---

### Post by s0larian on 2008-02-11
The extraction of  video.h264 and audio.ac3 out of the mkv file works just fine. I played them both successfully with the mplayer. And I created the audiodump.wav. But for some reason the converison of the ac3 to aac ist not working, it just doesnt stop to encode and would lead to a file with unlimited size. I have no clue why this is happening. Maybe I will try it on another Linux box.

I googled for the mplayer error messages and found many people also having these messages. So I don't really think they are correlated to this encoding problem.

---

### Post by m3_del on 2008-02-11
When I run the Nero command this is the output I get. Hope this helps some.

```

[2] 20366
*************************************************************
*                                                           *
*  Nero Digital Audio Reference MPEG-4 & 3GPP Audio Encoder *
*  Copyright 2007 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Aug  6 2007                          *
*                                                           *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing audio.ac3.
libavformat file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO PCM] File: audiodump.wav (WAVE)
PCM: Samplerate: 48000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...

```

---

### Post by m3_del on 2008-02-11
[http://www.soccio.it/michelinux/2008/01/27/gtkpod-09912-backport-for-ubuntu-gutsy-gibbon/](http://www.soccio.it/michelinux/2008/01/27/gtkpod-09912-backport-for-ubuntu-gutsy-gibbon/)

Here are some Deb's for Mpeg4ip, got some config errors but mp4creator still appears to work.

---

### Post by s0larian on 2008-02-12
Thank you for your help. I believe ```
mplayer audio.ac3 -vc null -vo null -channels 2 -ao pcm:fast 
```  is not working working . When I convert the audio.ac3 with ffmpeg to a wav file, and do the neroAacEnc afterward with that wav file, it is working. 

My output of "mplayer audio.ac3 -vc null -vo null -channels 2 -ao pcm:fast " is
```
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1600MHz (Family: 6, Model: 9, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Using SSE optimized IMDCT transform
Using MMX optimized resampler

```

and it is not stopping. Maybe there is something going wrong.I never see the output you have.

---

### Post by s0larian on 2008-02-12
**Solution to my problem**

I just found the solution. It was really silly, I had in the mplayer config file "loop=0" which means that it repeats everything endless. That is the reason why it never stopped. Now everything seems to work fine :-)

---

### Post by jexxie on 2008-02-12
This method didn't work for me -- I suspect that in my case, the 360 doesn't support the h264 stream that's inside the mkv, and that it needs to be completely re-encoded. :(

---

### Post by m3_del on 2008-02-12
an h.264 stream is an h.264 stream. This would not differ for anyone, unless you are not getting dashboard updates. Video re-encode is confirmed not needed (For most mkv h.264 streams) I have seen a couple scene releases that don't have the same beginning hex values. Not sure why that is but "It is what it is"

Would you mind sharing the mkvinfo output of the mkv file in question?

---

### Post by m3_del on 2008-02-12
> I just found the solution. It was really silly, I had in the mplayer config file "loop=0" which means that it repeats everything endless. That is the reason why it never stopped. Now everything seems to work fine

Is this working for you with files larger than 2 gb?

---

### Post by jexxie on 2008-02-13
Here it is:
```
+ EBML head
|+ Doc type: matroska
|+ Doc type version: 1
|+ Doc type read version: 1
+ Segment, size 1153738746
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4027)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.7 + libmatroska v0.8.1
| + Writing application: mkvmerge v2.0.2 ('You're My Flame') built on Sep 20 2007 09:25:45
| + Duration: 2595.968s (00:43:15.968000000)
| + Date: Tue Jan 15 03:43:23 2008 UTC
| + Segment UID: 0x6d 0xc5 0xa7 0x4c 0xba 0x32 0xd1 0x8f 0x03 0xe3 0xe2 0x69 0x35 0xf4 0x37 0xd1
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 1851004858
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: A_AC3
|  + Codec decode all: 1
|  + Default duration: 32.000ms (31.250 fps for a video track)
|  + Language: und
|  + Audio track
|   + Sampling frequency: 48000.000000
|   + Channels: 6
| + A track
|  + Track number: 2
|  + Track UID: 1
|  + Track type: video
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 1
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: V_MPEG4/ISO/AVC
|  + Codec decode all: 1
|  + CodecPrivate, length 39
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Language: eng
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 720
|   + Interlaced: 0
|   + Display width: 16
|   + Display height: 9
|+ EbmlVoid (size: 1024)
|+ Cluster
```

---

### Post by m3_del on 2008-02-13
In regards to the MP4Box issues with files larger than 2gb. There is a patch listed [HERE]("http://bugs.gentoo.org/show_bug.cgi?id=189630"). I do not know how to make this patch work. DO I run this prior to running ./configure? Also do I need to modify my directories, the references in the patch don't match what I have. Thanks in advance for any help!

---

### Post by kentay01 on 2008-02-17
Hey M3,

Man, I'm rooting for you! :)

As far as the patch file goes. You'd have to run it prior to installing. You can 'man patch' in order to see the syntax. Good luck, let us know if it works.

---

### Post by m3_del on 2008-02-17
So I need to run this after make but prior to make install if I am reading what you are saying correctly.

---

### Post by gsmanners on 2008-02-17
Isn't that a patch for a Makefile? If so, you'll need to do the patch, then configure, then make, then make install.

---

### Post by m3_del on 2008-02-17
Sweet thanks, I am such a newb to all of this. I will keep you all informed. I am currently having some other quite serious issues with my ubuntu machine. [http://ubuntuforums.org/showthread.php?t=698043](http://ubuntuforums.org/showthread.php?t=698043)

Read on and see if you can help! Thanks!

---

### Post by m3_del on 2008-02-18
> **jexxie said:**
> Here it is:
```
+ EBML head
|+ Doc type: matroska
|+ Doc type version: 1
|+ Doc type read version: 1
+ Segment, size 1153738746
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4027)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.7 + libmatroska v0.8.1
| + Writing application: mkvmerge v2.0.2 ('You're My Flame') built on Sep 20 2007 09:25:45
| + Duration: 2595.968s (00:43:15.968000000)
| + Date: Tue Jan 15 03:43:23 2008 UTC
| + Segment UID: 0x6d 0xc5 0xa7 0x4c 0xba 0x32 0xd1 0x8f 0x03 0xe3 0xe2 0x69 0x35 0xf4 0x37 0xd1
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 1851004858
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: A_AC3
|  + Codec decode all: 1
|  + Default duration: 32.000ms (31.250 fps for a video track)
|  + Language: und
|  + Audio track
|   + Sampling frequency: 48000.000000
|   + Channels: 6
| + A track
|  + Track number: 2
|  + Track UID: 1
|  + Track type: video
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 1
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: V_MPEG4/ISO/AVC
|  + Codec decode all: 1
|  + CodecPrivate, length 39
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Language: eng
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 720
|   + Interlaced: 0
|   + Display width: 16
|   + Display height: 9
|+ EbmlVoid (size: 1024)
|+ Cluster
```

Jexxie,  nothing looks wrong with this file, it is sc3 audio and the video uses the right stream. I have updated the steps above. Also when you Hexedit do those bytes not show up the same way I have listed above? Which part ends up not working right for you.

---

### Post by jexxie on 2008-02-18
The entire process is working for me in terms of the video dumping, hexedit (value is there, and I edit it properly, remux the audio/video -- the xbox 360 doesn't want to play it =p

Also, was a solution found so we could 'script' the hexedit bit?

---

### Post by vorcigernix on 2008-02-27
Hi, 
there is other option how to convert audio if that mkfifo way doesn't work for you.
```

a52dec -o wav audio.ac3 > audio.wav
neroAacEnc -lc  -if audio.wav -of audio.aac

```

Some launcher will be great, I am creating one for windows currently. I'll try to convert it to mono, but mono ide sucks, so it will take time.

---

### Post by jexxie on 2008-02-27
> **vorcigernix said:**
> 
Some launcher will be great, I am creating one for windows currently. I'll try to convert it to mono, but mono ide sucks, so it will take time.

I wrote a bash script for this -- it's mostly complete, you can grab it from here:
[http://ubuntuforums.org/showpost.php?p=4382989&postcount=24](http://ubuntuforums.org/showpost.php?p=4382989&postcount=24)

---

### Post by m3_del on 2008-02-28
Thanks jexxie, hey have you included audio detection for the a52 as vorcigernix mentioned above?

---

### Post by jexxie on 2008-02-28
I haven't yet -- it doesn't seem to be any different than using mplayer to output to wav.  Is there something I'm missing?

---

### Post by m3_del on 2008-02-28
For somereason when the audio is the a52 codec the mplayer way fails for me, maybe this a bad mplayer build, I will have to check it out

---

### Post by vorcigernix on 2008-02-29
Hi, nice script, but it have some issues. First is mentioned on beginning of script, x264 streams have to be copied and fixed to lvl 4.1 only. 
I'll make my try to script it by using your script, I never used script, but it looks easy enough.
//edit> I misread your scipt, in audio conversion it should work either your way.

---

### Post by vik.vaughn on 2008-03-09
I got this error when running the script:

```
Exiting... (End of file)
662's retcode: 0
success
 [x] Normalizing the audio.../usr/bin/converttoMP4: line 131: normalize-audio: command not found
  690's retcode: 127
failed
 [i] Showing the last 5 lines from the logfile (log.13:42:11-2008-03-09.txt)...
```

Also, will this play back movies that are larger than 4gb? I can't stream movies to my xbox that are larger than that unless they are WMV.

If I only have a 1080i tv, will I need to downscale 1080p movies or will the xbox do that for me?

---

### Post by jexxie on 2008-03-10
Regarding the error, it's pretty obvious that normalize-audio isn't installed (not sure why it's not autodetecting that that program isn't installed, please grab the latest version):
```
sudo apt-get install normalize-audio
```

I believe that the 360 should downscale the quality to your output device automatically, although if you downscale them, the filesize will be smaller -- on the flip side, if you downscale them, you will need to reencode the entire file, which takes awhile.  I have yet to test my script with the MP4Box patches listed at the top of the thread yet.

I pushed out another script version, here it is:
[http://ubuntuforums.org/showthread.php?p=4488837#post4488837](http://ubuntuforums.org/showthread.php?p=4488837#post4488837)

---

### Post by johnrhunt on 2008-07-17
Mplayer often throws up various warnings, you can generally ignore them... if it's working, it'll show you the status thingi that looks like this:
A:5190.3 ( 1:26:30.2) of 6928.4 ( 1:55:28.4)  5.8% 

Otherwise it'll just die with an error message.

Once I get it to finally work, I'll post something on my blog: [http://john-hunt.com](http://john-hunt.com) . Might take a bit of doing though as it *does* seem quite stubborn. The next step is getting windows media player 11 to add it to it's library properly.

* A quick note about the status thingi:
A:5190.3 ( 1:26:30.2) of 6928.4 ( 1:55:28.4)  5.8% 
           ^ Current frame time   ^ Last frame time
That gives you an idea of how long it will take.. does take a few mins on my core2/3GB ram, so don't expect miracles.

---

### Post by jexxie on 2008-07-17
So you you know, I've moved the most recent version of the script here:
[http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/](http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/)

Cheers all.

---

