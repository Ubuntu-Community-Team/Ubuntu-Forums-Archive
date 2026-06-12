---
title: "Convert mkv to mp4 to play on PS3 ?"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by davidme on 2007-09-11
How can I convert an mkv (HD) video file to mp4 so that I can play it on my PS3 ?

Source mkv .x264 destination mp4 (I think it should be .h264 as that is what ps3 supports

---

### Post by Eupham on 2007-10-08
bump I have the same problem

---

### Post by Prisma on 2007-10-17
i am also interested to know how to convert .mkv to .avi or .mp4 in ubuntu.

---

### Post by rahimveron on 2007-11-20
Anybody have a solution?

---

### Post by shirilover on 2007-11-20
It may be possible to do this using Avidemux.
I have not tried to yet, so I cannot guarantee success.

---

### Post by tuna74 on 2007-11-25
Shouldn't this be possible with ffmpeg or mencoder? Unfortunately, I don't know the right commands.....

---

### Post by chacham23 on 2007-11-25
I have the same problem but converting to **PSP**... I found that solution:
```

mencoder The.Departed.2006.HD.DVDRip.720p.x264.AC3-5.1-iLL.sample.mkv -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=9800:acodec=libfaac -af lavcresample=48000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -o aaa.mp4

```

but I can get the resolution higher for some reason!! when I try higher resolution(not 368:208 ) the psp dont succes to read it - **very strange!!!**

hope that link can help u too...

---

### Post by hansa56 on 2007-12-08
This is quite easy to do. Sorry for my english :-)
Note! This only works if the mkv file video track is H264!!!

First install mkvextract, mkvinfo, MP4Box, hexedit and mplayer
$ sudo apt-get install mkvtoolnix gpac hexedit mplayer

Then you need neroAacEnc. You may download it for free here:
[http://www.nero.com/eng/nero-aac-codec.html]("http://www.nero.com/eng/nero-aac-codec.html")
Unpack linux directory, chmod +x neroAacEnc and copy it to a location of your choice (whitin the path)

I've downloaded Heroes Season 2 episode 11 which as this filename: Heroes_S02E11_720p.mkv (and yes, this is legal in Norway!)

Then you have to find out which tracks contains the audio and video.
Run:
$ mkvinfo Heroes_S02E11_720p.mkv
Check out the printout to find the tracks.

(in my mkv file video is on track1 and audio is on track 2. Change the numbers to fit you mkv file)

Then demux the mkvfile by running:
$ mkvextract tracks Heroes_S02E11_720p.mkv 1:video.h264 2:audio.ac3

Next to do is to change one byte inside the video.h264.
$ hexedit video.h264
On the first line you should see this number combination:
"67 64 00 33"
change this to:
"67 64 00 29"
press ctrl-s to save and ctrl-x to exit

Then you need to convert audio to aac format.
$ mkfifo audiodump.wav
$ neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -ao pcm:fast
This may take a couple of minutes.

The only thing left is to mux the video and audio file:
$ MP4Box -add video.h264 -add audio.m4a Heroes_S02E11.mp4

All should be finished within 5 minutes because no video convertion is done.

Hans Audun
Rygge, Norway

---

### Post by davidme on 2007-12-15
This is quiet complicated. Is there are a simpler way. There are so many programs on windows which can just change say mkv to vob. Is there are something that can be done on Linux ?

Like a script ?

---

### Post by srmantis on 2007-12-15
to convert mkv to other format, I use the mencoder:
(sorry, i don't write good english)
first you install the mencoder:
sudo apt-get install mencoder

to convert:
video_in=video.mkv
video_out=video.avi

mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 video.mkv -o video.avi

you try to change the video_out for other format. the mencoder is very good program.
edit:10/03/2008
to extract subtitules or track audio, video, etc:
to extract subtitules from mkv file:
fileinput.mkv
now you extract the information from fileinput.mkv (it's a example)
mkvmerge -i fileinput.mkv
the result:
File 'fileinput.mkv': container: Matroska
Track ID 1: video (V_MS/VFW/FOURCC, H264)
Track ID 2: audio (A_AAC/MPEG2/LC/SBR)
Track ID 3: audio (A_AAC/MPEG2/LC/SBR)
Track ID 4: subtitles (S_VOBSUB)

the subtitules is in the track id 4, then
mkvextract tracks fileinput.mkv 4:subtitulesfileinput.srt

this process generates the subtitules: subtitulesfileinput.srt or two file subtitulesfileinput.idx y subtitulesfileinput.sub

with it's you must to have the subtitules and it change the name:
fileinput.mkv----->fileout.avi
subtitulesfileinput.srt------>fileout.srt
or
subtitulesfileinput.idx------>fileout.idx
subtitulesfileinput.sub------>fileout.sub

audio: track id 3
mkvextract tracks fileinput.mkv 3:audioout.ogg

SrMantis

---

### Post by davidme on 2007-12-15
Here is what is happening in Windows:

"Right, I've been helping the awfully nice people at Red Kawa test a new version of PS3 Video 9, their video conversion tool, and I've got some extremely good news

A lot of people have been trying (and failing) to convert MPEG4-AVC High Profile video in Matroska containers (i.e. the standard format on t'Internet for HD TV and movie rips) to a format compatible with the PS3's XMB without having to spend hours doing a full recode and it looks like Red Kawa have finally cracked it with v2.21. It's not doing any recoding of the video, just downmixing the audio (if necessary) adding some 'special sauce' (as they put it) to the video and remuxing as a .mp4 file."

From here: [http://www.avforums.com/forums/showthread.php?t=531985](http://www.avforums.com/forums/showthread.php?t=531985)


Is there anyway we can do this in Linux without rencoding ? Too much time it takes to re encode...

---

### Post by davidme on 2007-12-23
Anyone ?

I can only see that we have this:

[http://bunkus.org/videotools/mkvtoolnix/](http://bunkus.org/videotools/mkvtoolnix/) which can extract somehow from mkv to raw - I have no idea how ?

mp4box which I am not sure if it exists in Linux

There are probably other tools.

Any experts can help ?

---

### Post by Prisoner_97p904 on 2007-12-25
> **hansa56 said:**
> This is quite easy to do. Sorry for my english :-)
Note! This only works if the mkv file video track is H264!!!

First install mkvextract, mkvinfo, MP4Box, hexedit and mplayer
$ sudo apt.-get install mkvtoolnix gpac hexedit mplayer

Then you need neroAacEnc. You may download it for free here:
[http://www.nero.com/eng/nero-aac-codec.html]("http://www.nero.com/eng/nero-aac-codec.html")
Unpack linux directory, chmod +x neroAacEnc and copy it to a location of your choice (whitin the path)

I've downloaded Heroes Season 2 episode 11 which as this filename: Heroes_S02E11_720p.mkv (and yes, this is legal in Norway!)

Then you have to find out which tracks contains the audio and video.
Run:
$ mkvinfo Heroes_S02E11_720p.mkv
Check out the printout to find the tracks.

(in my mkv file video is on track1 and audio is on track 2. Change the numbers to fit you mkv file)

Then demux the mkvfile by running:
$ mkvextract tracks 1:video.h264 2:audio.ac3

Next to do is to change one byte inside the video.h264.
$ hexedit video.h264
On the first line you should see this number combination:
"67 64 00 33"
change this to:
"67 64 00 29"
press ctrl-s to save and ctrl-z to exit

Then you need to convert audio to aac format.
$ mkfifo audiodump.wav
$ neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -ao pcm:fast
This may take a couple of minutes.

The only thing left is to mux the video and audio file:
$ MP4Box -add video.h264 -add audio.m4a Heroes_S02E11.mp4

All should be finished within 5 minutes because no video convertion is done.

Hans Audun
Rygge, Norway

Thx, works without quality loss, and its a lot faster than when i convert. Perfect :)
Btw: when you exit hexedit, don't do do ctrl+s + ctrl+z, it puts the app in the background, use ctrl+x to exit it correctly.

Thx for guide I've been looking for, for a long time ;)

------

I have tried playing some movies on my ps3, and the sound is out of sync :( Does anyone know why or how to fix this?

---

### Post by specvthis on 2007-12-26
I have the same problem.  I hear that you can rip the mkv into a vob file in windows and the ps3 has no problem playing it.  Anyone have any idea how to do this?  someone made a windows program mkv2vob and a linux script to do the same would be awesome. 

I do not want to reencode due to loss of quaility and time.  A simple repackaging of the video/audio would be awesome.  Damn ps3, when will it support the open stuff.

---

### Post by pln on 2008-01-05
Hi, 

The audio sync problem is probably caused by using the wrong fps when muxing. MP4Box seems to default to 25 fps. The solution is to pass in the -fps parameter to MP4Box. You can get the frame rate for your h.264 stream by using mkvinfo. 

The other solution to mux everything into a vob file by using ffmpeg is a bit nicer (in a way that we're able to get AC3 sound then) but I haven't found anything similar to h264info which is needed to change the h.264 profile level to 4.1.  Why it's working with a simple hexedit for MP4Box I don't know, perhaps it's just takes the level from the first package? Preferable all packets should be changed , and I think that is what h264info (the win32 program) is doing?

---

### Post by Yamato on 2008-01-18
To get 5.1 sound with the neroAacEnc you have to add -channels 6 to mplayer, like this
---
mkfifo audiodump.wav
neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -channels 6 -ao pcm:fast
---

And remember to set the right fps rate with MP4Box to get the sound in sync.
---
MP4Box -add video.h264 -add audio.m4a -fps 23.98 output.mp4
---

---

### Post by danielmalmkvist on 2008-01-22
Hi

Adjusting the -fps solved my out of sync issue.

But I still can't play the file on my PS3, it tells me that the data is corrupt.

One step that did not work for me was the hexedit step. I could not find the string "67 64 00 33", I did find a similar string "67 xx xx 33" in the beginning of the video file but changing that didn't work. 

Does anyone have any information why the file is corrupt? 
What does the hex code mean, feels like a bit magic? is it different mp4 profiles or what is it?

Thanks
Daniel

PS. if someone know about a good stream hex editor (like sed but for hex) I can put the stuff in a script, which would make the process dead simple.

---

### Post by webjames on 2008-01-23
Hi, i cannot get this to work.  I think it might be because the audio in my mkv is DTS. there must be an easier way to remux my mkv into an mp4, or xvid.

anyone had any luck?

---

### Post by mgm2rr on 2008-03-06
I can't get this to work on my setup.  I am using a 32 bit dell with P4 processor, NVIDA graphics card, and Gutsy Gibbon installed.  II used the instructions described on the earlier page to use MP4Box, and it creates an MP4 file, but when I try to share it to PS3 using mediatomb it says that the it is unrecognized or something.  Does anyone have any advice on what may be going wrong?  Can mediatomb share MP4 files with PS3?  Any help would be appreciated, I have been struggling with this for over a week now.

---

### Post by disturbedite on 2008-03-06
its really easy to switch containers (such as mkv to mp4) with avidemux without converting the audio & video.  (assuming the audio & video is h264/x264/acc).

---

### Post by Deedlit on 2008-03-10
After three days of trying to make some mkv's into avi's and trying to put together the code that worked from what help was here, this is what we did.  This may not be the best solution but we were trying to hard encode subtitles into the avi.

We installed mkvtoolnix,  mplayer and mencoder.

In terminal:
```
mkvinfo "exact file name"
```           

{to determine what track the subtitles were on}

```
mkvextract tracks "file" [track #]:subtitles.srt
```

{this takes about 10 seconds}

```
mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 -sub "subtitles.srt" "file name" -o "output file name.avi"
```


Hope this may be of some help! Best of luck!

---

### Post by Poka64 on 2008-03-11
Trying to use mp4box but the only thing that happens is this:

```
AVC-H264 import - frame size 1280 x 720 at 23.9760 FPS
Adjusting AVC SizeLength to 16 bits
Adjusting AVC SizeLength to 24 bits
Import results: 106240 samples - Slices: 1395 I 61160 P 43685 B - 1 SEI - 1271 IDR
        Stream uses B-slice references - max frame delay 2
 (Feature Not Supported)Unknown input file type
Error importing audio.m4a: Feature Not Supported

```

Edit: I know what's wrong now, I'm not getting a audio.m4a at all when i use neroAacEnc :(

```
./neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -ao pcm:fast
```

---

### Post by vpapanik on 2008-03-16
A BIG thanks to hansa56 and Yamato for the excellent information. I have successfully converted a LOST .mkv episode which plays in my PS3. I have something more that is missing though : subtitles.

I have an .srt file with Greek subtitles that runs smoothly with the original .mkv file. Is there any way that I can include it in the .mp4 container ? I tried "-add <subtitle file name.srt>" but it doesn't work. I can neither see it in mplayer nor PS3.

And a question of pure curiosity : What does the byte change in .h264 file actually do ? 

Thanks a very lot. Vassilis

---

### Post by tigon5 on 2008-03-18
Ive tried hansa's approach but the ps3 doesn't recognise the file format.

my mkvinfo output is:
```

...
|+ Segment tracks
|  + Track type: video
|  + Codec ID: V_MPEG4/ISO/AVC
|   + Pixel width: 1280
|   + Pixel height: 544

|  + Track type: audio
|  + Codec ID: A_AC3


```

anything wrong here?


PS: in the line in his instructions
$ mkvextract tracks 1:video.h264 2:audio.ac3
you need to add the filename as such for it to work
$ mkvextract tracks myfilename.mkv 1:video.h264 2:audio.ac3
(with the numbers appropriately set)

---

### Post by fourforksache on 2008-04-01
Hi I'm trying to convert  also i have a problem converting the audio 

fourforksache@fourforksache-laptop:~$ neroAacEnc -lc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -channels 2 -ao pcm:fast
[1] 8127
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2050  @ 1.60GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

[2]+  Stopped                 mplayer audio.ac3 -vc null -vo null -channels 2 -ao pcm:fast
fourforksache@fourforksache-laptop:~$ bash: neroAacEnc: command not found

to be honest i don't really know what i'm doing i'm just trying to learn as i go whats wrong here?

---

### Post by Kilbasar on 2008-04-25
> **fourforksache said:**
> 
fourforksache@fourforksache-laptop:~$ bash: neroAacEnc: command not found


try doing "./neroAacEnc" instead of just "neroAacEnc", assuming you're in the directory you downloaded it to. if that doesn't work, you didn't download the nero package, or didn't make it executable.

```

wget http://ftp6.nero.com/tools/NeroDigitalAudio.zip
unzip NeroDigitalAudio.zip
mv linux/neroAacEnc .
chmod u+x neroAacEnc

```

Since I know terminals are a scary place for some, I put together a quick script to follow the wonderful instructions from hansa56. note you will need to have everything installed already (except hexedit) or it won't work. so first do:

```

sudo apt-get install mkvtoolnix gpac mplayer

```

Also, since this uses xxd instead of hexedit (that's your "sed for hex", danielmalmkvist, or at least allows you to pipe hex into sed and then back into hex :) ), it takes 5-10 minutes longer and requires up to a gig more free space during processing than if you modified it yourself. but other than selecting the tracks at the beginning, it does everything for you. neroAacEnc MUST be executable and in the same directory as this script! follow instructions above to make that so. then save the script (attached to this post), and:

```

chmod u+x mkv2mp4.sh
./mkv2mp4.sh [filename]

```

The resulting file (filename.mp4) will be in the same directory as the original. Make sure there is plenty of room in mkv2mp4.sh's working directory for intermediate files. Script is attached.

(and yes, i know i could have gotten the video track and fps non-interactively using something like awk, but i'm lazy. feel free to modify the script if you want.)

---

### Post by Mark'O on 2008-04-30
Some brilliant instructions here. Thanks to hansa56 & co. However I still have a peculiar problem with some audios. It appears that there is a codec missing. I just cannot figure out what it could be since libxine1-ffmpeg is installed and up to date. The prob looks as follows:
```

$ mkfifo audiodump.wav
$ neroAacEnc -lc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -channels 6 -ao pcm:fast
[5] 29792
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

MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing audio.ac3.
libavformat file format detected.
[mpeg2video @ 0x892a230]sequence header damaged
[lavf] Audio stream found, -aid 0
[lavf] Audio stream found, -aid 1
[lavf] Video stream found, -vid 2
[lavf] Audio stream found, -aid 3
[lavf] Audio stream found, -aid 4
[lavf] Audio stream found, -aid 5
[lavf] Video stream found, -vid 6
[lavf] Audio stream found, -aid 7
[lavf] Video stream found, -vid 8
[lavf] Audio stream found, -aid 9
[lavf] Audio stream found, -aid 10
[lavf] Audio stream found, -aid 11
[lavf] Video stream found, -vid 12
[lavf] Audio stream found, -aid 13
[lavf] Audio stream found, -aid 14
[lavf] Audio stream found, -aid 15
[lavf] Audio stream found, -aid 16
[lavf] Video stream found, -vid 17
[lavf] Video stream found, -vid 18
[lavf] Audio stream found, -aid 19
VIDEO:  [mpg2]  0x0  0bpp  0.083 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: null
Opening video decoder: [null] Null video decoder
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x3267706D.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
Cannot sync MAD frame
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [hwmpa] MPEG audio pass-through (fake decoder)
Cannot sync MPA frame: 0
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x50.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)

```
Any ideas?

---

### Post by kraft_ on 2008-05-05
I had a few issues with the neroAacEnc:

```

$ ls -l neroAacEnc
-rwxr-xr-x 1 <cut> <cut> 973300 2007-08-06 11:10 neroAacEnc

$ ./neroAacEnc
-bash: ./neroAacEnc: No such file or directory

$ strace ./neroAacEnc
execve("./neroAacEnc", ["./neroAacEnc"], [/* 20 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f45807b5000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0x7f45807b5000, 4096)            = 0
exit_group(1)                           = ?
Process 23131 detached

```

So i changed the script to use faac:
```

$ cat bin/mkv2mp4.sh
#!/bin/sh
# converts mkv to mp4
# Credits: orig script: Kilbasar , change to faac: kraft

# packages required:
# sudo apt-get install mkvtoolnix gpac mplayer faac

[ ! -r "$1" ] && echo "usage: $0 [filename]" && exit 1
bname=`basename $1`
dname=`dirname $1`
mkvinfo "$1" | grep -i track
echo "Which track is video? (generally 1 or 2)"
read vidtrack
echo "Which track is audio? (generally 1 or 2)"
read audtrack
echo "What is the video frames per second (fps)?"
read vidfps
mkvextract tracks $1 ${vidtrack}:video.h264 ${audtrack}:audio.ac3
xxd -g4 video.h264 | sed '0,/RE/s/67640033/67640029/' | xxd -r > video2.h264
mv video2.h264 video.h264
mkfifo audiodump.wav
faac -q 0.20 -o audio.m4a audiodump.wav & mplayer audio.ac3 -vc null -vo null -ao pcm:fast
rm audiodump.wav
MP4Box -fps $vidfps -add video.h264 -add audio.m4a ${dname}/${bname}.mp4
rm audio.m4a audio.ac3 video.h264

```

Big thanks to Kilbasar for the script and hansa56 & co for elerything else.

---

### Post by padams2002 on 2008-05-13
If you are using Ubuntu 64 and you keep getting: 
```

$ ./neroAacEnc
-bash: ./neroAacEnc: No such file or directory

```

You need to install the 32bit libs that neroAacEnc needs to run:

```

sudo apt-get install ia32-libs

```

Then neroAacEnc should work!

---

### Post by cookie__monster on 2008-05-14
Hi -

I have been trying to convert an mkv file to mp4 format in order to stream to my PS3 via fuppes.

Unfortunately I am having trouble with the neroAacEnc/mplayer command.  

For some reason mplayer does not recognize the codec -

Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
V:   2.0  52/ 52  0%  0%  0.0% 0 0 

I have tried to resolve this mplayer 'dvaudio' codec issue but was not able to.  Any help on this is very much appreciated.

I have no idea what to do at this point and any input would be great.

Thanks

---

### Post by Randall311 on 2008-05-14
Here is a Perl script that should help people automatically transcode an HD mkv file to mp4 format.  I got the original idea from a script by Josh Carrol, I hacked it up so that it is now automated (the original was very interactive).  It was released under the GPL v2, so have at it.  

```
#!/usr/bin/perl
#######################################################################
#
#  File:        mkv2mp4.pl
#  Author(s):   Justin Randall (randall311 AT yahoo DOT com)
#               Josh Carroll   (josh.carroll AT gmail DOT com)
#  Version:     0.1
#  Created:     29 April 2008
#  Last Change: Wed May 14 10:00 PM 2008 EDT
#  Description: This script takes an MKV file as input and produces
#               a MP4 (h264/aac) which will play back on the
#               Sony PlayStation 3 (tm)
#  Usage:       mkv2mp4.pl <maktrosa input file>
#  History:     none
#
#  Copyright (c) 2008 by Josh Carroll (josh.carroll AT gmail DOT com)
#  under the name mkv4ps3.  This is a highly modified version used to
#  produce an MP4 (h264/aac) from a mkv file in an automated fashion
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#  GNU General Public License for more details.
#
#######################################################################
use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);
use File::Basename;

my $prog = $0;
$prog =~ s/.*\///img;

if ($#ARGV != 0) {
   print "Usage: $prog <maktrosa input file>\n";
   exit 0;
}

# set the input based off the command arguments
my $opt_in = $ARGV[0];

my($name, $path, $suffix) = fileparse($opt_in, qr{\..*});

if ($suffix eq '') {
   print "input file did not contain a suffix!\n";
   exit -1;
}

# remove file extension from input file
my $char = 0;
my $basename = $opt_in;
while ($char ne '.') {
   $char = chop $basename;
}

# temoprary files and variables
my $opt_tmp = $basename;
$opt_tmp = "$opt_tmp";
my $opt_out = "$basename.mp4";
my $tmp_ac3 = "$name.ac3";
my $tmp_dts = "$name.dts";
my $tmp_h264 = "$name.h264";
my $tmp_wav_fifo = "$name.wav";
my $tmp_aac = "$name.aac";
my $tmp_mp4 = "$name.mp4";

# make sure we have all the tools
check_required_tools();

# make sure the mkv file is correct format
tprint("Checking input file format...\n");
check_resolution($opt_in);

tprint("Extracting mkv file...\n");
# get the fps of the video and the duration (in seconds) of the MKV, and
#	extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$audio_file,$channels) = extract_mkv($opt_in, $tmp_h264, 0,0);

# modify h264 header to change level_idc to 0x29
tprint("Changing h.264 stream's level_idc header...\n");
change_h264_level($tmp_h264);

tprint("Converting audio to aac...\n");
conv_to_aac($audio_file, $tmp_aac, $channels);

tprint("Creating mp4 file...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $tmp_mp4, $opt_out);

# cleanup and finsh processing
tprint("Cleaning up tmp files...\n");
unlink($tmp_ac3,$tmp_h264,$tmp_wav_fifo,$tmp_aac,$tmp_mp4);
tprint("Done!\n");

##############################################################################
# check the mkv file format
##############################################################################
sub check_resolution {
   my $mkv = shift;

   my $output = `mkvinfo "$mkv" 2>&1`;
   chomp($output);

   my $width = 0;
   if($output =~ /Pixel width:\s+(\d+)/i) {
      $width = $1;
      print "MSG - MkvInfo pixel width - $width \n";
   }
   if($width == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   my $height = 0;
   if($output =~ /Pixel height:\s+(\d+)/i) {
      $height = $1;
      print "MSG - MkvInfo pixel height - $height \n";
   }
   if($height == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   if($height % 16) {
      print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
      print "Consider using ffmpeg/mencoder to crop this video first.\n";
      exit 1;
   }
}

##############################################################################
# extract the video and audio raw tracks from the mkv continer
##############################################################################
sub extract_mkv {
   my ($in, $h264, $dont_extract, $channels) = @_;

   my $fps = -1;
   my $duration = -1;
   my $type = undef;
   my $audio_type = undef;
   my $video_type = undef;

   my ($audio_track_num, $h264_track_num) = (-1, -1);
   my ($found_video, $found_audio) = (0,0);

   my $cur_audio = 0;
   my $cur_video = 0;

   # find out which track is which
   my $curr_track_num = -1;

   my @output = `mkvinfo "$in" 2>&1`;
   chomp(@output);
   foreach my $line (@output) {
      if($found_video && $channels && $found_audio && $fps != -1 && defined $audio_type) {
         last;
      }
      if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
         my $tmp = $1;
         if($type =~ /video/i) {
            $fps = $tmp;
         }
      } elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
         $duration = $1;
      } elsif($line =~ /Track number:\s+(\d+)/i) {
         $curr_track_num = $1;
         next;
      } elsif($line =~ /Track type:\s+(\S+)/i) {
         if($curr_track_num == -1) {
            # we haven't found the track # yet, but we found the type.
            # this shouldn't happen
            print "Error, mkvinfo failed.\n";
            exit 1;
         }
         $type = $1;
         if($type =~ /audio/i) {
            if(! $found_audio) {
               $audio_track_num = $curr_track_num;
               $found_audio = 1;
               $cur_video = 0;
               $cur_audio = 1;
            }
         } else {
            if(! $found_video) {
               $h264_track_num = $curr_track_num;
               $found_video = 1;
               $cur_video = 1;
               $cur_audio = 0;
            }
         }
      } elsif($found_audio && $cur_audio && $line =~ /Codec ID:\s+(\S+)/i) {
         $audio_type = $1;
         print "MSG - MkvInfo Audio - $audio_type Track: $audio_track_num\n";
      } elsif($found_video && $cur_video && $line =~ /Codec ID:\s+(\S+)/i) {
         $video_type = $1;
         print "MSG - MkvInfo Video - $video_type Track: $h264_track_num\n";
      }

      if ($line =~ /Channels:\s+(\d+)/i) {
         $channels = $1;
         if ($channels == 6) {
            print "MSG - MkvInfo Audio Channels - (Dolby 5.1 / DTS)\n";
         } else {
            print "MSG - MkvInfo Audio Channels - (Stereo 2.1)\n";
         }
      }
   }

   if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
      print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
      exit 1;
   }

   my $audio_file;
   if($audio_type eq "A_DTS") {
      $audio_file = $tmp_dts;
   } elsif($audio_type eq "A_AC3") {
      $audio_file = $tmp_ac3;
   } else {
      print "Error: invalid audio type in mkv: $audio_type\n";
      exit 1;
   }

   print "mkvextract tracks \"$in\" $audio_track_num:$audio_file $h264_track_num:$tmp_h264\n";

   my $output = `mkvextract tracks "$in" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1`;

   if($?) {
      print "Error, mkvextract failed! output:\n\n$output\n";
      exit 1;
   }

   if($fps == -1) {
      print "Error, could not determine input MKV fps\n";
      exit 1;
   }

   return ($fps, $duration, $audio_file, $channels);
}

##############################################################################
# change h264 header level_idc to 0x29
##############################################################################
sub change_h264_level {
   my $file = shift;
   open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
   sysseek($fh, 7, 0);
   syswrite($fh,"\x29",1);
   close($fh);
}

##############################################################################
# convert audio AC3 -> WAV -> AAC
##############################################################################
sub conv_to_aac {
   my ($in, $aac, $channels) = @_;

   my $fifo = $tmp_wav_fifo;

   if ($channels == 6) {
      print "mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo\n";

      my $output = `mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1`;

      if($?) {
         tprint("mplayer/nero conversion to aac failed: $output\n");
         exit 1;
      }
   } else {
      print "mplayer $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo\n";

      my $output = `mplayer $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo 2>&1`;

      if($?) {
         tprint("mplayer/nero conversion to aac failed: $output\n");
         exit 1;
      }
   }

   print "neroAacEnc -ignorelength -q 0.38 -if $fifo -of $aac\n";

   system(`neroAacEnc -ignorelength -q 0.38 -if $fifo -of $aac `);

   # clean up the fifo and the ac3/dts file to save on disk space
   unlink($in);
   unlink($fifo);
}

##############################################################################
# remux the video and audio tracks in the mp4 format
##############################################################################
sub create_mp4 {
   my ($h264, $aac, $fps, $tmp_mp4, $outf) = @_;

   # size of h264 + aac
   my $total_size = 0;

   # split the file into 3.5 G chunks to avoid problems with
   # PS3 playback of 4G files, this is the size in KB
   my $split_size = 4000000;

   my $split = 0;

   # find out how big the existing file is. If it's less than
   # our split size, then don't bother splitting it
   my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
      $atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

   $total_size += $size;

   ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
      $atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

   $total_size += $size;

   # normalize to KB for comparison
   $total_size /= 1024;
   if($total_size > $split_size) {
      $split = 1;
   }

   my $split_str = "";
   if($split) {
      $split_str = "-splits $split_size";
   } else {
      $split_str = "";
   }

   my $cmd = "mp4box $split_str -add $h264 -add $aac -fps $fps -par 1=1:1 -lang eng \"$outf\" 2>&1";
   print "$cmd\n";

   my $output = `$cmd`;
   if($?) {
      print "mp4box creation of mp4 failed! output:\n\n$output\n";
      exit 1;
   }
}

##############################################################################
# make sure we have all the tools for the job
##############################################################################
sub check_required_tools {

   my $errors = 0;

   my @required = qw(mkvinfo.exe mkvextract ffmpeg mplayer mp4box neroAacEnc);
   foreach my $req_prog (@required) {
      my $found = 0;
      foreach my $path_ent (split(/:/, $ENV{PATH})) {
         if(-r "$path_ent/$req_prog") {
            $found = 1;
            last;
         }
      }
      if(! $found) {
         $errors++;
         print "Error, required program: $req_prog not found. Please install it.\n";
      }
   }

   if($errors > 0) {
      exit 1;
   }
}

##############################################################################
# print status messages during remux process
##############################################################################
sub tprint {
   my $msg = shift;

   print $msg;
}

```

---

### Post by sevensixty on 2008-05-15
Randall311 id like to try out your script but i get the following error:

Error, required program: mkvinfo.exe not found. Please install it.
Error, required program: mp4box not found. Please install it.
Error, required program: neroAacEnc not found. Please install it.

However, all of the above are installed and working properly? Do i need to put your script in a specific folder?

Your help would be appreciated as you obviously know you stuff.

---

### Post by bugmonkey on 2008-05-17
I also had the same problems as the above post. It looks like the script is checking for slightly wrong dependences. After changing a couple of things in the code it's working fine with mkvinfo, neroAacEnc and MP4Box. I've attached the script or you can download the script via this [blog post](http://bugmonkeyblog.blogspot.com/2008/05/mkv2mp4.html"). I've only tried it on a single file so there might be other problems with it.

Thanks for all the help in this thread!

---

### Post by tjwallace on 2008-06-03
Here is an edited script that I have been using.  It has worked perfectly for me so far but I'm still not sure if I need to reroute the surround sound channels or not (when the original video was encoded with AAC audio).  I'll have to do some more testing.
```

#!/usr/bin/perl
#######################################################################
#
#  File:                 mkv2mp4.pl
#  Edited by:            Jeff Wallace   (jeff AT tjwallace DOT ca)
#  Original Author(s):   Justin Randall (randall311 AT yahoo DOT com)
#                        Josh Carroll   (josh.carroll AT gmail DOT com)
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#  GNU General Public License for more details.
#
#######################################################################
use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);
use File::Basename;

my $prog = $0;
$prog =~ s/.*\///img;

# set the input based off the command arguments
my ($opt_in, $opt_2ch, $opt_nosplit, $opt_noremix);

GetOptions(	'in=s' => \$opt_in,
		'2ch' => \$opt_2ch,
		'nosplit' => \$opt_nosplit,
		'noremix' => \$opt_noremix);

if (!$opt_in) {
   print "Usage: $prog -in <maktrosa input file> [-2ch -nosplit -noremix]\n";
   print "[-2ch]: Re-encode audio to 2 channels\n";
   print "[-nosplit]: Do NOT split the final MP4 file\n";
   print "[-noremix]: Do NOT remix the surround sound channels\n";
   exit 0;
}

my($name, $path, $suffix) = fileparse($opt_in, qr{\..*});

if ($suffix eq '') {
   print "input file did not contain a suffix!\n";
   exit -1;
}

# remove file extension from input file
my $char = 0;
my $basename = $opt_in;
while ($char ne '.') {
   $char = chop $basename;
}

# temoprary files and variables
my $opt_tmp = $basename;
$opt_tmp = "$opt_tmp";
my $opt_out = "$basename.mp4";
my $tmp_h264 = "$name.h264";
my $tmp_wav_fifo = "$name.wav";
my $tmp_aac = "$name.aac";

# make sure we have all the tools
check_required_tools();

# make sure the mkv file is correct format
tprint("Checking input file format...\n");
check_resolution($opt_in);

tprint("Extracting mkv file...\n");
# get the fps of the video and the duration (in seconds) of the MKV, and extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$channels) = extract_mkv($opt_in, $tmp_h264, 0,0);

# modify h264 header to change level_idc to 0x29
tprint("Changing h.264 stream's level_idc header...\n");
change_h264_level($tmp_h264);

tprint("Converting audio to aac...\n");
conv_to_aac($opt_in, $tmp_aac, $channels);

tprint("Creating mp4 file...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $opt_out);

# cleanup and finsh processing
tprint("Cleaning up tmp files...\n");
unlink($tmp_h264,$tmp_wav_fifo,$tmp_aac);
tprint("Done!\n");

##############################################################################
# check the mkv file format
##############################################################################
sub check_resolution {
   my $mkv = shift;

   my $output = `mkvinfo "$mkv" 2>&1`;
   chomp($output);

   my $width = 0;
   if($output =~ /Pixel width:\s+(\d+)/i) {
      $width = $1;
      print "MSG - MkvInfo pixel width - $width \n";
   }
   if($width == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   my $height = 0;
   if($output =~ /Pixel height:\s+(\d+)/i) {
      $height = $1;
      print "MSG - MkvInfo pixel height - $height \n";
   }
   if($height == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   if($height % 16) {
      print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
      print "Consider using ffmpeg/mencoder to crop this video first.\n";
      exit 1;
   }
}

##############################################################################
# extract the video and audio raw tracks from the mkv continer
##############################################################################
sub extract_mkv {
   my ($in, $h264, $dont_extract, $channels) = @_;

   my $fps = -1;
   my $duration = -1;
   my $type = undef;
   my $audio_type = undef;
   my $video_type = undef;

   my ($audio_track_num, $h264_track_num) = (-1, -1);
   my ($found_video, $found_audio) = (0,0);

   my $cur_audio = 0;
   my $cur_video = 0;

   # find out which track is which
   my $curr_track_num = -1;

   my @output = `mkvinfo "$in" 2>&1`;
   chomp(@output);
   foreach my $line (@output) {
      if($found_video && $channels && $found_audio && $fps != -1 && defined $audio_type) {
         last;
      }
      if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
         my $tmp = $1;
         if($type =~ /video/i) {
            $fps = $tmp;
		if($fps == -1) {
		      print "Error, could not determine input MKV fps\n";
		      exit 1;
		   }
            print "MSG - MkvInfo Video - fps: $fps\n";
         }
      } elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
         $duration = $1;
      } elsif($line =~ /Track number:\s+(\d+)/i) {
         $curr_track_num = $1;
         next;
      } elsif($line =~ /Track type:\s+(\S+)/i) {
         if($curr_track_num == -1) {
            # we haven't found the track # yet, but we found the type.
            # this shouldn't happen
            print "Error, mkvinfo failed.\n";
            exit 1;
         }
         $type = $1;
         if($type =~ /audio/i) {
            if(! $found_audio) {
               $audio_track_num = $curr_track_num;
               $found_audio = 1;
               $cur_video = 0;
               $cur_audio = 1;
            }
         } else {
            if(! $found_video) {
               $h264_track_num = $curr_track_num;
               $found_video = 1;
               $cur_video = 1;
               $cur_audio = 0;
            }
         }
      } elsif($found_audio && $cur_audio && $line =~ /Codec ID:\s+(\S+)/i) {
         $audio_type = $1;
         print "MSG - MkvInfo Audio - $audio_type Track: $audio_track_num\n";
      } elsif($found_video && $cur_video && $line =~ /Codec ID:\s+(\S+)/i) {
         $video_type = $1;
         print "MSG - MkvInfo Video - $video_type Track: $h264_track_num\n";
      }

      if ($line =~ /Channels:\s+(\d+)/i) {
         $channels = $1;
         if ($channels == 6) {
            print "MSG - MkvInfo Audio Channels - 6 - (Dolby 5.1 / DTS)\n";
         } else {
            print "MSG - MkvInfo Audio Channels - 2 - (Stereo 2.1)\n";
         }
      }
   }

   if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
      print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
      exit 1;
   }

   my $audio_file;

   if ($audio_type ne "A_DTS" && $audio_type ne "A_AC3") {
      if ($audio_type eq "A_AAC") {
          print "No audio channel remix needed...\n";
          #$opt_noremix = 1;
      } else {
          print "Error: invalid audio type in mkv: $audio_type\n";
          exit 1;
      }
   }

    print "mkvextract tracks \"$in\" $h264_track_num:$tmp_h264\n";

   my $output = `mkvextract tracks "$in" $h264_track_num:$tmp_h264`;

   if($?) {
      print "Error, mkvextract failed! output:\n\n$output\n";
      exit 1;
   }

   return ($fps, $duration, $channels);
}

##############################################################################
# change h264 header level_idc to 0x29
##############################################################################
sub change_h264_level {
   my $file = shift;
   open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
   sysseek($fh, 7, 0);
   syswrite($fh,"\x29",1);
   close($fh);
}

##############################################################################
# convert audio AC3 -> WAV -> AAC
##############################################################################
sub conv_to_aac {
	my ($in, $aac, $channels) = @_;

	my $fifo = $tmp_wav_fifo;
	print "Making fifo: $fifo\n";
	system("mkfifo $fifo");

	if($?) {
		print "mkfifo failed -- $!\n";
		exit 1;
	}

	if ($channels == 6 && !$opt_2ch) {
		my $channelstr;
		if ($opt_noremix) {
	   		$channelstr = "";
		} else {
	   		$channelstr = "-af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3";
		}
		print "neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in $channelstr -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo\n";

		my $output = `neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in $channelstr -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo`;

		if($?) {
			tprint("mplayer/nero conversion to aac failed: $output\n");
			exit 1;
		}
	} else {
		print "neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo\n";

		my $output = `neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer -vo null -vc null $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo`;

		if($?) {
			tprint("mplayer/nero conversion to aac failed: $output\n");
			exit 1;
		}
	}

	my $strfix = substr($aac,0,rindex($aac,"."));

	print("MP4Box -raw 1 $aac\n");
	system("MP4Box -raw 1 $aac");
	print("mv ${strfix}_track1.aac $aac");
	system("mv ${strfix}_track1.aac $aac");

	# clean up the fifo and the ac3/dts file to save on disk space
	unlink($fifo);
}

##############################################################################
# remux the video and audio tracks in the mp4 format
##############################################################################
sub create_mp4 {
   my ($h264, $aac, $fps, $outf) = @_;

   # size of h264 + aac
   my $total_size = 0;

   # split the file into 3.5 G chunks to avoid problems with
   # PS3 playback of 4G files, this is the size in KB
   my $split_size = 3942400;

   my $split = 0;

   if ($opt_nosplit) {
	   # find out how big the existing file is. If it's less than
	   # our split size, then don't bother splitting it
	   my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
	      $atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

	   $total_size += $size;

	   ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
	      $atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

	   $total_size += $size;

	   # normalize to KB for comparison
	   $total_size /= 1024;
	   if($total_size > $split_size) {
	      $split = 1;
	   }
   }

   my $split_str = "";
   if($split) {
      $split_str = "-splits $split_size";
   } else {
      $split_str = "";
   }

   my $cmd = "MP4Box $split_str -add $h264 -add $aac -fps $fps -nosys -new \"$outf\" 2>&1";
   print "$cmd\n";

   my $output = `$cmd`;
   if($?) {
      print "MP4Box creation of mp4 failed! output:\n\n$output\n";
      exit 1;
   }
}

##############################################################################
# make sure we have all the tools for the job
##############################################################################
sub check_required_tools {

   my $errors = 0;

   my @required = qw(mkvinfo mkvextract mplayer MP4Box neroAacEnc);
   foreach my $req_prog (@required) {
      my $found = 0;
      foreach my $path_ent (split(/:/, $ENV{PATH})) {
         if(-r "$path_ent/$req_prog") {
            $found = 1;
            last;
         }
      }
      if(! $found) {
         $errors++;
         print "Error, required program: $req_prog not found. Please install it.\n";
      }
   }

   if($errors > 0) {
      exit 1;
   }
}

##############################################################################
# print status messages during remux process
##############################################################################
sub tprint {
   my $msg = shift;

   print $msg;
}

```

---

### Post by Randall311 on 2008-06-03
> **sevensixty said:**
> Randall311 id like to try out your script but i get the following error:

Error, required program: mkvinfo.exe not found. Please install it.
Error, required program: mp4box not found. Please install it.
Error, required program: neroAacEnc not found. Please install it.

However, all of the above are installed and working properly? Do i need to put your script in a specific folder?

Your help would be appreciated as you obviously know you stuff.Yeah sorry about that, the dependencies are case sensitive and mkvinfo should not have an .exe extension unless your copy of that application does.  Tjwallace has already fixed that line for us, it should read: ```
   my @required = qw(mkvinfo mkvextract mplayer MP4Box neroAacEnc);

```

---

### Post by wraithrmm on 2008-06-06
The script you provided sounds awsome and I've got it to run, but it errors saying:

Error: invalid audio type in mkv: A_AAC

Is ther any way to get it to deal with the AAC format?

Thanks. :-)

---

### Post by yodalives on 2008-06-06
This script works great when your file is 720, but when trying to do this with a file that is 1080, it breaks because 1080 is not divisible by 16:

>    if($height % 16) {
      print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
      print "Consider using ffmpeg/mencoder to crop this video first.\n";
      exit 1;
   }


I havent uncommented the section to try it yet.... Just wondering the best way to deal with this, crop with ffmpeg, scale the video?

---

### Post by tjwallace on 2008-06-06
> **yodalives said:**
> This script works great when your file is 720, but when trying to do this with a file that is 1080, it breaks because 1080 is not divisible by 16:



I havent uncommented the section to try it yet.... Just wondering the best way to deal with this, crop with ffmpeg, scale the video?

Try this script (it's not mine):
```

#!/usr/bin/perl

# mkv4ps3
#
# Copyright Josh Carroll <josh.carroll@gmail.com>
#
# Released under the GPL v2
#
# This script takes an MKV file as input and produces either
#	an AVI (xvid/ac3) or MP4 (h264/aac) which will play back
#	on the Sony PlayStation 3 (tm).
#
# By default, if the input file is 720p (or less), the script
#	will retain the h264 elemental stream and use it unmodified,
#	while transcoding the ac3 to 5.1 aac with proper channel
#	mapping.

# If the -target option is used to specify avi, then
#	the script uses ffmpeg to transcode to a high bitrate XVID
#	avi file, leaving the AC3 audio intact.
#
# If the input file is 1080p, then the script prompts the user
#	whether they would like to transcode the h264 elemental stream
#	to a high quality h264 stream that's Level High@4.1 compliant and
#	mux that with the transcoded aac audio, or whether they want to
#	transcode to avi (xvid/ac3). If the user has explicitly specified
#	the target, they are not prompted.

use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);

my $prog = $0;
$prog =~ s/.*\///img;

my ($opt_in, $opt_out, $opt_tmp, $opt_nosplit, $opt_thr, $opt_quiet, $opt_reenc,
	$opt_help, $opt_target, $opt_pad, $opt_2pass, $opt_verbose, $opt_force);

GetOptions( 'in=s' => \$opt_in,
			'out=s' => \$opt_out,
			'tmp=s' => \$opt_tmp,
			'nosplit' => \$opt_nosplit,
			'thr=s' => \$opt_thr,
			'target=s' => \$opt_target,
			'pad=s' => \$opt_pad,
			'2pass' => \$opt_2pass,
			'force' => \$opt_force,
			'h' => \$opt_help,
			'v' => \$opt_verbose);

if(! $opt_in || ! $opt_out || $opt_help) {
	print "Usage: $prog -in <in.mkv> -out <out dir>\n";
	print "		[ -tmp <dir> | -nosplit | -thr N | \n";
	print "			-target avi|mp4 | -pad <kbps>]\n\n";
	print "The -target option is generally only needed for 1080p input\n";
	print "	unless you want an avi (xvid/ac3), since the default is h264/aac\n\n";
	print "If target mode is avi and you want to increase the video bitrate,\n";
	print "	add -pad <kbps> to add additional bitrate to the xvid video.\n\n";
	exit 0;
}

# setup the tmp dir if necessary
setup_working_dirs();

# assume we need roughly 2x the input file size for storage (worse case scenario)
check_available_diskspace($opt_in);

check_required_tools();
tprint("Checking input file sanity...\n");
check_resolution($opt_in);

# output file(s) are based on input file name
if(! $opt_target) {
	if($opt_out !~ /\.mp4/i) {
		print "Warning: default target is avi but output file has a different extension.\n";
	}
} elsif( ($opt_target eq "mp4" && $opt_out !~ /\.mp4/i ) ||
	($opt_target eq "avi" && $opt_out !~ /\.avi/i) ) {
	print "Warning: target specified is $opt_target but output file has a different extension.\n";
}

if(defined $opt_target && $opt_target ne "mp4" && $opt_target ne "avi") {
	print "Invalid target: $opt_target\n";
	exit 1;
}

# setup tmp files
my $tmp_ac3 = "$opt_tmp/tmp.ac3";
my $tmp_dts = "$opt_tmp/tmp.dts";
my $tmp_h264 = "$opt_tmp/tmp.h264";
my $tmp_pre_reenc_h264 = "$opt_tmp/tmp_reenc.h264";
my $tmp_wav = "$opt_tmp/tmp.wav";
my $tmp_wav_fifo = "$opt_tmp/tmp.fifo.wav";
my $tmp_aac = "$opt_tmp/tmp.aac";
my $tmp_mp4 = "$opt_tmp/tmp.mp4";
my $tmp_2pass_log = "$opt_tmp/ffmpeg2pass";
my $tmp_2pass_real_path = "$tmp_2pass_log-0.log";

# if the user wants to transcode directly to avi, we skip all of the many
#	intermediate steps for mp4 creation (or re-encoding)
my $dont_extract = 0;
if(defined $opt_target && $opt_target eq "avi") {
	$dont_extract = 1;
	tprint("Reading mkv info...\n");
} else {
	tprint("Extracting mkv file...\n");
}

# get the fps of the video and the duration (in seconds) of the MKV, and
#	extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$audio_file) = extract_mkv($opt_in, $tmp_h264, $dont_extract);

if(defined $opt_target && $opt_target eq "avi") {
	tprint("Transcoding mkv to avi (this may take a while)...\n");
	mkv2avi($opt_in, $opt_out, $vid_fps, $duration, $tmp_2pass_log);
	tprint("Done!\n");
	unlink($tmp_2pass_real_path);
	rmdir($opt_tmp);
	exit(0);
} elsif(defined $opt_target && $opt_target eq "mp4") {
	tprint("Re-encoding h.264 elementa stream (this may take a while)...\n");
	reencode_h264($tmp_h264, $tmp_pre_reenc_h264, $duration, $tmp_2pass_log);
} else {
	tprint("Changing h.264 stream's level_idc header...\n");
	change_h264_level($tmp_h264);
}

tprint("Converting audio to aac...\n");
conv_to_aac($audio_file, $tmp_aac);

tprint("Creating mp4 file...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $tmp_mp4, $opt_out);

# cleanup
tprint("Cleaning up tmp directory...\n");
unlink($tmp_ac3,$tmp_h264,$tmp_wav,$tmp_aac,$tmp_mp4,$tmp_pre_reenc_h264,$tmp_2pass_real_path);
rmdir($opt_tmp);

tprint("Done!\n");
# done


sub check_resolution {
	my $mkv = shift;

	if($opt_verbose) {
		print "Running: mkvinfo \"$mkv\" 2>&1\n";
	}
	my $output = `mkvinfo "$mkv" 2>&1`;
	chomp($output);

	my $width = 0;
	if($output =~ /Pixel width:\s+(\d+)/i) {
		$width = $1;
	}
	if($width == 0) {
		print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
		exit 1;
	}

	my $height = 0;
	if($output =~ /Pixel height:\s+(\d+)/i) {
		$height = $1;
	}
	if($height == 0) {
		print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
		exit 1;
	}

	if($width > 1280) {
		if(! $opt_target) {
			print "The input file appears to need transcoding.\n";
			print "Would you like to transcode to avi (xvid/ac3: faster,\n";
			print "but slightly less video quality), or mp4 (h264/aac: slower,\n";
			print "and better video quality, but potential some loss in\n";
			print "audio quality).\n\n";
			
			while(! $opt_target) {
				print "Please enter your choice (avi,mp4): ";
				my $answer = <STDIN>;
				chomp($answer);
				if($answer =~ /avi/i) {
					$opt_target = "avi";
				} elsif($answer =~ /mp4/i) {
					$opt_target = "mp4";
				} else {
					print "Invalid response! Please try again\n";
				}
			}
		}
	}
	
	if($height % 16) {
		print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
		print "Consider using ffmpeg/mencoder to crop this video first.\n";
		exit 1;
	}
}


sub extract_mkv {
	my ($in, $h264, $dont_extract) = @_;

	my $fps = -1;
	my $duration = -1;
	my $type = undef;
	my $audio_type = undef;

	my ($audio_track_num, $h264_track_num) = (-1, -1);
	my ($found_video, $found_audio) = (0,0);

	# find out which track is which
	my $curr_track_num = -1;
	if($opt_verbose) {
		print "Running: mkvinfo \"$in\" 2>&1\n";
	}
	my @output = `mkvinfo "$in" 2>&1`;
	chomp(@output);
	foreach my $line (@output) {
		if($found_video && $found_audio && $fps != -1 && defined $audio_type) {
			last;
		}
		if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
			my $tmp = $1;
			if($type =~ /video/i) {
				$fps = $tmp;
			}
		} elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
			$duration = $1;
		} elsif($line =~ /Track number:\s+(\d+)/i) {
			$curr_track_num = $1;
			next;
		} elsif($line =~ /Track type:\s+(\S+)/i) {
			if($curr_track_num == -1) {
				# we haven't found the track # yet, but we found the type. this shouldn't happen
				print "Error, mkvinfo failed.\n";
				exit 1;
			}
			$type = $1;
			if($type =~ /audio/i) {
				if(! $found_audio) {
					$audio_track_num = $curr_track_num;
					$found_audio = 1;
				}
			} else {
				if(! $found_video) {
					$h264_track_num = $curr_track_num;
					$found_video = 1;
				}
			}
		} elsif($found_audio && $line =~ /Codec ID:\s+(\S+)/i) {
			if(! $audio_type) {
				$audio_type = $1;
			}
		}	
	}

	if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
		print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
		exit 1;
	}

	my $audio_file;
	if($audio_type eq "A_DTS") {
		$audio_file = $tmp_dts;
	} elsif($audio_type eq "A_AC3") {
		$audio_file = $tmp_ac3;
	} else {
		print "Error: invalid audio type in mkv: $audio_type\n";
		exit 1;
	}

	if(! $dont_extract) {
		if($opt_verbose) {
			print "Running: mkvextract tracks \"$in\" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1\n";
		}
		my $output = `mkvextract tracks "$in" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1`;
		if($?) {
			print "Error, mkvextract failed! output:\n\n$output\n";
			exit 1;
		}
	}

	if($fps == -1) {
		print "Error, could not determine input MKV fps\n";
		exit 1;
	}

	return ($fps, $duration, $audio_file);
}


sub is_dir_empty {
	my $dir = shift;

	my $count = 0;
	opendir my $fh, "$dir" or die "Cannot open directory: $dir\n";
	while(my $ent = readdir($fh)) {
		if($ent eq "." || $ent eq "..") {
			next;
		}

		$count++;
	}

	if($count > 0) {
		return 0;
	} else {
		return 1;
	}
}


sub change_h264_level {
	my $file = shift;

	open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
	sysseek($fh, 7, 0);
	syswrite($fh,"\x29",1);
	close($fh);

}

sub conv_to_aac {
	my ($in, $aac) = @_;

	my $fifo = $tmp_wav_fifo;

	if($opt_verbose) {
		print "Running mkfifo $fifo\n";
	}
	`mkfifo $fifo`;
	if($?) {
		print "mkfifo failed -- $!\n";
		exit 1;
	}

	if($opt_verbose) {
		print "Running neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac > /dev/null 2>&1 &\n";
	}
	system("neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac > /dev/null 2>&1 &");

	if($opt_verbose) {
		print "Running mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1\n";
	}
	my $output = `mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1`;
	if($?) {
		tprint("mplayer/nero conversion to aac failed: $output\n");
		exit 1;
	}

	# clean up the fifo and the ac3/dts file to save on disk space while we're muxing
	unlink($in);
	unlink($fifo);
}

sub create_mp4 {
	my ($h264, $aac, $fps, $tmp_mp4, $outf) = @_;

	# size of h264 + aac
	my $total_size = 0;

	# split the file into 3.5 G chunks to avoid problems with PS3 playback of 4G files
	# this is the size in KB
	my $split_size = 4000000;

	my $split = 0;

	if(! $opt_nosplit) {
		# find out how big the existing file is. If it's less than our split size, then
		#	don't bother splitting it
		my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
			$atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

		$total_size += $size;

		($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
			$atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

		$total_size += $size;

		# normalize to KB for comparison
		$total_size /= 1024;
		if($total_size > $split_size) {
			$split = 1;
		}
	}

	my $split_str = "";
	if($split) {
		$split_str = "-splits $split_size";
	} else {
		$split_str = "";
	}

	my $cmd = "mp4box $split_str -tmp $opt_tmp -add $h264 -fps $fps -add $aac -new \"$outf\" 2>&1";
	if($opt_verbose) {
		print "Running $cmd\n";
	}
	my $output = `$cmd`;
	if($?) {
		print "mp4box creation of mp4 failed! output:\n\n$output\n";
		exit 1;
	}
}

sub check_required_tools {

	my $errors = 0;

	my @required = qw(mkvinfo mkvextract ffmpeg mplayer mp4box neroAacEnc);
	foreach my $req_prog (@required) {
		my $found = 0;
		foreach my $path_ent (split(/:/, $ENV{PATH})) {
			if(-r "$path_ent/$req_prog") {
				$found = 1;
				last;
			}
		}
		if(! $found) {
			$errors++;
			print "Error, required program: $req_prog not found. Please install it.\n";
		}
	}

	if($errors > 0) {
		exit 1;
	}
}

sub tprint {
	my $msg = shift;

	if($opt_quiet) {
		return;
	}

	print $msg;
}

sub reencode_h264 {
	my ($in, $out, $duration, $tmp_2pass_log) = @_;

	# we want the file for the next step to be in the path pointed
	#	to be $in, so move it
	`mv -f $in $out`;

	# determine the input bitrate using size of file and duration
	my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
		$atime,$mtime,$ctime,$blksize,$blocks) = stat($out);

	# size is in bytes, we want bits
	$size *= 8;

	# figure out bitrate in kbps
	my $vbitrate = POSIX::floor($size / $duration / 1024);

	# in/out are "swapped" here, since we want the resulting file to be the
	#	$tmp_h264 path
	my $thr_str = "";
	if($opt_thr) {
		$thr_str = "-threads $opt_thr";
	}

	my $cmd = "ffmpeg -y $thr_str %PASS% -f h264 -i $out -vcodec libx264 -level 41 -coder 1 -flags +loop -flags2 +dct8x8 -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me umh -subq 5 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -refs 3 -bf 3 -trellis 1 -b ${vbitrate}k -maxrate ${vbitrate}k -f h264 %OUT%";

	if($opt_2pass) {
		print "Using 2-pass encode...\n";
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 1 -passlogfile $tmp_2pass_log/ig;
		$cmd1 =~ s/%OUT%/\/dev\/null/ig;

		if($opt_verbose) {
			print "Running (1st pass) $cmd1 2>&1\n";
		}
		my $pass1_out = `$cmd1 2>&1`;
		if($?) {
			print "First pass failed for x264 re-encode! output:\n\n$pass1_out\n";
			exit 1;
		}

		my $cmd2 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 2 -passlogfile $tmp_2pass_log/ig;
		$cmd2 =~ s/%OUT%/$out/ig;

		if($opt_verbose) {
			print "Running (2nd pass) $cmd2 2>&1\n";
		}
		my $pass2_out = `$cmd2 2>&1`;
		if($?) {
			print "Second pass failed for x264 re-encode! output:\n\n$pass2_out\n";
			exit 1;
		}
	} else {
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%//ig;
		$cmd1 =~ s/%OUT%/$out/ig;

		if($opt_verbose) {
			print "Running $cmd1 2>&1\n";
		}
		my $output = `$cmd1 2>&1`;
		if($?) {
			print "Re-encode of h264 stream failed. output:\n\n$output\n";
			exit 1;
		}
	}
}

sub mkv2avi {
	my ($in, $outf, $fps, $duration, $tmp_2pass_log) = @_;

	my $vbitrate = get_video_bitrate($in);

	if($opt_pad) {
		$vbitrate += $opt_pad;
	}

	my $thr_str = "";
	if($opt_thr) {
		$thr_str = "-threads $opt_thr";
	}
	
	my $cmd = "ffmpeg -y $thr_str %PASS% -i $in -vcodec mpeg4 -vtag XVID -b ${vbitrate}k -cmp 2 -subcmp 2 -trell 1 -mbd 2 -acodec copy -r $fps -f avi %OUT%";

	if($opt_2pass) {
		print "Using 2-pass encode...\n";
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 1 -passlogfile $tmp_2pass_log/ig;
		$cmd1 =~ s/%OUT%/\/dev\/null/ig;

		if($opt_verbose) {
			print "Running (1st pass) $cmd1 2>&1\n";
		}
		my $pass1_out = `$cmd1 2>&1`;
		if($?) {
			print "First pass failed for mkv -> avi conversion! output:\n\n$pass1_out\n";
			exit 1;
		}

		my $cmd2 = $cmd;
		$cmd2 =~ s/%PASS%/-pass 2 -passlogfile $tmp_2pass_log/ig;
		$cmd2 =~ s/%OUT%/$outf/ig;

		if($opt_verbose) {
			print "Running (2nd pass) $cmd2 2>&1\n";
		}
		my $pass2_out = `$cmd2 2>&1`;
		if($?) {
			print "Second pass failed for mkv -> avi conversion! output:\n\n$pass2_out\n";
			exit 1;
		}
	} else {
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%//ig;
		$cmd1 =~ s/%OUT%/$outf/ig;

		if($opt_verbose) {
			print "Running $cmd1 2>&1\n";
		}
		my $output = `$cmd1 2>&1`;
		if($?) {
			print "mkv to avi conversion failed. output:\n\n$output\n";
			exit 1;
		}
	}
}


sub get_video_bitrate {
	my $input = shift;

	my $bitrate = 0;

	if($opt_verbose) {
		print "Running ffmpeg -i \"$input\" 2>&1\n";
	}
	my $info = `ffmpeg -i "$input" 2>&1`;

	# determine the video bitrate, either from ffmpeg -i output directly
	#   or by assuming a constant average bitrate over the length of the video
	if($info =~ /Duration.*bitrate:\s+(\d+)\s+kb\/s/i) {
		$bitrate = $1;
	} else {
		# need to find the file size and video length to guesstimate
		my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
			$atime,$mtime,$ctime,$blksize,$blocks)
			= stat($input);
		$info =~ /Duration:\s+(\d+):(\d+):(\d+\.\d+),/img;
		if(! $1) {
			return 0;	
		}
		my $seconds = $1*60*60 + $2*60 + $3;
		$bitrate = floor($size*8 / $seconds / 1024);
	}

	if($bitrate == 0) {
		print "Could not determine bitrate! Corrupt file?\n";
		exit 1;
	}

	return $bitrate;
}

sub setup_working_dirs {

	my $default_tmp_dir = "/tmp/$prog";
	if(! $opt_tmp) {
		print "Warning, using default tmp directory: $default_tmp_dir\n";
		$opt_tmp = $default_tmp_dir;
	} else {
		$opt_tmp = realpath($opt_tmp);
	}

	if(-f $opt_tmp) {
		print "Error, tmp directory is already a file.\n";
		exit 1;
	} elsif(-d $opt_tmp) {
		if(! is_dir_empty($opt_tmp)) {
			print "Error, tmp directory is not empty.\n";
			exit 1;
		}
	} else {
		mkdir($opt_tmp, 0755);
		if(! -d $opt_tmp) {
			print "Could not create tmp directory!\n";
			exit 1;
		}
	}

	if(-f $opt_out) {
		print "Error, requested output file already exists!\n";
		exit 1;
	} elsif(-d $opt_out) {
		print "Error, requested output file is a directory.\n";
		exit 1;
	}
}

sub check_available_diskspace {
	my $in = shift;

	my $needed_size = 0;
	my $available_size = 0;
	my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
		$atime,$mtime,$ctime,$blksize,$blocks) = stat($in);

	# rough size needed (in bytes)
	$needed_size = 2 * $size;

	# check what's available in the specified tmp dir
	my $df = `BLOCKSIZE=1024 df $opt_tmp`;
	chomp($df);

	$df =~ /^\/\S+\s+(\d+)/imgs;
	$available_size = $1 * 1024;

	if($needed_size > $available_size) {
		if($opt_force) {
			print "Warning: temp directory may not have enough free space. But -force specified...\n";
		} else {
			my $human_size = $needed_size / 1024 / 1024;
			print "Error: not enough disk space to continue.\n";
			printf("Please use -tmp to specify a temp directory with at least %.2f MB free\n", $human_size);
			exit 1;
		}
	}
}

```

---

### Post by tjwallace on 2008-06-06
> **wraithrmm said:**
> The script you provided sounds awsome and I've got it to run, but it errors saying:

Error: invalid audio type in mkv: A_AAC

Is ther any way to get it to deal with the AAC format?

Thanks. :-)

Did you try the script from this ([http://ubuntuforums.org/showpost.php?p=5103770&postcount=34](http://ubuntuforums.org/showpost.php?p=5103770&postcount=34)) post?

---

### Post by yodalives on 2008-06-07
> **tjwallace said:**
> Try this script (it's not mine):
```

#!/usr/bin/perl

# mkv4ps3
#
# Copyright Josh Carroll <josh.carroll@gmail.com>
#
# Released under the GPL v2
#
# This script takes an MKV file as input and produces either
#	an AVI (xvid/ac3) or MP4 (h264/aac) which will play back
#	on the Sony PlayStation 3 (tm).
#
# By default, if the input file is 720p (or less), the script
#	will retain the h264 elemental stream and use it unmodified,
#	while transcoding the ac3 to 5.1 aac with proper channel
#	mapping.

# If the -target option is used to specify avi, then
#	the script uses ffmpeg to transcode to a high bitrate XVID
#	avi file, leaving the AC3 audio intact.
#
# If the input file is 1080p, then the script prompts the user
#	whether they would like to transcode the h264 elemental stream
#	to a high quality h264 stream that's Level High@4.1 compliant and
#	mux that with the transcoded aac audio, or whether they want to
#	transcode to avi (xvid/ac3). If the user has explicitly specified
#	the target, they are not prompted.

use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);

my $prog = $0;
$prog =~ s/.*\///img;

my ($opt_in, $opt_out, $opt_tmp, $opt_nosplit, $opt_thr, $opt_quiet, $opt_reenc,
	$opt_help, $opt_target, $opt_pad, $opt_2pass, $opt_verbose, $opt_force);

GetOptions( 'in=s' => \$opt_in,
			'out=s' => \$opt_out,
			'tmp=s' => \$opt_tmp,
			'nosplit' => \$opt_nosplit,
			'thr=s' => \$opt_thr,
			'target=s' => \$opt_target,
			'pad=s' => \$opt_pad,
			'2pass' => \$opt_2pass,
			'force' => \$opt_force,
			'h' => \$opt_help,
			'v' => \$opt_verbose);

if(! $opt_in || ! $opt_out || $opt_help) {
	print "Usage: $prog -in <in.mkv> -out <out dir>\n";
	print "		[ -tmp <dir> | -nosplit | -thr N | \n";
	print "			-target avi|mp4 | -pad <kbps>]\n\n";
	print "The -target option is generally only needed for 1080p input\n";
	print "	unless you want an avi (xvid/ac3), since the default is h264/aac\n\n";
	print "If target mode is avi and you want to increase the video bitrate,\n";
	print "	add -pad <kbps> to add additional bitrate to the xvid video.\n\n";
	exit 0;
}

# setup the tmp dir if necessary
setup_working_dirs();

# assume we need roughly 2x the input file size for storage (worse case scenario)
check_available_diskspace($opt_in);

check_required_tools();
tprint("Checking input file sanity...\n");
check_resolution($opt_in);

# output file(s) are based on input file name
if(! $opt_target) {
	if($opt_out !~ /\.mp4/i) {
		print "Warning: default target is avi but output file has a different extension.\n";
	}
} elsif( ($opt_target eq "mp4" && $opt_out !~ /\.mp4/i ) ||
	($opt_target eq "avi" && $opt_out !~ /\.avi/i) ) {
	print "Warning: target specified is $opt_target but output file has a different extension.\n";
}

if(defined $opt_target && $opt_target ne "mp4" && $opt_target ne "avi") {
	print "Invalid target: $opt_target\n";
	exit 1;
}

# setup tmp files
my $tmp_ac3 = "$opt_tmp/tmp.ac3";
my $tmp_dts = "$opt_tmp/tmp.dts";
my $tmp_h264 = "$opt_tmp/tmp.h264";
my $tmp_pre_reenc_h264 = "$opt_tmp/tmp_reenc.h264";
my $tmp_wav = "$opt_tmp/tmp.wav";
my $tmp_wav_fifo = "$opt_tmp/tmp.fifo.wav";
my $tmp_aac = "$opt_tmp/tmp.aac";
my $tmp_mp4 = "$opt_tmp/tmp.mp4";
my $tmp_2pass_log = "$opt_tmp/ffmpeg2pass";
my $tmp_2pass_real_path = "$tmp_2pass_log-0.log";

# if the user wants to transcode directly to avi, we skip all of the many
#	intermediate steps for mp4 creation (or re-encoding)
my $dont_extract = 0;
if(defined $opt_target && $opt_target eq "avi") {
	$dont_extract = 1;
	tprint("Reading mkv info...\n");
} else {
	tprint("Extracting mkv file...\n");
}

# get the fps of the video and the duration (in seconds) of the MKV, and
#	extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$audio_file) = extract_mkv($opt_in, $tmp_h264, $dont_extract);

if(defined $opt_target && $opt_target eq "avi") {
	tprint("Transcoding mkv to avi (this may take a while)...\n");
	mkv2avi($opt_in, $opt_out, $vid_fps, $duration, $tmp_2pass_log);
	tprint("Done!\n");
	unlink($tmp_2pass_real_path);
	rmdir($opt_tmp);
	exit(0);
} elsif(defined $opt_target && $opt_target eq "mp4") {
	tprint("Re-encoding h.264 elementa stream (this may take a while)...\n");
	reencode_h264($tmp_h264, $tmp_pre_reenc_h264, $duration, $tmp_2pass_log);
} else {
	tprint("Changing h.264 stream's level_idc header...\n");
	change_h264_level($tmp_h264);
}

tprint("Converting audio to aac...\n");
conv_to_aac($audio_file, $tmp_aac);

tprint("Creating mp4 file...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $tmp_mp4, $opt_out);

# cleanup
tprint("Cleaning up tmp directory...\n");
unlink($tmp_ac3,$tmp_h264,$tmp_wav,$tmp_aac,$tmp_mp4,$tmp_pre_reenc_h264,$tmp_2pass_real_path);
rmdir($opt_tmp);

tprint("Done!\n");
# done


sub check_resolution {
	my $mkv = shift;

	if($opt_verbose) {
		print "Running: mkvinfo \"$mkv\" 2>&1\n";
	}
	my $output = `mkvinfo "$mkv" 2>&1`;
	chomp($output);

	my $width = 0;
	if($output =~ /Pixel width:\s+(\d+)/i) {
		$width = $1;
	}
	if($width == 0) {
		print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
		exit 1;
	}

	my $height = 0;
	if($output =~ /Pixel height:\s+(\d+)/i) {
		$height = $1;
	}
	if($height == 0) {
		print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
		exit 1;
	}

	if($width > 1280) {
		if(! $opt_target) {
			print "The input file appears to need transcoding.\n";
			print "Would you like to transcode to avi (xvid/ac3: faster,\n";
			print "but slightly less video quality), or mp4 (h264/aac: slower,\n";
			print "and better video quality, but potential some loss in\n";
			print "audio quality).\n\n";
			
			while(! $opt_target) {
				print "Please enter your choice (avi,mp4): ";
				my $answer = <STDIN>;
				chomp($answer);
				if($answer =~ /avi/i) {
					$opt_target = "avi";
				} elsif($answer =~ /mp4/i) {
					$opt_target = "mp4";
				} else {
					print "Invalid response! Please try again\n";
				}
			}
		}
	}
	
	if($height % 16) {
		print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
		print "Consider using ffmpeg/mencoder to crop this video first.\n";
		exit 1;
	}
}


sub extract_mkv {
	my ($in, $h264, $dont_extract) = @_;

	my $fps = -1;
	my $duration = -1;
	my $type = undef;
	my $audio_type = undef;

	my ($audio_track_num, $h264_track_num) = (-1, -1);
	my ($found_video, $found_audio) = (0,0);

	# find out which track is which
	my $curr_track_num = -1;
	if($opt_verbose) {
		print "Running: mkvinfo \"$in\" 2>&1\n";
	}
	my @output = `mkvinfo "$in" 2>&1`;
	chomp(@output);
	foreach my $line (@output) {
		if($found_video && $found_audio && $fps != -1 && defined $audio_type) {
			last;
		}
		if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
			my $tmp = $1;
			if($type =~ /video/i) {
				$fps = $tmp;
			}
		} elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
			$duration = $1;
		} elsif($line =~ /Track number:\s+(\d+)/i) {
			$curr_track_num = $1;
			next;
		} elsif($line =~ /Track type:\s+(\S+)/i) {
			if($curr_track_num == -1) {
				# we haven't found the track # yet, but we found the type. this shouldn't happen
				print "Error, mkvinfo failed.\n";
				exit 1;
			}
			$type = $1;
			if($type =~ /audio/i) {
				if(! $found_audio) {
					$audio_track_num = $curr_track_num;
					$found_audio = 1;
				}
			} else {
				if(! $found_video) {
					$h264_track_num = $curr_track_num;
					$found_video = 1;
				}
			}
		} elsif($found_audio && $line =~ /Codec ID:\s+(\S+)/i) {
			if(! $audio_type) {
				$audio_type = $1;
			}
		}	
	}

	if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
		print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
		exit 1;
	}

	my $audio_file;
	if($audio_type eq "A_DTS") {
		$audio_file = $tmp_dts;
	} elsif($audio_type eq "A_AC3") {
		$audio_file = $tmp_ac3;
	} else {
		print "Error: invalid audio type in mkv: $audio_type\n";
		exit 1;
	}

	if(! $dont_extract) {
		if($opt_verbose) {
			print "Running: mkvextract tracks \"$in\" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1\n";
		}
		my $output = `mkvextract tracks "$in" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1`;
		if($?) {
			print "Error, mkvextract failed! output:\n\n$output\n";
			exit 1;
		}
	}

	if($fps == -1) {
		print "Error, could not determine input MKV fps\n";
		exit 1;
	}

	return ($fps, $duration, $audio_file);
}


sub is_dir_empty {
	my $dir = shift;

	my $count = 0;
	opendir my $fh, "$dir" or die "Cannot open directory: $dir\n";
	while(my $ent = readdir($fh)) {
		if($ent eq "." || $ent eq "..") {
			next;
		}

		$count++;
	}

	if($count > 0) {
		return 0;
	} else {
		return 1;
	}
}


sub change_h264_level {
	my $file = shift;

	open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
	sysseek($fh, 7, 0);
	syswrite($fh,"\x29",1);
	close($fh);

}

sub conv_to_aac {
	my ($in, $aac) = @_;

	my $fifo = $tmp_wav_fifo;

	if($opt_verbose) {
		print "Running mkfifo $fifo\n";
	}
	`mkfifo $fifo`;
	if($?) {
		print "mkfifo failed -- $!\n";
		exit 1;
	}

	if($opt_verbose) {
		print "Running neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac > /dev/null 2>&1 &\n";
	}
	system("neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac > /dev/null 2>&1 &");

	if($opt_verbose) {
		print "Running mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1\n";
	}
	my $output = `mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1`;
	if($?) {
		tprint("mplayer/nero conversion to aac failed: $output\n");
		exit 1;
	}

	# clean up the fifo and the ac3/dts file to save on disk space while we're muxing
	unlink($in);
	unlink($fifo);
}

sub create_mp4 {
	my ($h264, $aac, $fps, $tmp_mp4, $outf) = @_;

	# size of h264 + aac
	my $total_size = 0;

	# split the file into 3.5 G chunks to avoid problems with PS3 playback of 4G files
	# this is the size in KB
	my $split_size = 4000000;

	my $split = 0;

	if(! $opt_nosplit) {
		# find out how big the existing file is. If it's less than our split size, then
		#	don't bother splitting it
		my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
			$atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

		$total_size += $size;

		($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
			$atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

		$total_size += $size;

		# normalize to KB for comparison
		$total_size /= 1024;
		if($total_size > $split_size) {
			$split = 1;
		}
	}

	my $split_str = "";
	if($split) {
		$split_str = "-splits $split_size";
	} else {
		$split_str = "";
	}

	my $cmd = "mp4box $split_str -tmp $opt_tmp -add $h264 -fps $fps -add $aac -new \"$outf\" 2>&1";
	if($opt_verbose) {
		print "Running $cmd\n";
	}
	my $output = `$cmd`;
	if($?) {
		print "mp4box creation of mp4 failed! output:\n\n$output\n";
		exit 1;
	}
}

sub check_required_tools {

	my $errors = 0;

	my @required = qw(mkvinfo mkvextract ffmpeg mplayer mp4box neroAacEnc);
	foreach my $req_prog (@required) {
		my $found = 0;
		foreach my $path_ent (split(/:/, $ENV{PATH})) {
			if(-r "$path_ent/$req_prog") {
				$found = 1;
				last;
			}
		}
		if(! $found) {
			$errors++;
			print "Error, required program: $req_prog not found. Please install it.\n";
		}
	}

	if($errors > 0) {
		exit 1;
	}
}

sub tprint {
	my $msg = shift;

	if($opt_quiet) {
		return;
	}

	print $msg;
}

sub reencode_h264 {
	my ($in, $out, $duration, $tmp_2pass_log) = @_;

	# we want the file for the next step to be in the path pointed
	#	to be $in, so move it
	`mv -f $in $out`;

	# determine the input bitrate using size of file and duration
	my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
		$atime,$mtime,$ctime,$blksize,$blocks) = stat($out);

	# size is in bytes, we want bits
	$size *= 8;

	# figure out bitrate in kbps
	my $vbitrate = POSIX::floor($size / $duration / 1024);

	# in/out are "swapped" here, since we want the resulting file to be the
	#	$tmp_h264 path
	my $thr_str = "";
	if($opt_thr) {
		$thr_str = "-threads $opt_thr";
	}

	my $cmd = "ffmpeg -y $thr_str %PASS% -f h264 -i $out -vcodec libx264 -level 41 -coder 1 -flags +loop -flags2 +dct8x8 -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me umh -subq 5 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -refs 3 -bf 3 -trellis 1 -b ${vbitrate}k -maxrate ${vbitrate}k -f h264 %OUT%";

	if($opt_2pass) {
		print "Using 2-pass encode...\n";
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 1 -passlogfile $tmp_2pass_log/ig;
		$cmd1 =~ s/%OUT%/\/dev\/null/ig;

		if($opt_verbose) {
			print "Running (1st pass) $cmd1 2>&1\n";
		}
		my $pass1_out = `$cmd1 2>&1`;
		if($?) {
			print "First pass failed for x264 re-encode! output:\n\n$pass1_out\n";
			exit 1;
		}

		my $cmd2 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 2 -passlogfile $tmp_2pass_log/ig;
		$cmd2 =~ s/%OUT%/$out/ig;

		if($opt_verbose) {
			print "Running (2nd pass) $cmd2 2>&1\n";
		}
		my $pass2_out = `$cmd2 2>&1`;
		if($?) {
			print "Second pass failed for x264 re-encode! output:\n\n$pass2_out\n";
			exit 1;
		}
	} else {
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%//ig;
		$cmd1 =~ s/%OUT%/$out/ig;

		if($opt_verbose) {
			print "Running $cmd1 2>&1\n";
		}
		my $output = `$cmd1 2>&1`;
		if($?) {
			print "Re-encode of h264 stream failed. output:\n\n$output\n";
			exit 1;
		}
	}
}

sub mkv2avi {
	my ($in, $outf, $fps, $duration, $tmp_2pass_log) = @_;

	my $vbitrate = get_video_bitrate($in);

	if($opt_pad) {
		$vbitrate += $opt_pad;
	}

	my $thr_str = "";
	if($opt_thr) {
		$thr_str = "-threads $opt_thr";
	}
	
	my $cmd = "ffmpeg -y $thr_str %PASS% -i $in -vcodec mpeg4 -vtag XVID -b ${vbitrate}k -cmp 2 -subcmp 2 -trell 1 -mbd 2 -acodec copy -r $fps -f avi %OUT%";

	if($opt_2pass) {
		print "Using 2-pass encode...\n";
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 1 -passlogfile $tmp_2pass_log/ig;
		$cmd1 =~ s/%OUT%/\/dev\/null/ig;

		if($opt_verbose) {
			print "Running (1st pass) $cmd1 2>&1\n";
		}
		my $pass1_out = `$cmd1 2>&1`;
		if($?) {
			print "First pass failed for mkv -> avi conversion! output:\n\n$pass1_out\n";
			exit 1;
		}

		my $cmd2 = $cmd;
		$cmd2 =~ s/%PASS%/-pass 2 -passlogfile $tmp_2pass_log/ig;
		$cmd2 =~ s/%OUT%/$outf/ig;

		if($opt_verbose) {
			print "Running (2nd pass) $cmd2 2>&1\n";
		}
		my $pass2_out = `$cmd2 2>&1`;
		if($?) {
			print "Second pass failed for mkv -> avi conversion! output:\n\n$pass2_out\n";
			exit 1;
		}
	} else {
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%//ig;
		$cmd1 =~ s/%OUT%/$outf/ig;

		if($opt_verbose) {
			print "Running $cmd1 2>&1\n";
		}
		my $output = `$cmd1 2>&1`;
		if($?) {
			print "mkv to avi conversion failed. output:\n\n$output\n";
			exit 1;
		}
	}
}


sub get_video_bitrate {
	my $input = shift;

	my $bitrate = 0;

	if($opt_verbose) {
		print "Running ffmpeg -i \"$input\" 2>&1\n";
	}
	my $info = `ffmpeg -i "$input" 2>&1`;

	# determine the video bitrate, either from ffmpeg -i output directly
	#   or by assuming a constant average bitrate over the length of the video
	if($info =~ /Duration.*bitrate:\s+(\d+)\s+kb\/s/i) {
		$bitrate = $1;
	} else {
		# need to find the file size and video length to guesstimate
		my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
			$atime,$mtime,$ctime,$blksize,$blocks)
			= stat($input);
		$info =~ /Duration:\s+(\d+):(\d+):(\d+\.\d+),/img;
		if(! $1) {
			return 0;	
		}
		my $seconds = $1*60*60 + $2*60 + $3;
		$bitrate = floor($size*8 / $seconds / 1024);
	}

	if($bitrate == 0) {
		print "Could not determine bitrate! Corrupt file?\n";
		exit 1;
	}

	return $bitrate;
}

sub setup_working_dirs {

	my $default_tmp_dir = "/tmp/$prog";
	if(! $opt_tmp) {
		print "Warning, using default tmp directory: $default_tmp_dir\n";
		$opt_tmp = $default_tmp_dir;
	} else {
		$opt_tmp = realpath($opt_tmp);
	}

	if(-f $opt_tmp) {
		print "Error, tmp directory is already a file.\n";
		exit 1;
	} elsif(-d $opt_tmp) {
		if(! is_dir_empty($opt_tmp)) {
			print "Error, tmp directory is not empty.\n";
			exit 1;
		}
	} else {
		mkdir($opt_tmp, 0755);
		if(! -d $opt_tmp) {
			print "Could not create tmp directory!\n";
			exit 1;
		}
	}

	if(-f $opt_out) {
		print "Error, requested output file already exists!\n";
		exit 1;
	} elsif(-d $opt_out) {
		print "Error, requested output file is a directory.\n";
		exit 1;
	}
}

sub check_available_diskspace {
	my $in = shift;

	my $needed_size = 0;
	my $available_size = 0;
	my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
		$atime,$mtime,$ctime,$blksize,$blocks) = stat($in);

	# rough size needed (in bytes)
	$needed_size = 2 * $size;

	# check what's available in the specified tmp dir
	my $df = `BLOCKSIZE=1024 df $opt_tmp`;
	chomp($df);

	$df =~ /^\/\S+\s+(\d+)/imgs;
	$available_size = $1 * 1024;

	if($needed_size > $available_size) {
		if($opt_force) {
			print "Warning: temp directory may not have enough free space. But -force specified...\n";
		} else {
			my $human_size = $needed_size / 1024 / 1024;
			print "Error: not enough disk space to continue.\n";
			printf("Please use -tmp to specify a temp directory with at least %.2f MB free\n", $human_size);
			exit 1;
		}
	}
}

```

Strangely, the same thing. mkvinfo on the file states that the pixel heigh is 1080, which is not actually divisible by 16.
```

|  + Video track
|   + Pixel width: 1920
|   + Pixel height: 1080
|   + Interlaced: 0
|   + Display width: 16
|   + Display height: 9

```

When running the script I get:
```

Checking input file sanity...
Error, height must be a multiple of 16 for the PS3 to recognize the file.
Consider using ffmpeg/mencoder to crop this video first.

```

Wondering if it's the file at this point. I'll need to get another 1080 file to see if I get the same results.

Thanks

---

### Post by yodalives on 2008-06-07
I think it was the file.

Most other 1080 video files are acutally 1080x816 or 1080x800 which is actually divisible by 16.

It's nice being able to play videos out of the PS3 but it's not worth the extra effort. I was hoping not to have to buy a mini-ITX to use as a myth frontend but with all these extra steps, it seems like the best way to go.

Thanks for the help

---

### Post by cookie__monster on 2008-06-07
when running the PERL script i get error -

Extracting mkv file...
Changing h.264 stream's level_idc header...
Converting audio to aac...
Creating mp4 file...
Use of uninitialized value in addition (+) at ./mkv2mp4.pl line 382.
MP4Box creation of mp4 failed! output:

AVC-H264 import - frame size 1280 x 528 at 23.976 FPS
Import results: 165876 samples - Slices: 2990 I 111844 P 51042 B - 1 SEI - 2447 IDR
        Stream uses B-slice references - max frame delay 2
Opening file /tmp/mkv2mp4.pl/tmp.aac failed
Error importing /tmp/mkv2mp4.pl/tmp.aac: Requested URL is not valid or cannot be found

can you please help to resolve this error?

thanks

---

### Post by tjwallace on 2008-06-09
> **cookie__monster said:**
> when running the PERL script i get error -

Extracting mkv file...
Changing h.264 stream's level_idc header...
Converting audio to aac...
Creating mp4 file...
Use of uninitialized value in addition (+) at ./mkv2mp4.pl line 382.
MP4Box creation of mp4 failed! output:

AVC-H264 import - frame size 1280 x 528 at 23.976 FPS
Import results: 165876 samples - Slices: 2990 I 111844 P 51042 B - 1 SEI - 2447 IDR
        Stream uses B-slice references - max frame delay 2
Opening file /tmp/mkv2mp4.pl/tmp.aac failed
Error importing /tmp/mkv2mp4.pl/tmp.aac: Requested URL is not valid or cannot be found

can you please help to resolve this error?

thanks
Hmm, is there a plus in the mkv file name?

---

### Post by cookie__monster on 2008-06-09
the file name is -

The.Movie.Film.720p.HDDVD.x264-DECiC

the size of the file is - 4.4 G

however i think it may have something to do with the MP4Box application.  

i appreciated any help provided.  i have been trying to convert mkv files into mp4 files to server to my PS3 for the last month.

it would be nice to resolve this.

thanks

---

### Post by tjwallace on 2008-06-09
> **cookie__monster said:**
> the file name is -

The.Movie.Film.720p.HDDVD.x264-DECiC

the size of the file is - 4.4 G

however i think it may have something to do with the MP4Box application.  

i appreciated any help provided.  i have been trying to convert mkv files into mp4 files to server to my PS3 for the last month.

it would be nice to resolve this.

thanks
```

#!/usr/bin/perl

# mkv4ps3
#
# Copyright Josh Carroll <josh.carroll@gmail.com>
#
# Released under the GPL v2
#
# This script takes an MKV file as input and produces either
#	an AVI (xvid/ac3) or MP4 (h264/aac) which will play back
#	on the Sony PlayStation 3 (tm).
#
# By default, if the input file is 720p (or less), the script
#	will retain the h264 elemental stream and use it unmodified,
#	while transcoding the ac3 to 5.1 aac with proper channel
#	mapping.

# If the -target option is used to specify avi, then
#	the script uses ffmpeg to transcode to a high bitrate XVID
#	avi file, leaving the AC3 audio intact.
#
# If the input file is 1080p, then the script prompts the user
#	whether they would like to transcode the h264 elemental stream
#	to a high quality h264 stream that's Level High@4.1 compliant and
#	mux that with the transcoded aac audio, or whether they want to
#	transcode to avi (xvid/ac3). If the user has explicitly specified
#	the target, they are not prompted.

use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);

my $prog = $0;
$prog =~ s/.*\///img;

my ($opt_in, $opt_out, $opt_tmp, $opt_nosplit, $opt_thr, $opt_quiet, $opt_reenc,
	$opt_help, $opt_target, $opt_pad, $opt_2pass, $opt_verbose, $opt_force);

GetOptions( 'in=s' => \$opt_in,
			'out=s' => \$opt_out,
			'tmp=s' => \$opt_tmp,
			'nosplit' => \$opt_nosplit,
			'thr=s' => \$opt_thr,
			'target=s' => \$opt_target,
			'pad=s' => \$opt_pad,
			'2pass' => \$opt_2pass,
			'force' => \$opt_force,
			'h' => \$opt_help,
			'v' => \$opt_verbose);

if(! $opt_in || ! $opt_out || $opt_help) {
	print "Usage: $prog -in <in.mkv> -out <out dir>\n";
	print "		[ -tmp <dir> | -nosplit | -thr N | \n";
	print "			-target avi|mp4 | -pad <kbps>]\n\n";
	print "The -target option is generally only needed for 1080p input\n";
	print "	unless you want an avi (xvid/ac3), since the default is h264/aac\n\n";
	print "If target mode is avi and you want to increase the video bitrate,\n";
	print "	add -pad <kbps> to add additional bitrate to the xvid video.\n\n";
	exit 0;
}

# setup the tmp dir if necessary
setup_working_dirs();

# assume we need roughly 2x the input file size for storage (worse case scenario)
check_available_diskspace($opt_in);

check_required_tools();
tprint("Checking input file sanity...\n");
check_resolution($opt_in);

# output file(s) are based on input file name
if(! $opt_target) {
	if($opt_out !~ /\.mp4/i) {
		print "Warning: default target is avi but output file has a different extension.\n";
	}
} elsif( ($opt_target eq "mp4" && $opt_out !~ /\.mp4/i ) ||
	($opt_target eq "avi" && $opt_out !~ /\.avi/i) ) {
	print "Warning: target specified is $opt_target but output file has a different extension.\n";
}

if(defined $opt_target && $opt_target ne "mp4" && $opt_target ne "avi") {
	print "Invalid target: $opt_target\n";
	exit 1;
}

# setup tmp files
my $tmp_ac3 = "$opt_tmp/tmp.ac3";
my $tmp_dts = "$opt_tmp/tmp.dts";
my $tmp_h264 = "$opt_tmp/tmp.h264";
my $tmp_pre_reenc_h264 = "$opt_tmp/tmp_reenc.h264";
my $tmp_wav = "$opt_tmp/tmp.wav";
my $tmp_wav_fifo = "$opt_tmp/tmp.fifo.wav";
my $tmp_aac = "$opt_tmp/tmp.aac";
my $tmp_mp4 = "$opt_tmp/tmp.mp4";
my $tmp_2pass_log = "$opt_tmp/ffmpeg2pass";
my $tmp_2pass_real_path = "$tmp_2pass_log-0.log";

# if the user wants to transcode directly to avi, we skip all of the many
#	intermediate steps for mp4 creation (or re-encoding)
my $dont_extract = 0;
if(defined $opt_target && $opt_target eq "avi") {
	$dont_extract = 1;
	tprint("Reading mkv info...\n");
} else {
	tprint("Extracting mkv file...\n");
}

# get the fps of the video and the duration (in seconds) of the MKV, and
#	extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$audio_file) = extract_mkv($opt_in, $tmp_h264, $dont_extract);

if(defined $opt_target && $opt_target eq "avi") {
	tprint("Transcoding mkv to avi (this may take a while)...\n");
	mkv2avi($opt_in, $opt_out, $vid_fps, $duration, $tmp_2pass_log);
	tprint("Done!\n");
	unlink($tmp_2pass_real_path);
	rmdir($opt_tmp);
	exit(0);
} elsif(defined $opt_target && $opt_target eq "mp4") {
	tprint("Re-encoding h.264 elementa stream (this may take a while)...\n");
	reencode_h264($tmp_h264, $tmp_pre_reenc_h264, $duration, $tmp_2pass_log);
} else {
	tprint("Changing h.264 stream's level_idc header...\n");
	change_h264_level($tmp_h264);
}

tprint("Converting audio to aac...\n");
conv_to_aac($audio_file, $tmp_aac);

tprint("Creating mp4 file...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $tmp_mp4, $opt_out);

# cleanup
tprint("Cleaning up tmp directory...\n");
unlink($tmp_ac3,$tmp_h264,$tmp_wav,$tmp_aac,$tmp_mp4,$tmp_pre_reenc_h264,$tmp_2pass_real_path);
rmdir($opt_tmp);

tprint("Done!\n");
# done


sub check_resolution {
	my $mkv = shift;

	if($opt_verbose) {
		print "Running: mkvinfo \"$mkv\" 2>&1\n";
	}
	my $output = `mkvinfo "$mkv" 2>&1`;
	chomp($output);

	my $width = 0;
	if($output =~ /Pixel width:\s+(\d+)/i) {
		$width = $1;
	}
	if($width == 0) {
		print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
		exit 1;
	}

	my $height = 0;
	if($output =~ /Pixel height:\s+(\d+)/i) {
		$height = $1;
	}
	if($height == 0) {
		print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
		exit 1;
	}

	if($width > 1280) {
		if(! $opt_target) {
			print "The input file appears to need transcoding.\n";
			print "Would you like to transcode to avi (xvid/ac3: faster,\n";
			print "but slightly less video quality), or mp4 (h264/aac: slower,\n";
			print "and better video quality, but potential some loss in\n";
			print "audio quality).\n\n";
			
			while(! $opt_target) {
				print "Please enter your choice (avi,mp4): ";
				my $answer = <STDIN>;
				chomp($answer);
				if($answer =~ /avi/i) {
					$opt_target = "avi";
				} elsif($answer =~ /mp4/i) {
					$opt_target = "mp4";
				} else {
					print "Invalid response! Please try again\n";
				}
			}
		}
	}
	
	if($height % 16) {
		print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
		print "Consider using ffmpeg/mencoder to crop this video first.\n";
		exit 1;
	}
}


sub extract_mkv {
	my ($in, $h264, $dont_extract) = @_;

	my $fps = -1;
	my $duration = -1;
	my $type = undef;
	my $audio_type = undef;

	my ($audio_track_num, $h264_track_num) = (-1, -1);
	my ($found_video, $found_audio) = (0,0);

	# find out which track is which
	my $curr_track_num = -1;
	if($opt_verbose) {
		print "Running: mkvinfo \"$in\" 2>&1\n";
	}
	my @output = `mkvinfo "$in" 2>&1`;
	chomp(@output);
	foreach my $line (@output) {
		if($found_video && $found_audio && $fps != -1 && defined $audio_type) {
			last;
		}
		if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
			my $tmp = $1;
			if($type =~ /video/i) {
				$fps = $tmp;
			}
		} elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
			$duration = $1;
		} elsif($line =~ /Track number:\s+(\d+)/i) {
			$curr_track_num = $1;
			next;
		} elsif($line =~ /Track type:\s+(\S+)/i) {
			if($curr_track_num == -1) {
				# we haven't found the track # yet, but we found the type. this shouldn't happen
				print "Error, mkvinfo failed.\n";
				exit 1;
			}
			$type = $1;
			if($type =~ /audio/i) {
				if(! $found_audio) {
					$audio_track_num = $curr_track_num;
					$found_audio = 1;
				}
			} else {
				if(! $found_video) {
					$h264_track_num = $curr_track_num;
					$found_video = 1;
				}
			}
		} elsif($found_audio && $line =~ /Codec ID:\s+(\S+)/i) {
			if(! $audio_type) {
				$audio_type = $1;
			}
		}	
	}

	if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
		print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
		exit 1;
	}

	my $audio_file;
	if($audio_type eq "A_DTS") {
		$audio_file = $tmp_dts;
	} elsif($audio_type eq "A_AC3") {
		$audio_file = $tmp_ac3;
	} else {
		print "Error: invalid audio type in mkv: $audio_type\n";
		exit 1;
	}

	if(! $dont_extract) {
		if($opt_verbose) {
			print "Running: mkvextract tracks \"$in\" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1\n";
		}
		my $output = `mkvextract tracks "$in" $audio_track_num:$audio_file $h264_track_num:$tmp_h264 2>&1`;
		if($?) {
			print "Error, mkvextract failed! output:\n\n$output\n";
			exit 1;
		}
	}

	if($fps == -1) {
		print "Error, could not determine input MKV fps\n";
		exit 1;
	}

	return ($fps, $duration, $audio_file);
}


sub is_dir_empty {
	my $dir = shift;

	my $count = 0;
	opendir my $fh, "$dir" or die "Cannot open directory: $dir\n";
	while(my $ent = readdir($fh)) {
		if($ent eq "." || $ent eq "..") {
			next;
		}

		$count++;
	}

	if($count > 0) {
		return 0;
	} else {
		return 1;
	}
}


sub change_h264_level {
	my $file = shift;

	open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
	sysseek($fh, 7, 0);
	syswrite($fh,"\x29",1);
	close($fh);

}

sub conv_to_aac {
	my ($in, $aac) = @_;

	my $fifo = $tmp_wav_fifo;

	if($opt_verbose) {
		print "Running mkfifo $fifo\n";
	}
	`mkfifo $fifo`;
	if($?) {
		print "mkfifo failed -- $!\n";
		exit 1;
	}

	if($opt_verbose) {
		print "Running neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac > /dev/null 2>&1 &\n";
	}
	system("neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac > /dev/null 2>&1 &");

	if($opt_verbose) {
		print "Running mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1\n";
	}
	my $output = `mplayer $in -af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo 2>&1`;
	if($?) {
		tprint("mplayer/nero conversion to aac failed: $output\n");
		exit 1;
	}

	# clean up the fifo and the ac3/dts file to save on disk space while we're muxing
	unlink($in);
	unlink($fifo);
}

sub create_mp4 {
	my ($h264, $aac, $fps, $tmp_mp4, $outf) = @_;

	# size of h264 + aac
	my $total_size = 0;

	# split the file into 3.5 G chunks to avoid problems with PS3 playback of 4G files
	# this is the size in KB
	my $split_size = 4000000;

	my $split = 0;

	if(false) {
		# find out how big the existing file is. If it's less than our split size, then
		#	don't bother splitting it
		my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,$atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

		$total_size += $size;

		($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,$atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

		$total_size += $size;

		# normalize to KB for comparison
		$total_size /= 1024;
		if($total_size > $split_size) {
			$split = 1;
		}
	}

	my $split_str = "";
	if($split) {
		$split_str = "-splits $split_size";
	} else {
		$split_str = "";
	}

	my $cmd = "mp4box $split_str -tmp $opt_tmp -add $h264 -fps $fps -add $aac -new \"$outf\" 2>&1";
	if($opt_verbose) {
		print "Running $cmd\n";
	}
	my $output = `$cmd`;
	if($?) {
		print "mp4box creation of mp4 failed! output:\n\n$output\n";
		exit 1;
	}
}

sub check_required_tools {

	my $errors = 0;

	my @required = qw(mkvinfo mkvextract ffmpeg mplayer mp4box neroAacEnc);
	foreach my $req_prog (@required) {
		my $found = 0;
		foreach my $path_ent (split(/:/, $ENV{PATH})) {
			if(-r "$path_ent/$req_prog") {
				$found = 1;
				last;
			}
		}
		if(! $found) {
			$errors++;
			print "Error, required program: $req_prog not found. Please install it.\n";
		}
	}

	if($errors > 0) {
		exit 1;
	}
}

sub tprint {
	my $msg = shift;

	if($opt_quiet) {
		return;
	}

	print $msg;
}

sub reencode_h264 {
	my ($in, $out, $duration, $tmp_2pass_log) = @_;

	# we want the file for the next step to be in the path pointed
	#	to be $in, so move it
	`mv -f $in $out`;

	# determine the input bitrate using size of file and duration
	my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
		$atime,$mtime,$ctime,$blksize,$blocks) = stat($out);

	# size is in bytes, we want bits
	$size *= 8;

	# figure out bitrate in kbps
	my $vbitrate = POSIX::floor($size / $duration / 1024);

	# in/out are "swapped" here, since we want the resulting file to be the
	#	$tmp_h264 path
	my $thr_str = "";
	if($opt_thr) {
		$thr_str = "-threads $opt_thr";
	}

	my $cmd = "ffmpeg -y $thr_str %PASS% -f h264 -i $out -vcodec libx264 -level 41 -coder 1 -flags +loop -flags2 +dct8x8 -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me umh -subq 5 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -refs 3 -bf 3 -trellis 1 -b ${vbitrate}k -maxrate ${vbitrate}k -f h264 %OUT%";

	if($opt_2pass) {
		print "Using 2-pass encode...\n";
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 1 -passlogfile $tmp_2pass_log/ig;
		$cmd1 =~ s/%OUT%/\/dev\/null/ig;

		if($opt_verbose) {
			print "Running (1st pass) $cmd1 2>&1\n";
		}
		my $pass1_out = `$cmd1 2>&1`;
		if($?) {
			print "First pass failed for x264 re-encode! output:\n\n$pass1_out\n";
			exit 1;
		}

		my $cmd2 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 2 -passlogfile $tmp_2pass_log/ig;
		$cmd2 =~ s/%OUT%/$out/ig;

		if($opt_verbose) {
			print "Running (2nd pass) $cmd2 2>&1\n";
		}
		my $pass2_out = `$cmd2 2>&1`;
		if($?) {
			print "Second pass failed for x264 re-encode! output:\n\n$pass2_out\n";
			exit 1;
		}
	} else {
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%//ig;
		$cmd1 =~ s/%OUT%/$out/ig;

		if($opt_verbose) {
			print "Running $cmd1 2>&1\n";
		}
		my $output = `$cmd1 2>&1`;
		if($?) {
			print "Re-encode of h264 stream failed. output:\n\n$output\n";
			exit 1;
		}
	}
}

sub mkv2avi {
	my ($in, $outf, $fps, $duration, $tmp_2pass_log) = @_;

	my $vbitrate = get_video_bitrate($in);

	if($opt_pad) {
		$vbitrate += $opt_pad;
	}

	my $thr_str = "";
	if($opt_thr) {
		$thr_str = "-threads $opt_thr";
	}
	
	my $cmd = "ffmpeg -y $thr_str %PASS% -i $in -vcodec mpeg4 -vtag XVID -b ${vbitrate}k -cmp 2 -subcmp 2 -trell 1 -mbd 2 -acodec copy -r $fps -f avi %OUT%";

	if($opt_2pass) {
		print "Using 2-pass encode...\n";
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%/-pass 1 -passlogfile $tmp_2pass_log/ig;
		$cmd1 =~ s/%OUT%/\/dev\/null/ig;

		if($opt_verbose) {
			print "Running (1st pass) $cmd1 2>&1\n";
		}
		my $pass1_out = `$cmd1 2>&1`;
		if($?) {
			print "First pass failed for mkv -> avi conversion! output:\n\n$pass1_out\n";
			exit 1;
		}

		my $cmd2 = $cmd;
		$cmd2 =~ s/%PASS%/-pass 2 -passlogfile $tmp_2pass_log/ig;
		$cmd2 =~ s/%OUT%/$outf/ig;

		if($opt_verbose) {
			print "Running (2nd pass) $cmd2 2>&1\n";
		}
		my $pass2_out = `$cmd2 2>&1`;
		if($?) {
			print "Second pass failed for mkv -> avi conversion! output:\n\n$pass2_out\n";
			exit 1;
		}
	} else {
		my $cmd1 = $cmd;
		$cmd1 =~ s/%PASS%//ig;
		$cmd1 =~ s/%OUT%/$outf/ig;

		if($opt_verbose) {
			print "Running $cmd1 2>&1\n";
		}
		my $output = `$cmd1 2>&1`;
		if($?) {
			print "mkv to avi conversion failed. output:\n\n$output\n";
			exit 1;
		}
	}
}


sub get_video_bitrate {
	my $input = shift;

	my $bitrate = 0;

	if($opt_verbose) {
		print "Running ffmpeg -i \"$input\" 2>&1\n";
	}
	my $info = `ffmpeg -i "$input" 2>&1`;

	# determine the video bitrate, either from ffmpeg -i output directly
	#   or by assuming a constant average bitrate over the length of the video
	if($info =~ /Duration.*bitrate:\s+(\d+)\s+kb\/s/i) {
		$bitrate = $1;
	} else {
		# need to find the file size and video length to guesstimate
		my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
			$atime,$mtime,$ctime,$blksize,$blocks)
			= stat($input);
		$info =~ /Duration:\s+(\d+):(\d+):(\d+\.\d+),/img;
		if(! $1) {
			return 0;	
		}
		my $seconds = $1*60*60 + $2*60 + $3;
		$bitrate = floor($size*8 / $seconds / 1024);
	}

	if($bitrate == 0) {
		print "Could not determine bitrate! Corrupt file?\n";
		exit 1;
	}

	return $bitrate;
}

sub setup_working_dirs {

	my $default_tmp_dir = "/tmp/$prog";
	if(! $opt_tmp) {
		print "Warning, using default tmp directory: $default_tmp_dir\n";
		$opt_tmp = $default_tmp_dir;
	} else {
		$opt_tmp = realpath($opt_tmp);
	}

	if(-f $opt_tmp) {
		print "Error, tmp directory is already a file.\n";
		exit 1;
	} elsif(-d $opt_tmp) {
		if(! is_dir_empty($opt_tmp)) {
			print "Error, tmp directory is not empty.\n";
			exit 1;
		}
	} else {
		mkdir($opt_tmp, 0755);
		if(! -d $opt_tmp) {
			print "Could not create tmp directory!\n";
			exit 1;
		}
	}

	if(-f $opt_out) {
		print "Error, requested output file already exists!\n";
		exit 1;
	} elsif(-d $opt_out) {
		print "Error, requested output file is a directory.\n";
		exit 1;
	}
}

sub check_available_diskspace {
	my $in = shift;

	my $needed_size = 0;
	my $available_size = 0;
	my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
		$atime,$mtime,$ctime,$blksize,$blocks) = stat($in);

	# rough size needed (in bytes)
	$needed_size = 2 * $size;

	# check what's available in the specified tmp dir
	my $df = `BLOCKSIZE=1024 df $opt_tmp`;
	chomp($df);

	$df =~ /^\/\S+\s+(\d+)/imgs;
	$available_size = $1 * 1024;

	if($needed_size > $available_size) {
		if($opt_force) {
			print "Warning: temp directory may not have enough free space. But -force specified...\n";
		} else {
			my $human_size = $needed_size / 1024 / 1024;
			print "Error: not enough disk space to continue.\n";
			printf("Please use -tmp to specify a temp directory with at least %.2f MB free\n", $human_size);
			exit 1;
		}
	}
}

```

Try this.  I turned off the splitting feature.

---

### Post by cookie__monster on 2008-06-09
the error has not bee resolved -


Warning, using default tmp directory: /tmp/mkv4ps3.pl
Checking input file sanity...
Extracting mkv file...
Changing h.264 stream's level_idc header...
Converting audio to aac...
Creating mp4 file...
MP4Box creation of mp4 failed! output:

AVC-H264 import - frame size 1280 x 528 at 23.976 FPS
Import results: 165876 samples - Slices: 2990 I 111844 P 51042 B - 1 SEI - 2447 IDR
        Stream uses B-slice references - max frame delay 2
Opening file /tmp/mkv4ps3.pl/tmp.aac failed
Error importing /tmp/mkv4ps3.pl/tmp.aac: Requested URL is not valid or cannot be found


are you able to solve this?

---

### Post by cookie__monster on 2008-06-09
are you removing the tmp.aac file before running the MP4Box command?

---

### Post by cookie__monster on 2008-06-09
the file being converted has audio codec AC3.  is mplayer capable of understanding this codec?

the sample file is being converted with any error but anything over 4G is failing when the audio format is AC3.

do you think this is the problem?  If yes - do you know a workaround?

---

### Post by tjwallace on 2008-06-10
> **cookie__monster said:**
> the file being converted has audio codec AC3.  is mplayer capable of understanding this codec?

the sample file is being converted with any error but anything over 4G is failing when the audio format is AC3.

do you think this is the problem?  If yes - do you know a workaround?
That script isn't mine, this one below is mine and it works pretty good (for me, I've done 4+ gb movies with AC3 audio):
```

#!/usr/bin/perl
#######################################################################
#
#  File:                 mkv2mp4.pl
#  Edited by:            Jeff Wallace   (jeff AT tjwallace DOT ca)
#  Original Author(s):   Justin Randall (randall311 AT yahoo DOT com)
#                        Josh Carroll   (josh.carroll AT gmail DOT com)
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#  GNU General Public License for more details.
#
#######################################################################
use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);
use File::Basename;

my $prog = $0;
$prog =~ s/.*\///img;

# set the input based off the command arguments
my ($opt_in, $opt_2ch, $opt_nosplit, $opt_noremix);

GetOptions(	'in=s' => \$opt_in,
		'2ch' => \$opt_2ch,
		'nosplit' => \$opt_nosplit,
		'noremix' => \$opt_noremix);

if (!$opt_in) {
   print "Usage: $prog -in <maktrosa input file> [-2ch -nosplit -noremix]\n";
   print "[-2ch]: Re-encode audio to 2 channels\n";
   print "[-nosplit]: Do NOT split the final MP4 file\n";
   print "[-noremix]: Do NOT remix the surround sound channels\n";
   exit 0;
}

my($name, $path, $suffix) = fileparse($opt_in, qr{\..*});

if ($suffix eq '') {
   print "input file did not contain a suffix!\n";
   exit -1;
}

# remove file extension from input file
my $char = 0;
my $basename = $opt_in;
while ($char ne '.') {
   $char = chop $basename;
}

# temoprary files and variables
my $opt_tmp = $basename;
$opt_tmp = "$opt_tmp";
my $opt_out = "$basename.mp4";
my $tmp_h264 = "$name.h264";
my $tmp_wav_fifo = "$name.wav";
my $tmp_aac = "$name.aac";

# make sure we have all the tools
check_required_tools();

# make sure the mkv file is correct format
tprint("Checking input file format...\n");
check_resolution($opt_in);

tprint("Extracting mkv file...\n");
# get the fps of the video and the duration (in seconds) of the MKV, and extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$channels) = extract_mkv($opt_in, $tmp_h264, 0,0);

# modify h264 header to change level_idc to 0x29
tprint("Changing h.264 stream's level_idc header...\n");
change_h264_level($tmp_h264);

tprint("Converting audio to aac...\n");
conv_to_aac($opt_in, $tmp_aac, $channels);

tprint("Creating mp4 file...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $opt_out);

# cleanup and finsh processing
tprint("Cleaning up tmp files...\n");
unlink($tmp_h264,$tmp_wav_fifo,$tmp_aac);
tprint("Done!\n");

##############################################################################
# check the mkv file format
##############################################################################
sub check_resolution {
   my $mkv = shift;

   my $output = `mkvinfo "$mkv" 2>&1`;
   chomp($output);

   my $width = 0;
   if($output =~ /Pixel width:\s+(\d+)/i) {
      $width = $1;
      print "MSG - MkvInfo pixel width - $width \n";
   }
   if($width == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   my $height = 0;
   if($output =~ /Pixel height:\s+(\d+)/i) {
      $height = $1;
      print "MSG - MkvInfo pixel height - $height \n";
   }
   if($height == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   if($height % 16) {
      print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
      print "Consider using ffmpeg/mencoder to crop this video first.\n";
      exit 1;
   }
}

##############################################################################
# extract the video and audio raw tracks from the mkv continer
##############################################################################
sub extract_mkv {
   my ($in, $h264, $dont_extract, $channels) = @_;

   my $fps = -1;
   my $duration = -1;
   my $type = undef;
   my $audio_type = undef;
   my $video_type = undef;

   my ($audio_track_num, $h264_track_num) = (-1, -1);
   my ($found_video, $found_audio) = (0,0);

   my $cur_audio = 0;
   my $cur_video = 0;

   # find out which track is which
   my $curr_track_num = -1;

   my @output = `mkvinfo "$in" 2>&1`;
   chomp(@output);
   foreach my $line (@output) {
      if($found_video && $channels && $found_audio && $fps != -1 && defined $audio_type) {
         last;
      }
      if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
         my $tmp = $1;
         if($type =~ /video/i) {
            $fps = $tmp;
		if($fps == -1) {
		      print "Error, could not determine input MKV fps\n";
		      exit 1;
		   }
            print "MSG - MkvInfo Video - fps: $fps\n";
         }
      } elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
         $duration = $1;
      } elsif($line =~ /Track number:\s+(\d+)/i) {
         $curr_track_num = $1;
         next;
      } elsif($line =~ /Track type:\s+(\S+)/i) {
         if($curr_track_num == -1) {
            # we haven't found the track # yet, but we found the type.
            # this shouldn't happen
            print "Error, mkvinfo failed.\n";
            exit 1;
         }
         $type = $1;
         if($type =~ /audio/i) {
            if(! $found_audio) {
               $audio_track_num = $curr_track_num;
               $found_audio = 1;
               $cur_video = 0;
               $cur_audio = 1;
            }
         } else {
            if(! $found_video) {
               $h264_track_num = $curr_track_num;
               $found_video = 1;
               $cur_video = 1;
               $cur_audio = 0;
            }
         }
      } elsif($found_audio && $cur_audio && $line =~ /Codec ID:\s+(\S+)/i) {
         $audio_type = $1;
         print "MSG - MkvInfo Audio - $audio_type Track: $audio_track_num\n";
      } elsif($found_video && $cur_video && $line =~ /Codec ID:\s+(\S+)/i) {
         $video_type = $1;
         print "MSG - MkvInfo Video - $video_type Track: $h264_track_num\n";
      }

      if ($line =~ /Channels:\s+(\d+)/i) {
         $channels = $1;
         if ($channels == 6) {
            print "MSG - MkvInfo Audio Channels - 6 - (Dolby 5.1 / DTS)\n";
         } else {
            print "MSG - MkvInfo Audio Channels - 2 - (Stereo 2.1)\n";
         }
      }
   }

   if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
      print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
      exit 1;
   }

   my $audio_file;

   if ($audio_type ne "A_DTS" && $audio_type ne "A_AC3") {
      if ($audio_type eq "A_AAC") {
          print "No audio channel remix needed...\n";
          #$opt_noremix = 1;
      } else {
          print "Error: invalid audio type in mkv: $audio_type\n";
          exit 1;
      }
   }

    print "mkvextract tracks \"$in\" $h264_track_num:$tmp_h264\n";

   my $output = `mkvextract tracks "$in" $h264_track_num:$tmp_h264`;

   if($?) {
      print "Error, mkvextract failed! output:\n\n$output\n";
      exit 1;
   }

   return ($fps, $duration, $channels);
}

##############################################################################
# change h264 header level_idc to 0x29
##############################################################################
sub change_h264_level {
   my $file = shift;
   open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
   sysseek($fh, 7, 0);
   syswrite($fh,"\x29",1);
   close($fh);
}

##############################################################################
# convert audio AC3 -> WAV -> AAC
##############################################################################
sub conv_to_aac {
	my ($in, $aac, $channels) = @_;

	my $fifo = $tmp_wav_fifo;
	print "Making fifo: $fifo\n";
	system("mkfifo $fifo");

	if($?) {
		print "mkfifo failed -- $!\n";
		exit 1;
	}

	if ($channels == 6 && !$opt_2ch) {
		my $channelstr;
		if ($opt_noremix) {
	   		$channelstr = "";
		} else {
	   		$channelstr = "-af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3";
		}
		print "neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in $channelstr -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo\n";

		my $output = `neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in $channelstr -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo`;

		if($?) {
			tprint("mplayer/nero conversion to aac failed: $output\n");
			exit 1;
		}
	} else {
		print "neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo\n";

		my $output = `neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer -vo null -vc null $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo`;

		if($?) {
			tprint("mplayer/nero conversion to aac failed: $output\n");
			exit 1;
		}
	}

	my $strfix = substr($aac,0,rindex($aac,"."));

	print("MP4Box -raw 1 $aac\n");
	system("MP4Box -raw 1 $aac");
	print("mv ${strfix}_track1.aac $aac");
	system("mv ${strfix}_track1.aac $aac");

	# clean up the fifo and the ac3/dts file to save on disk space
	unlink($fifo);
}

##############################################################################
# remux the video and audio tracks in the mp4 format
##############################################################################
sub create_mp4 {
   my ($h264, $aac, $fps, $outf) = @_;

   # size of h264 + aac
   my $total_size = 0;

   # split the file into 3.5 G chunks to avoid problems with
   # PS3 playback of 4G files, this is the size in KB
   my $split_size = 3942400;

   my $split = 0;

   if (! $opt_nosplit) {
	   # find out how big the existing file is. If it's less than
	   # our split size, then don't bother splitting it
	   my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
	      $atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

	   $total_size += $size;

	   ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
	      $atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

	   $total_size += $size;

	   # normalize to KB for comparison
	   $total_size /= 1024;
	   if($total_size > $split_size) {
	      $split = 1;
	   }
   }

   my $split_str = "";
   if($split) {
      $split_str = "-splits $split_size";
   } else {
      $split_str = "";
   }

   my $cmd = "MP4Box $split_str -add $h264 -add $aac -fps $fps -nosys -new \"$outf\" 2>&1";
   print "$cmd\n";

   my $output = `$cmd`;
   if($?) {
      print "MP4Box creation of mp4 failed! output:\n\n$output\n";
      exit 1;
   }
}

##############################################################################
# make sure we have all the tools for the job
##############################################################################
sub check_required_tools {

   my $errors = 0;

   my @required = qw(mkvinfo mkvextract mplayer MP4Box neroAacEnc);
   foreach my $req_prog (@required) {
      my $found = 0;
      foreach my $path_ent (split(/:/, $ENV{PATH})) {
         if(-r "$path_ent/$req_prog") {
            $found = 1;
            last;
         }
      }
      if(! $found) {
         $errors++;
         print "Error, required program: $req_prog not found. Please install it.\n";
      }
   }

   if($errors > 0) {
      exit 1;
   }
}

##############################################################################
# print status messages during remux process
##############################################################################
sub tprint {
   my $msg = shift;

   print $msg;
}

```

---

### Post by cookie__monster on 2008-06-12
thank you for all the help but unfortunately your script is not producing a converted mp4 file.

at this point i am ready to give up.  i believe it will be an easier setup if i just plug in the PC into LCD via HDMI interface.

mplayer plays the mkv files without any lengthy converting.

---

### Post by denisesballs on 2008-06-15
Anyone know why I'm getting this error on this step? The last error just repeats forever and nothing happens.

```
$ neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -ao pcm:fast
[1] 23198
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

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing audio.ac3.
libavformat file format detected.
[mpeg @ 0x8804c54]Could not find codec parameters (Audio: mp2, 256 kb/s)
[mpeg @ 0x8804c54]Could not find codec parameters (Audio: mp2)
[mpeg @ 0x8804c54]Could not find codec parameters (Audio: mp2, 224 kb/s)
LAVF_header: av_find_stream_info() failed
MPEG-PS file format detected.
MPEG: FATAL: EOF while searching for sequence header.
Video: Cannot read properties.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 32000 Hz, 2 ch, s16le, 288.0 kbit/28.12% (ratio: 36000->128000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
[AO PCM] File: audiodump.wav (WAVE)
PCM: Samplerate: 32000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 32000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame) of 11290.1 ( 3:08:10.0) ??,?% 
Cannot sync MAD frame) of 11290.1 ( 3:08:10.0) ??,?% 
Cannot sync MAD frame) of 11290.1 ( 3:08:10.0) ??,?% 
Cannot sync MAD frame) of 11290.1 ( 3:08:10.0) ??,?%
```

---

### Post by tjwallace on 2008-06-15
> **denisesballs said:**
> Anyone know why I'm getting this error on this step? The last error just repeats forever and nothing happens.

```
$ neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer audio.ac3 -vc null -vo null -ao pcm:fast
[1] 23198
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

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing audio.ac3.
libavformat file format detected.
[mpeg @ 0x8804c54]Could not find codec parameters (Audio: mp2, 256 kb/s)
[mpeg @ 0x8804c54]Could not find codec parameters (Audio: mp2)
[mpeg @ 0x8804c54]Could not find codec parameters (Audio: mp2, 224 kb/s)
LAVF_header: av_find_stream_info() failed
MPEG-PS file format detected.
MPEG: FATAL: EOF while searching for sequence header.
Video: Cannot read properties.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 32000 Hz, 2 ch, s16le, 288.0 kbit/28.12% (ratio: 36000->128000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
[AO PCM] File: audiodump.wav (WAVE)
PCM: Samplerate: 32000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 32000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame) of 11290.1 ( 3:08:10.0) ??,?% 
Cannot sync MAD frame) of 11290.1 ( 3:08:10.0) ??,?% 
Cannot sync MAD frame) of 11290.1 ( 3:08:10.0) ??,?% 
Cannot sync MAD frame) of 11290.1 ( 3:08:10.0) ??,?%
```
Instead of inputting the audio.ac3 file to mplayer, input the mkv file, and add these flags:
```

-vo null -vc null -novideo

```

If you were using a script try this one instead:
```

#!/usr/bin/perl
#######################################################################
#
#  File:                 mkv2mp4.pl
#  Edited by:            Jeff Wallace   (jeff AT tjwallace DOT ca)
#  Original Author(s):   Justin Randall (randall311 AT yahoo DOT com)
#                        Josh Carroll   (josh.carroll AT gmail DOT com)
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#  GNU General Public License for more details.
#
#######################################################################
use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);
use File::Basename;

my $prog = $0;
$prog =~ s/.*\///img;

# set the input based off the command arguments
my ($opt_in, $opt_2ch, $opt_nosplit, $opt_noremix);

GetOptions(	'in=s' => \$opt_in,
		'2ch' => \$opt_2ch,
		'nosplit' => \$opt_nosplit,
		'noremix' => \$opt_noremix);

if (!$opt_in) {
   print "Usage: $prog -in <maktrosa input file> [-2ch -nosplit -noremix]\n";
   print "[-2ch]: Re-encode audio to 2 channels\n";
   print "[-nosplit]: Do NOT split the final MP4 file\n";
   print "[-noremix]: Do NOT remix the surround sound channels\n";
   exit 0;
}

my($name, $path, $suffix) = fileparse($opt_in, qr{\..*});

if ($suffix eq '') {
   print "input file did not contain a suffix!\n";
   exit -1;
}

# remove file extension from input file
my $char = 0;
my $basename = $opt_in;
while ($char ne '.') {
   $char = chop $basename;
}

# temoprary files and variables
my $opt_tmp = $basename;
$opt_tmp = "$opt_tmp";
my $opt_out = "$basename.mp4";
my $tmp_h264 = "$name.h264";
my $tmp_wav_fifo = "$name.wav";
my $tmp_aac = "$name.aac";

# make sure we have all the tools
check_required_tools();

# make sure the mkv file is correct format
tprint("Checking input file format...\n");
check_resolution($opt_in);

tprint("Extracting mkv file...\n");
# get the fps of the video and the duration (in seconds) of the MKV, and extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$channels) = extract_mkv($opt_in, $tmp_h264, 0,0);

# modify h264 header to change level_idc to 0x29
tprint("Changing h.264 stream's level_idc header...\n");
change_h264_level($tmp_h264);

tprint("Converting audio to aac...\n");
conv_to_aac($opt_in, $tmp_aac, $channels);

tprint("Creating mp4 file...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $opt_out);

# cleanup and finsh processing
tprint("Cleaning up tmp files...\n");
unlink($tmp_h264,$tmp_wav_fifo,$tmp_aac);
tprint("Done!\n");

##############################################################################
# check the mkv file format
##############################################################################
sub check_resolution {
   my $mkv = shift;

   my $output = `mkvinfo "$mkv" 2>&1`;
   chomp($output);

   my $width = 0;
   if($output =~ /Pixel width:\s+(\d+)/i) {
      $width = $1;
      print "MSG - MkvInfo pixel width - $width \n";
   }
   if($width == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   my $height = 0;
   if($output =~ /Pixel height:\s+(\d+)/i) {
      $height = $1;
      print "MSG - MkvInfo pixel height - $height \n";
   }
   if($height == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   if($height % 16) {
      print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
      print "Consider using ffmpeg/mencoder to crop this video first.\n";
      exit 1;
   }
}

##############################################################################
# extract the video and audio raw tracks from the mkv continer
##############################################################################
sub extract_mkv {
   my ($in, $h264, $dont_extract, $channels) = @_;

   my $fps = -1;
   my $duration = -1;
   my $type = undef;
   my $audio_type = undef;
   my $video_type = undef;

   my ($audio_track_num, $h264_track_num) = (-1, -1);
   my ($found_video, $found_audio) = (0,0);

   my $cur_audio = 0;
   my $cur_video = 0;

   # find out which track is which
   my $curr_track_num = -1;

   my @output = `mkvinfo "$in" 2>&1`;
   chomp(@output);
   foreach my $line (@output) {
      if($found_video && $channels && $found_audio && $fps != -1 && defined $audio_type) {
         last;
      }
      if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
         my $tmp = $1;
         if($type =~ /video/i) {
            $fps = $tmp;
		if($fps == -1) {
		      print "Error, could not determine input MKV fps\n";
		      exit 1;
		   }
            print "MSG - MkvInfo Video - fps: $fps\n";
         }
      } elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
         $duration = $1;
      } elsif($line =~ /Track number:\s+(\d+)/i) {
         $curr_track_num = $1;
         next;
      } elsif($line =~ /Track type:\s+(\S+)/i) {
         if($curr_track_num == -1) {
            # we haven't found the track # yet, but we found the type.
            # this shouldn't happen
            print "Error, mkvinfo failed.\n";
            exit 1;
         }
         $type = $1;
         if($type =~ /audio/i) {
            if(! $found_audio) {
               $audio_track_num = $curr_track_num;
               $found_audio = 1;
               $cur_video = 0;
               $cur_audio = 1;
            }
         } else {
            if(! $found_video) {
               $h264_track_num = $curr_track_num;
               $found_video = 1;
               $cur_video = 1;
               $cur_audio = 0;
            }
         }
      } elsif($found_audio && $cur_audio && $line =~ /Codec ID:\s+(\S+)/i) {
         $audio_type = $1;
         print "MSG - MkvInfo Audio - $audio_type Track: $audio_track_num\n";
      } elsif($found_video && $cur_video && $line =~ /Codec ID:\s+(\S+)/i) {
         $video_type = $1;
         print "MSG - MkvInfo Video - $video_type Track: $h264_track_num\n";
      }

      if ($line =~ /Channels:\s+(\d+)/i) {
         $channels = $1;
         if ($channels == 6) {
            print "MSG - MkvInfo Audio Channels - 6 - (Dolby 5.1 / DTS)\n";
         } else {
            print "MSG - MkvInfo Audio Channels - 2 - (Stereo 2.1)\n";
         }
      }
   }

   if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
      print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
      exit 1;
   }

   my $audio_file;

   if ($audio_type ne "A_DTS" && $audio_type ne "A_AC3") {
      if ($audio_type eq "A_AAC") {
          print "No audio channel remix needed...\n";
          #$opt_noremix = 1;
      } else {
          print "Error: invalid audio type in mkv: $audio_type\n";
          exit 1;
      }
   }

    print "mkvextract tracks \"$in\" $h264_track_num:$tmp_h264\n";

   my $output = `mkvextract tracks "$in" $h264_track_num:$tmp_h264`;

   if($?) {
      print "Error, mkvextract failed! output:\n\n$output\n";
      exit 1;
   }

   return ($fps, $duration, $channels);
}

##############################################################################
# change h264 header level_idc to 0x29
##############################################################################
sub change_h264_level {
   my $file = shift;
   open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
   sysseek($fh, 7, 0);
   syswrite($fh,"\x29",1);
   close($fh);
}

##############################################################################
# convert audio AC3 -> WAV -> AAC
##############################################################################
sub conv_to_aac {
	my ($in, $aac, $channels) = @_;

	my $fifo = $tmp_wav_fifo;
	print "Making fifo: $fifo\n";
	system("mkfifo $fifo");

	if($?) {
		print "mkfifo failed -- $!\n";
		exit 1;
	}

	if ($channels == 6 && !$opt_2ch) {
		my $channelstr;
		if ($opt_noremix) {
	   		$channelstr = "";
		} else {
	   		$channelstr = "-af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3";
		}
		print "neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in $channelstr -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo\n";

		my $output = `neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in $channelstr -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo`;

		if($?) {
			tprint("mplayer/nero conversion to aac failed: $output\n");
			exit 1;
		}
	} else {
		print "neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo\n";

		my $output = `neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer -vo null -vc null $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo`;

		if($?) {
			tprint("mplayer/nero conversion to aac failed: $output\n");
			exit 1;
		}
	}

	my $strfix = substr($aac,0,rindex($aac,"."));

	print("MP4Box -raw 1 $aac\n");
	system("MP4Box -raw 1 $aac");
	print("mv ${strfix}_track1.aac $aac");
	system("mv ${strfix}_track1.aac $aac");

	# clean up the fifo and the ac3/dts file to save on disk space
	unlink($fifo);
}

##############################################################################
# remux the video and audio tracks in the mp4 format
##############################################################################
sub create_mp4 {
   my ($h264, $aac, $fps, $outf) = @_;

   # size of h264 + aac
   my $total_size = 0;

   # split the file into 3.5 G chunks to avoid problems with
   # PS3 playback of 4G files, this is the size in KB
   my $split_size = 3942400;

   my $split = 0;

   if (! $opt_nosplit) {
	   # find out how big the existing file is. If it's less than
	   # our split size, then don't bother splitting it
	   my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
	      $atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

	   $total_size += $size;

	   ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
	      $atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

	   $total_size += $size;

	   # normalize to KB for comparison
	   $total_size /= 1024;
	   if($total_size > $split_size) {
	      $split = 1;
	   }
   }

   my $split_str = "";
   if($split) {
      $split_str = "-splits $split_size";
   } else {
      $split_str = "";
   }

   my $cmd = "MP4Box $split_str -add $h264 -add $aac -fps $fps -nosys -new \"$outf\" 2>&1";
   print "$cmd\n";

   my $output = `$cmd`;
   if($?) {
      print "MP4Box creation of mp4 failed! output:\n\n$output\n";
      exit 1;
   }
}

##############################################################################
# make sure we have all the tools for the job
##############################################################################
sub check_required_tools {

   my $errors = 0;

   my @required = qw(mkvinfo mkvextract mplayer MP4Box neroAacEnc);
   foreach my $req_prog (@required) {
      my $found = 0;
      foreach my $path_ent (split(/:/, $ENV{PATH})) {
         if(-r "$path_ent/$req_prog") {
            $found = 1;
            last;
         }
      }
      if(! $found) {
         $errors++;
         print "Error, required program: $req_prog not found. Please install it.\n";
      }
   }

   if($errors > 0) {
      exit 1;
   }
}

##############################################################################
# print status messages during remux process
##############################################################################
sub tprint {
   my $msg = shift;

   print $msg;
}

```

---

### Post by denisesballs on 2008-06-15
> **tjwallace said:**
> Instead of inputting the audio.ac3 file to mplayer, input the mkv file, and add these flags:
```

-vo null -vc null -novideo

```

If you were using a script try this one instead:
```

#!/usr/bin/perl
#######################################################################
#
#  File:                 mkv2mp4.pl
#  Edited by:            Jeff Wallace   (jeff AT tjwallace DOT ca)
#  Original Author(s):   Justin Randall (randall311 AT yahoo DOT com)
#                        Josh Carroll   (josh.carroll AT gmail DOT com)
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#  GNU General Public License for more details.
#
#######################################################################
use warnings;
use strict;
use Getopt::Long;
use POSIX qw(floor);
use Cwd qw(realpath);
use File::Basename;

my $prog = $0;
$prog =~ s/.*\///img;

# set the input based off the command arguments
my ($opt_in, $opt_2ch, $opt_nosplit, $opt_noremix);

GetOptions(	'in=s' => \$opt_in,
		'2ch' => \$opt_2ch,
		'nosplit' => \$opt_nosplit,
		'noremix' => \$opt_noremix);

if (!$opt_in) {
   print "Usage: $prog -in <maktrosa input file> [-2ch -nosplit -noremix]\n";
   print "[-2ch]: Re-encode audio to 2 channels\n";
   print "[-nosplit]: Do NOT split the final MP4 file\n";
   print "[-noremix]: Do NOT remix the surround sound channels\n";
   exit 0;
}

my($name, $path, $suffix) = fileparse($opt_in, qr{\..*});

if ($suffix eq '') {
   print "input file did not contain a suffix!\n";
   exit -1;
}

# remove file extension from input file
my $char = 0;
my $basename = $opt_in;
while ($char ne '.') {
   $char = chop $basename;
}

# temoprary files and variables
my $opt_tmp = $basename;
$opt_tmp = "$opt_tmp";
my $opt_out = "$basename.mp4";
my $tmp_h264 = "$name.h264";
my $tmp_wav_fifo = "$name.wav";
my $tmp_aac = "$name.aac";

# make sure we have all the tools
check_required_tools();

# make sure the mkv file is correct format
tprint("Checking input file format...\n");
check_resolution($opt_in);

tprint("Extracting mkv file...\n");
# get the fps of the video and the duration (in seconds) of the MKV, and extract the mkv (if only re-muxing to mp4 with aac)
my ($vid_fps,$duration,$channels) = extract_mkv($opt_in, $tmp_h264, 0,0);

# modify h264 header to change level_idc to 0x29
tprint("Changing h.264 stream's level_idc header...\n");
change_h264_level($tmp_h264);

tprint("Converting audio to aac...\n");
conv_to_aac($opt_in, $tmp_aac, $channels);

tprint("Creating mp4 file...\n");
create_mp4($tmp_h264, $tmp_aac, $vid_fps, $opt_out);

# cleanup and finsh processing
tprint("Cleaning up tmp files...\n");
unlink($tmp_h264,$tmp_wav_fifo,$tmp_aac);
tprint("Done!\n");

##############################################################################
# check the mkv file format
##############################################################################
sub check_resolution {
   my $mkv = shift;

   my $output = `mkvinfo "$mkv" 2>&1`;
   chomp($output);

   my $width = 0;
   if($output =~ /Pixel width:\s+(\d+)/i) {
      $width = $1;
      print "MSG - MkvInfo pixel width - $width \n";
   }
   if($width == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   my $height = 0;
   if($output =~ /Pixel height:\s+(\d+)/i) {
      $height = $1;
      print "MSG - MkvInfo pixel height - $height \n";
   }
   if($height == 0) {
      print "Could not determine video width. mkvinfo parsing failed. mkvinfo output:\n\n$output\n";
      exit 1;
   }

   if($height % 16) {
      print "Error, height must be a multiple of 16 for the PS3 to recognize the file.\n";
      print "Consider using ffmpeg/mencoder to crop this video first.\n";
      exit 1;
   }
}

##############################################################################
# extract the video and audio raw tracks from the mkv continer
##############################################################################
sub extract_mkv {
   my ($in, $h264, $dont_extract, $channels) = @_;

   my $fps = -1;
   my $duration = -1;
   my $type = undef;
   my $audio_type = undef;
   my $video_type = undef;

   my ($audio_track_num, $h264_track_num) = (-1, -1);
   my ($found_video, $found_audio) = (0,0);

   my $cur_audio = 0;
   my $cur_video = 0;

   # find out which track is which
   my $curr_track_num = -1;

   my @output = `mkvinfo "$in" 2>&1`;
   chomp(@output);
   foreach my $line (@output) {
      if($found_video && $channels && $found_audio && $fps != -1 && defined $audio_type) {
         last;
      }
      if($line =~ /Default duration.*\((\d+\.\d+)\s*fps/i) {
         my $tmp = $1;
         if($type =~ /video/i) {
            $fps = $tmp;
		if($fps == -1) {
		      print "Error, could not determine input MKV fps\n";
		      exit 1;
		   }
            print "MSG - MkvInfo Video - fps: $fps\n";
         }
      } elsif($line =~ /^\s*\|\s*\+\s*Duration:\s*(\d+\.\d+)\s*s\s+/i) {
         $duration = $1;
      } elsif($line =~ /Track number:\s+(\d+)/i) {
         $curr_track_num = $1;
         next;
      } elsif($line =~ /Track type:\s+(\S+)/i) {
         if($curr_track_num == -1) {
            # we haven't found the track # yet, but we found the type.
            # this shouldn't happen
            print "Error, mkvinfo failed.\n";
            exit 1;
         }
         $type = $1;
         if($type =~ /audio/i) {
            if(! $found_audio) {
               $audio_track_num = $curr_track_num;
               $found_audio = 1;
               $cur_video = 0;
               $cur_audio = 1;
            }
         } else {
            if(! $found_video) {
               $h264_track_num = $curr_track_num;
               $found_video = 1;
               $cur_video = 1;
               $cur_audio = 0;
            }
         }
      } elsif($found_audio && $cur_audio && $line =~ /Codec ID:\s+(\S+)/i) {
         $audio_type = $1;
         print "MSG - MkvInfo Audio - $audio_type Track: $audio_track_num\n";
      } elsif($found_video && $cur_video && $line =~ /Codec ID:\s+(\S+)/i) {
         $video_type = $1;
         print "MSG - MkvInfo Video - $video_type Track: $h264_track_num\n";
      }

      if ($line =~ /Channels:\s+(\d+)/i) {
         $channels = $1;
         if ($channels == 6) {
            print "MSG - MkvInfo Audio Channels - 6 - (Dolby 5.1 / DTS)\n";
         } else {
            print "MSG - MkvInfo Audio Channels - 2 - (Stereo 2.1)\n";
         }
      }
   }

   if($fps == -1 || $duration == -1 || $audio_track_num == -1 || $h264_track_num == -1) {
      print "mkvinfo parsing failed. mkvinfo output:\n\n" . join("\n", @output), "\n";
      exit 1;
   }

   my $audio_file;

   if ($audio_type ne "A_DTS" && $audio_type ne "A_AC3") {
      if ($audio_type eq "A_AAC") {
          print "No audio channel remix needed...\n";
          #$opt_noremix = 1;
      } else {
          print "Error: invalid audio type in mkv: $audio_type\n";
          exit 1;
      }
   }

    print "mkvextract tracks \"$in\" $h264_track_num:$tmp_h264\n";

   my $output = `mkvextract tracks "$in" $h264_track_num:$tmp_h264`;

   if($?) {
      print "Error, mkvextract failed! output:\n\n$output\n";
      exit 1;
   }

   return ($fps, $duration, $channels);
}

##############################################################################
# change h264 header level_idc to 0x29
##############################################################################
sub change_h264_level {
   my $file = shift;
   open my $fh, "+< $file" or die "Cannot open temporary h264 file\n";
   sysseek($fh, 7, 0);
   syswrite($fh,"\x29",1);
   close($fh);
}

##############################################################################
# convert audio AC3 -> WAV -> AAC
##############################################################################
sub conv_to_aac {
	my ($in, $aac, $channels) = @_;

	my $fifo = $tmp_wav_fifo;
	print "Making fifo: $fifo\n";
	system("mkfifo $fifo");

	if($?) {
		print "mkfifo failed -- $!\n";
		exit 1;
	}

	if ($channels == 6 && !$opt_2ch) {
		my $channelstr;
		if ($opt_noremix) {
	   		$channelstr = "";
		} else {
	   		$channelstr = "-af channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3";
		}
		print "neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in $channelstr -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo\n";

		my $output = `neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in $channelstr -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels 6 -novideo`;

		if($?) {
			tprint("mplayer/nero conversion to aac failed: $output\n");
			exit 1;
		}
	} else {
		print "neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer $in -vo null -vc null -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo\n";

		my $output = `neroAacEnc -ignorelength -q 1.0 -if $fifo -of $aac & mplayer -vo null -vc null $in -ao pcm:fast:waveheader:file=$fifo -channels $channels -novideo`;

		if($?) {
			tprint("mplayer/nero conversion to aac failed: $output\n");
			exit 1;
		}
	}

	my $strfix = substr($aac,0,rindex($aac,"."));

	print("MP4Box -raw 1 $aac\n");
	system("MP4Box -raw 1 $aac");
	print("mv ${strfix}_track1.aac $aac");
	system("mv ${strfix}_track1.aac $aac");

	# clean up the fifo and the ac3/dts file to save on disk space
	unlink($fifo);
}

##############################################################################
# remux the video and audio tracks in the mp4 format
##############################################################################
sub create_mp4 {
   my ($h264, $aac, $fps, $outf) = @_;

   # size of h264 + aac
   my $total_size = 0;

   # split the file into 3.5 G chunks to avoid problems with
   # PS3 playback of 4G files, this is the size in KB
   my $split_size = 3942400;

   my $split = 0;

   if (! $opt_nosplit) {
	   # find out how big the existing file is. If it's less than
	   # our split size, then don't bother splitting it
	   my ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
	      $atime,$mtime,$ctime,$blksize,$blocks) = stat($h264);

	   $total_size += $size;

	   ($dev,$ino,$mode,$nlink,$uid,$gid,$rdev,$size,
	      $atime,$mtime,$ctime,$blksize,$blocks) = stat($aac);

	   $total_size += $size;

	   # normalize to KB for comparison
	   $total_size /= 1024;
	   if($total_size > $split_size) {
	      $split = 1;
	   }
   }

   my $split_str = "";
   if($split) {
      $split_str = "-splits $split_size";
   } else {
      $split_str = "";
   }

   my $cmd = "MP4Box $split_str -add $h264 -add $aac -fps $fps -nosys -new \"$outf\" 2>&1";
   print "$cmd\n";

   my $output = `$cmd`;
   if($?) {
      print "MP4Box creation of mp4 failed! output:\n\n$output\n";
      exit 1;
   }
}

##############################################################################
# make sure we have all the tools for the job
##############################################################################
sub check_required_tools {

   my $errors = 0;

   my @required = qw(mkvinfo mkvextract mplayer MP4Box neroAacEnc);
   foreach my $req_prog (@required) {
      my $found = 0;
      foreach my $path_ent (split(/:/, $ENV{PATH})) {
         if(-r "$path_ent/$req_prog") {
            $found = 1;
            last;
         }
      }
      if(! $found) {
         $errors++;
         print "Error, required program: $req_prog not found. Please install it.\n";
      }
   }

   if($errors > 0) {
      exit 1;
   }
}

##############################################################################
# print status messages during remux process
##############################################################################
sub tprint {
   my $msg = shift;

   print $msg;
}

```

Using the script you gave doesn't work either, I get:

```
mkv2mp4 1920-cloverfield.mkv 
Checking input file format...
MSG - MkvInfo pixel width - 1920 
MSG - MkvInfo pixel height - 1080 
Error, height must be a multiple of 16 for the PS3 to recognize the file.
Consider using ffmpeg/mencoder to crop this video first.
```

---

### Post by jhiza on 2008-06-17
Not sure if this is the place or not, but:

I have had luck changing the wrappers from mkv->mp4 (more luck with the shell script than the perl one, thanks).  However, the PS3 appears to be picky as HELL about resolution.  

For example the following resolution plays:
1280x720

These do NOT (I can hear sound, but no video):
1920x1080
1920x820
1280x528

If it was an aspect ratio issue, the 1920x1080 should have worked?  Anyone have more insight as to the role that resolution plays with the PS3 actually displaying a picture instead of a black screen???

---

### Post by crocowhile on 2008-06-22
The perl script works very nicely for me.
Only one question: is the conversion from AC3 to AAC needed with the new firmware (2.3x) too?

---

### Post by tjwallace on 2008-06-22
> **crocowhile said:**
> The perl script works very nicely for me.
Only one question: is the conversion from AC3 to AAC needed with the new firmware (2.3x) too?
Hmm, I haven't tried leaving the audio along but I'll give it a try when I get some time and post the results.

---

### Post by tjwallace on 2008-06-22
> **crocowhile said:**
> The perl script works very nicely for me.
Only one question: is the conversion from AC3 to AAC needed with the new firmware (2.3x) too?
I just looked at this, [http://en.wikipedia.org/wiki/MP4#Data_streams](http://en.wikipedia.org/wiki/MP4#Data_streams), and it doesn't look like MP4 can take AC3 streams.  I'll give it a try anyways.

---

### Post by Yaka on 2008-06-28
not sure if this is anyhelp tou guys but i use a app on windows based pc called MVK2VOB can be found [http://forum.doom9.org/showthread.php?t=131782](http://forum.doom9.org/showthread.php?t=131782)
it should be usable via wine

---

### Post by crocowhile on 2008-07-01
> **tjwallace said:**
> I just looked at this, [http://en.wikipedia.org/wiki/MP4#Data_streams](http://en.wikipedia.org/wiki/MP4#Data_streams), and it doesn't look like MP4 can take AC3 streams.  I'll give it a try anyways.
Any luck?

---

### Post by Yaka on 2008-07-12
sorry to sound like a n00b but how are you meant to isntall neroAacEnc ?

---

### Post by crocowhile on 2008-07-12
> **Yaka said:**
> sorry to sound like a n00b but how are you meant to isntall neroAacEnc ?

just download it and copy the two files somewhere covered by PATH (e.g.: /usr/bin )

---

### Post by Yaka on 2008-07-12
i am preet n00bish in ubuntu, when i drag the file in there it says permission denieid when i try thru command line it says same thing

---

### Post by goldenfri on 2008-07-12
sudo cp neroAacEnc /usr/local/bin/

> **Yaka said:**
> i am preet n00bish in ubuntu, when i drag the file in there it says permission denieid when i try thru command line it says same thing

---

### Post by goldenfri on 2008-07-14
Having trouble running the scripts on a few files their mkvinfo seems to be in a diff order. Here is the info:

+ EBML head
|+ EBML version: 1
|+ EBML read version: 1
|+ EBML maximum ID length: 4
|+ (Unknown element: EBMLMaxSizeLength; ID: 0x42f3 size: 4)
|+ Doc type version: 1
|+ Doc type read version: 1
|+ Doc type: matroska
+ Segment, size 576509196
|+ Seek head (subentries will be skipped)
|+ Segment tracks
| + A track
|  + Video track
|   + Pixel crop right: 0
|   + Pixel crop top: 0
|   + Pixel crop bottom: 0
|   + Pixel height: 720
|   + Pixel width: 1280
|   + Pixel crop left: 0
|   + Display width: 16
|   + Display height: 9
|  + Timecode scale: 1.000000
|  + Language: eng
|  + CodecPrivate, length 38
|  + Codec ID: V_MPEG4/ISO/AVC
|  + MaxCache: 0
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Track type: video
|  + Lacing flag: 0
|  + Default flag: 1
|  + Track number: 1
|  + Track UID: 3834084758
|  + MinCache: 1
| + A track
|  + Codec ID: A_AC3
|  + Lacing flag: 1
|  + Default flag: 0
|  + Track number: 2
|  + Track UID: 1661539830
|  + Track type: audio
|  + Default duration: 32.000ms (31.250 fps for a video track)
|  + MinCache: 1
|  + MaxCache: 1
|  + Name: entro.audio
|  + Timecode scale: 1.000000
|  + Audio track
|   + Sampling frequency: 48000.000000
|   + Channels: 5
| + EbmlVoid (size: 206)
|+ Segment information
| + Timecode scale: 500000
| + Muxing application: matroska muxer by Alexander Noe, build date May 25 2006
| + Writing application: VirtualDub
| + Duration: 1559.488s (00:25:59.488000000)
| + Segment UID: 0x6d 0xfd 0xf5 0xa3 0x41 0xd7 0x59 0x89 0x4d 0xfb 0xd1 0x25 0x1b 0x4b 0xbd 0x73
|+ Tags
| + Tag
| + Tag
|+ Cues (subentries will be skipped)
|+ EbmlVoid (size: 500)
|+ Cluster

It is possible to fix one of the scripts to work with this file?

Thanks!

EDIT I had to load it up in mkvmerge and remux it and that allowed it to run, but it would be nice to not have to do that :)

---

### Post by FarmCretin on 2008-07-17
heres my issue: whenever i try to run the script "perl mkv2mp4" im getting a wealth of cryptic errors. the errors i get are....drum-roll.....

```

ben@ubuntu:~/stay$ perl mkv2mp4
"my" variable $opt_in masks earlier declaration in same scope at mkv2mp4 line 78.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 78.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 82.
"my" variable $opt_in masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $channels masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $vid_fps masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $opt_out masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $tmp_wav_fifo masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $output masks earlier declaration in same scope at mkv2mp4 line 292.
syntax error at mkv2mp4 line 78, near "aac)
"
Execution of mkv2mp4 aborted due to compilation errors.

```

---

### Post by tjwallace on 2008-07-17
> **FarmCretin said:**
> heres my issue: whenever i try to run the script "perl mkv2mp4" im getting a wealth of cryptic errors. the errors i get are....drum-roll.....

```

ben@ubuntu:~/stay$ perl mkv2mp4
"my" variable $opt_in masks earlier declaration in same scope at mkv2mp4 line 78.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 78.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 82.
"my" variable $opt_in masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $channels masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $vid_fps masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $opt_out masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $tmp_wav_fifo masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $output masks earlier declaration in same scope at mkv2mp4 line 292.
syntax error at mkv2mp4 line 78, near "aac)
"
Execution of mkv2mp4 aborted due to compilation errors.

```
you need to isntall neroAacEnc

---

### Post by FarmCretin on 2008-07-17
i have it "installed". or at least i think i do. i have it in the same directory as the script. it has full 777 rights. i might be missing something here....
thanks for the quick reply though

---

### Post by tjwallace on 2008-07-17
> **FarmCretin said:**
> i have it "installed". or at least i think i do. i have it in the same directory as the script. it has full 777 rights. i might be missing something here....
thanks for the quick reply though
you need to move it to /usr/bin

---

### Post by FarmCretin on 2008-07-17
> **tjwallace said:**
> you need to move it to /usr/bin

ok, it is now in /usr/bin, again with full 777 rights.
```

ben@ubuntu:~/stay$ perl mkv2mp4
"my" variable $opt_in masks earlier declaration in same scope at mkv2mp4 line 78.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 78.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 82.
"my" variable $opt_in masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $channels masks earlier declaration in same scope at mkv2mp4 line 85.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $vid_fps masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $opt_out masks earlier declaration in same scope at mkv2mp4 line 88.
"my" variable $tmp_h264 masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $tmp_wav_fifo masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $tmp_aac masks earlier declaration in same scope at mkv2mp4 line 92.
"my" variable $output masks earlier declaration in same scope at mkv2mp4 line 292.
syntax error at mkv2mp4 line 78, near "aac)
"
Execution of mkv2mp4 aborted due to compilation errors.

```

---

### Post by FarmCretin on 2008-07-19
nevermind, its all working perfectly. nothing a clean install couldnt cure ;].

---

