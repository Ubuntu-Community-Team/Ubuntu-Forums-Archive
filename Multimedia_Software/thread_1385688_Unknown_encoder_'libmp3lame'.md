---
title: "Unknown encoder 'libmp3lame'"
date: 2010-01-19
forum: Multimedia Software
---

### Post by cowboy7305 on 2010-01-19
Iam  trying to use winff to convert a FLv file to AVI 
but i get this error message "Unknown encoder 'libmp3lame'"i know this is on my machine i looked 
so what file should WIn ff be looking for any help please

---

### Post by FreezWay on 2010-01-19
try sudo-apt get install <name>

it might be a very similar package and it doesn't hurt to check

---

### Post by andrew.46 on 2010-01-20
Hi cowboy,

> **cowboy7305 said:**
>  i get this error message "Unknown encoder 'libmp3lame'

It could be that your copy of FFmpeg has not been compiled to allow mp3 encoding. Usually a simple solution can be found here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
<snip>

All the best,

Andrew

---

### Post by cowboy7305 on 2010-01-20
Many thanks that looks like it did the trick

---

### Post by johanesbrain on 2010-11-13
for me solve by:

sudo apt-get install ffmpeg libavcodec-extra-52

---

### Post by newbuntuxx on 2010-11-29
> **johanesbrain said:**
> for me solve by:

sudo apt-get install ffmpeg libavcodec-extra-52

I was trying to convert an mp4 video to avi and I was getting that error. The above solution worked just fine!

Thanks,

---

### Post by stobio on 2011-04-19
great advice, many thanks!

---

### Post by mike_crossgreen on 2011-04-24
Yeah that one's fantastic! Tried the first but unfortunately it all went wrong half way through.. Second solution worked great though, thanks very much!

---

### Post by fiklein on 2011-05-25
Thanks,
It worked great on Maverick. I have a newbie friend who just installed Natty. Does it work on Natty as well?

---

### Post by aspora.isernia on 2011-05-27
> **fiklein said:**
> Thanks,
It worked great on Maverick. I have a newbie friend who just installed Natty. Does it work on Natty as well?

I can confirm: in Natty it works as well.

---

### Post by MattiGee on 2011-07-03
> **johanesbrain said:**
> for me solve by:

sudo apt-get install ffmpeg libavcodec-extra-52

Reinstall of the codec manually using this solution did the trick! Thanks - you are a lifesaver! 

Matt

---

### Post by Dafydd on 2011-08-25
Thanks. This worked for me too in (L)Ubuntu 11.04

---

### Post by alfredoul on 2012-01-02
sudo apt-get install ffmpeg libavcodec-extra* 

for Ubuntu 11.10

---

### Post by xbartolo on 2012-05-15
great solution. It worked perfectly on the first try!

---

### Post by Robirt55 on 2012-05-22
Sweet thanks this was very helpful and worked well!

using 10.10

---

### Post by moresun on 2012-06-26
> **alfredoul said:**
> sudo apt-get install ffmpeg libavcodec-extra* 

Worked also for 12.04
Just a hint

This works gread to encode Samsung Galaxy S2 videos
```
ffmpeg -i video-2012-06-23-23-14-13.mp4  -vcodec mpeg4 -vtag XVID -b 1200k -acodec libmp3lame -ab 128k output.avi
```

LG
Max

---

### Post by isa.dsouza on 2012-09-23
I am unable to check that link. But got the app "winff" working since page 2 was informative on what needs to be installed.

I am including a screenshot of the error.

---

### Post by FakeOutdoorsman on 2012-09-24
> **isa.dsouza said:**
> I am unable to check that link. But got the app "winff" working since page 2 was informative on what needs to be installed.

I am including a screenshot of the error.

Ubuntu no longer uses FFmpeg, and the forum policy changed which required me to gain permission from a moderator every time I wanted to update my own post. These changes were unacceptable to me, so I deleted it to prevent it from rotting and becoming outdated or wrong. The guide basically said to install the **libavcodec-extra-5*** package to enable additional encoders, or the same named package from Medibuntu if you need ffmpeg to support the AAC encoder named libfaac.

---

### Post by tarahmarie on 2012-10-13
For Precise, install libavcodec-extra-53; looks like an update to the package, but this fix works perfectly.

---

### Post by egatuz on 2012-10-22
GREAT !!!! :popcorn: :P

yeah, libavcodec-extra-52 .... :guitar:

you save me ...

---

### Post by cybrsaylr on 2012-10-22
> **tarahmarie said:**
> For Precise, install libavcodec-extra-53; looks like an update to the package, but this fix works perfectly.

Tried doing that. 
Then ran ffmpeg and it didn't work for me.
I got this output in terminal:

> rr@rr-Studio-XPS-8000:~$ ffmpeg -loop_input -i ~/Desktop/1.jpg -i ~/Desktop/E.mp3 -shortest -b 1000k -acodec copy video.mp4
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
-loop_input is deprecated, use -loop 1
Input #0, image2, from '/home/rr/Desktop/1.jpg':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj422p, 2048x1536, 25 tbr, 25 tbn, 25 tbc
-loop_input is deprecated, use -loop 1
[mp3 @ 0x2529660] max_analyze_duration reached
Input #1, mp3, from '/home/rr/Desktop/E.mp3':
  Metadata:
    artist          : Eliane Elias
    album           : Yule Struttin' - A Blue Note Christmas
    genre           : Jazz
    track           : 4
    title           : I'll Be Home For Christmas / Sleigh Ride
    date            : 1990
  Duration: 00:04:57.06, start: 0.000000, bitrate: 185 kb/s
    Stream #1.0: Audio: mp3, 44100 Hz, stereo, s16, 185 kb/s
File 'video.mp4' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'yuvj422p' for codec 'mpeg4', auto-selecting format 'yuv420p'
[buffer @ 0x2537100] w:2048 h:1536 pixfmt:yuvj422p
[avsink @ 0x2551d20] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x2557a40] w:2048 h:1536 fmt:yuvj422p -> w:2048 h:1536 fmt:yuv420p flags:0x4
Output #0, mp4, to 'video.mp4':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: mpeg4, yuv420p, 2048x1536, q=2-31, 1000 kb/s, 25 tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, 185 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Press ctrl-c to stop encoding
frame=    1 fps=  0 q=9.4 Lsize=     176kB time=0.04 bitrate=35969.6kbits/s    
video:174kB audio:0kB global headers:0kB muxing overhead 0.685802%
rr@rr-Studio-XPS-8000:~$

What went wrong?

---

### Post by 4rt3k on 2012-12-25
Have you tried in other files? I suppose that something is wrong with object. You should also check winff (your life will be simplier ;>).

---

### Post by cab11 on 2012-12-31
Tks man! You save me! :)

---

### Post by malspa on 2013-10-15
> **tarahmarie said:**
> For Precise, install libavcodec-extra-53; looks like an update to the package, but this fix works perfectly.
Thanks for this. In Ubuntu 12.04 (Precise), I used Synaptic to install libavcodec-extra-53. The terminal output looked kinda scary, so I made a note of what was installed and removed, but then everything worked fine. From my /var/log/apt/history.log:

```
Start-Date: 2013-10-14  21:53:47
Commandline: /usr/sbin/synaptic
Install: libopenjpeg2:i386 (1.3+dfsg-4+squeeze1build0.12.04.1, automatic), libavcodec-extra-53:i386 (0.8.6ubuntu0.12.04.1), libavutil-extra-51:i386 (0.8.6ubuntu0.12.04.1, automatic)
Remove: libavutil51:i386 (0.8.6-0ubuntu0.12.04.1), libavcodec53:i386 (0.8.6-0ubuntu0.12.04.1)
End-Date: 2013-10-14  21:54:08
```

This post is probably gonna get nailed for necromancy, but I thought that Precise users who find this thread might appreciate seeing what got removed on my system.

---

### Post by rziman on 2013-10-19
Just a quick note to anyone else with this issue (for me, it came up at some point when trying to use youtube-dl --extract-audio --audio-format=mp3): the tip about libavcodec-extra-53 didn't seem to work for me (see also ubuntu-restricted-extras) apparently since packages.medibuntu.org, from which libavcodec-extra-53 gets downloaded, is no longer maintained. (I am using Linux Mint 13 at the moment but don't see how this would make a difference)

I can't see what's in the thread mentioned in post #3 of this thread since I have less than 10 posts, but ultimately what worked was, as mentioned in that post, to build ffmpeg from source with libmp3lame enabled following the guide at [https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) (and after building it, remember to logout/login (or run ~/.profile in your terminal, as in the guide) to be sure that you're actually using it).

Also, if you're confused about avconv and ffmpeg, be sure to read this: [http://stackoverflow.com/questions/9477115/who-can-tell-me-the-difference-and-relation-between-ffmpeg-libav-and-avconv/9477756#9477756](http://stackoverflow.com/questions/9477115/who-can-tell-me-the-difference-and-relation-between-ffmpeg-libav-and-avconv/9477756#9477756) -- as well as the final link mentioned in that answer: [http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)

---

