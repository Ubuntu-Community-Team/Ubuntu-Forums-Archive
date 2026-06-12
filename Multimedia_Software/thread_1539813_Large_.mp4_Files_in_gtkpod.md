---
title: "Large *.mp4 Files in gtkpod"
date: 2010-07-27
forum: Multimedia Software
---

### Post by Deersindal on 2010-07-27
Hi, guys.

I'm fairly new to Ubuntu, but I've been able to resolve most of my problems with a little searching and this site has been invaluable to me. Finally, however, I have come across something that nobody else seems to have asked.

Currently, I am dual booting XP and Ubuntu 10.04, but in the future I will be getting a new machine and I will only be running Ubuntu and won't have access to iTunes. Because I have an iPod Touch, I have been trying to find workarounds for syncing everything that iTunes took care of in the past. One problem I have is managing movies.


I have looked through various media players/iPod management tools (Amarok, Rhythmbox, gtkpod) and I am using Rhythmbox to sync my music and and attempting to use gtkpod to sync my movies.

gtkpod is able to sync songs (Tested with a few minute test clip) and short *.mp4 files (15mb I know for sure from test).

I am unable, however, to get it to sync a movie (~700mb)


I *am* able to drag it onto my iPod in gtkpod, but when I try to save the changes and write the files, it hangs at "Copying Tracks" at 0%. It eventually crashes during the couple times I have tried to wait it out.

So this being my situation, my question is, is there a size limit to the *.mp4 files I can sync to my iPod Touch via gtkpod? Also appreciated, is there any other tools that you know of that I can sync videos to my iPod with?



Thanks for the help, guys. I know that iPhone support isn't the best in Ubuntu, but you seem to be very helpful to everyone else I've seen here. :)

---

### Post by Deersindal on 2010-07-27
If it is relevant to any suggested program, I *do* have my iPod Touch jailbroken. Also fairly important is it's model.

[B]Second Generation
16 GB
Non-MC Model
Can SSH into filesystem[/B]

If worse comes to worst, I can SSH the movies into the /var/moble/Library/Downloads folder of my iPod and use dTunes to play them, but dTunes's movie player isn't as good as the default one (resume where you left off, thumbnails, etc.)

EDIT:

Took a picture of the difference between two files. One syncs fine and plays, the other does not sync at all.

[IMG]http://i302.photobucket.com/download-albums/nn92/deersindal/Screenshot.png[/IMG]

---

### Post by Deersindal on 2010-07-27
Looking at these files, I thought that it might be possible that the DVD ripper I used to get the nonfunctional movies might be causing the problems. I am ripping a movie with OGMRip to see how that might help things.


EDIT: OGMRip wasn't working. it kept freezing while "extracting audio track 1." I am trying with k9copy and it's slow, but I would have to return to my original question and ask if anyone else can sync ripped dvds to their ipods/iphones via gtkpod?

---

### Post by Deersindal on 2010-07-28
Tonight I will try to rip a DVD with handbrake and see if that makes any difference.

---

### Post by d3v1150m471c on 2010-07-28
gtkpod is what I use and it works perfect for both movies and music. iPod videos can't just be any video shoved in an .mp4 container. Depending on the video encoding and the iPod version they require specific audio and video bitrates to actually go onto the iPod. Try converting the videos properly with a tool like Ibulk, listed on my signature, or another tool like arista transcoder, mp4ize, ect.

---

### Post by Deersindal on 2010-07-28
I was thinking that it might be a problem like that. I converted them on XP with Magic DVD on iPhone settings which usually works, but I had been running them through iTunes which might have done something to them. I will try Ibulk and let you know how it works out.

---

### Post by Deersindal on 2010-07-28
Alright I'm back. I downloaded and installed Ibulk as per the included instructions and I ran ```
sudo ibulk -H -P
``` which returned ```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'fullmetaljacket.mp4':
  Duration: 01:56:31.01, start: 0.000000, bitrate: 871 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 424x320 [PAR 1:1 DAR 53:40], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'libx264'
find: `/home/jonathan/Ibulk/output/*': No such file or directory
find: `/home/jonathan/Ibulk/output/*': No such file or directory
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
*: no such file or directory
find: `/home/jonathan/Ibulk/output/*': No such file or directory

Ibulk has finished. Enjoy your new videos. Please
remove all files from ~/Ibulk/input & output folders

find: `/home/jonathan/Ibulk/output/*': No such file or directory
``` along with no converted file.

---

### Post by d3v1150m471c on 2010-07-28
right, in the Read Me it will tell you, that you have to first run ibulk as:
```

ibulk -r

```This will create the directories ibulk will use to convert the videos. use:
```

ibulk -h

```for more info.

after you use "ibulk -r", you can either convert several videos by placing them in ~/Ibulk/input and then running the code you attempted earlier or to convert a single video, set the -S flag.

---

### Post by Deersindal on 2010-07-28
I did run ```
ibulk -r
``` and i do have the directories ```
~/Ibulk/input
~/Ibulk/output
``` both of these directories are only accessible by root, though, hence why i ran ```
sudo ibulk -H -P
``` instead of ```
ibulk -H -P
```

---

### Post by d3v1150m471c on 2010-07-28
```

[FONT=monospace]Unknown encoder 'libx264'
[/FONT]
```[FONT=monospace]

That's the problem. Ibulk cannot find any videos in output because ffmpeg doesn't have the H.264 library, thus it never actually made any videos. You'll need to install that. Sorry I didn't notice that earlier. I'll have to update the dependencies on ibulk so I'm glad you caught that.

```

sudo apt-get install libx264-67

```

that should solve the problem.
[/FONT]

---

### Post by Deersindal on 2010-07-28
Yes, I put one *.mp4 that wasn't working in the input file and yes, it is strange, but all of ~/Ibulk is root only and I've been needing to use terminal with sudo to copy files to it.

---

### Post by d3v1150m471c on 2010-07-28
this will also help. [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by d3v1150m471c on 2010-07-28
you could just right click Ibulk and change its permissions to have read and write permissions by non-root user and then check the box for it to set the same for all "enclosed files and folders". that should fix the problem. it would seem I have some bugs to work out.

---

### Post by Deersindal on 2010-07-28
I think I tried that but I needed root permission to change permission settings. I will try that when I get back to my computer again (I am posting from my iPod right now.) thanks again for the help. Hopefully I will have my iPod working great on ubuntu soon :D

---

### Post by d3v1150m471c on 2010-07-28
hey, thank you actually. I've been working on ibulk for some time now and it's good to have someone actually give me some feedback. It's impossible to work out all the bugs when I only have my platform to test it on.

---

### Post by Deersindal on 2010-07-28
No problem, I'm just glad I'm getting somewhere. I am back on my computer and I have adjusted the permissions on ~/Ibulk and have tried to run it again, but it has the same error. One thing I did notice is that ```
/usr/bin/ibulk
``` needs sudo to run it. Now, because the tutorial never mentions running ```
*sudo* ibulk
``` I think that this might be contributing to the problem, but I'm not entirely sure. I will try re-installing from the original you gave me and try again.

On a side note, how would I be able to run a command through terminal and shut down after the command is finished running? On windows I could do something like ```
start /wait ipconfig/renew
shutdown -s -t 30 
``` which would renew ip configuration and then shutdown in 30 seconds. I'm asking because if, after all, this is just a problem with my DVD ripping program, I will still need to rip DVDs (probably using handbrake via the terminal) and I would like my system to be able to shutdown after it is done ripping.

---

### Post by Deersindal on 2010-07-29
Okay I think I found out why /usr/bin/ibulk and ~/Ibulk were both root only. The fourth instruction of the readme, ```
sudo cp ibulk /usr/bin/ibulk
``` causes ibulk to be copied to /usr/bin as a file that needs sudo. When you run the fifth instruction ```
ibulk -r
``` you also create everything in ~/Ibulk as needing root as well. I modified /usr/bin/ibulk to be able to be run without sudo before I followed the fifth instruction, so I will see how it goes this time.

---

### Post by Deersindal on 2010-07-29
Okay, I realize that I am triple posting, but I *finally* found out what I was doing wrong. It turns out that I had the crippled version of ffmpeg and libx264. I followed the medibuntu instructions on this page 

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283) 

and all is well on ibulk. I suggest that you mention that you can't use the generic ones from synaptic and that you need to use the ones from this guide. So far so good on ibulk :D

EDIT:

*Facepalm*

> this will also help. [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)Yea, that might have saved me some time. Guess I just glanced over it though. Oh well, no harm done ;)

---

### Post by d3v1150m471c on 2010-07-29
lol i'm glad to see things finally worked out.

---

### Post by Deersindal on 2010-07-29
Ehhh more or less. I'm one step closer to seeing if it was the DVD ripper on windows that was causing the problem, but I don't have a file that I know for sure will work straight to my iPod. After I ran ibulk for ~10 minutes I get this...```
frame=208446 fps=199 q=4.1 Lsize=  237418kB time=6989.55 bitrate= 278.3kbits/s    
video:170954kB audio:54616kB global headers:0kB muxing overhead 5.252180%
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 29999.00 (29999/1) -> 29.97 (30000/1001)
Input #0, avi, from 'fullmetaljacket.avi':
  Duration: 01:56:30.91, start: 0.000000, bitrate: 278 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 424x320 [PAR 1:1 DAR 53:40], 29.97 tbr, 29.97 tbn, 29999 tbc
    Stream #0.1: Audio: mp2, 48000 Hz, stereo, s16, 64 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, mov, to '/home/jonathan/Ibulk/output/fullmetaljacket.mp4':
    Stream #0.0: Video: libx264, yuv420p, 480x380 [PAR 150:143 DAR 3600:2717], q=3-5, 0 kb/s, 90k tbn, 30 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, s16, 160 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x9c6bb70]broken ffmpeg default settings detected
[libx264 @ 0x9c6bb70]use an encoding preset (vpre)
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 29999.00 (29999/1) -> 29.97 (30000/1001)
Input #0, avi, from '/home/jonathan/Ibulk/.middle/fullmetaljacket.avi':
  Duration: 01:56:30.91, start: 0.000000, bitrate: 278 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 424x320 [PAR 1:1 DAR 53:40], 29.97 tbr, 29.97 tbn, 29999 tbc
    Stream #0.1: Audio: mp2, 48000 Hz, stereo, s16, 64 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, mov, to '/home/jonathan/Ibulk/output/fullmetaljacket.mp4':
    Stream #0.0: Video: libx264, yuv420p, 480x380 [PAR 150:143 DAR 3600:2717], q=3-5, 0 kb/s, 90k tbn, 30 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, s16, 160 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x8b87b90]broken ffmpeg default settings detected
[libx264 @ 0x8b87b90]use an encoding preset (vpre)
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

Ibulk has finished. Enjoy your new videos. Please
remove all files from ~/Ibulk/input & output folders

Sorry jonathan...fullmetaljacket couldn't be converted
jonathan@Computer:~$
```And I also think I might try Amarok instead of Rhythmbox. I spent a couple hours adding album art to ~700 songs ID3 tags only to find that didn't give me artwork on my ipod. :(

EDIT: If you could suggest to me a good DVD ripper, I might have better success than trying to fix files that don't work.

---

### Post by Deersindal on 2010-07-29
I think that something might be wrong with my gtkpod installation... How would I go about a complete removal and reinstall of gtkpod along with all the other packages I would need to get it to work correctly?

---

### Post by d3v1150m471c on 2010-07-29
I'm wondering what version of ffmpeg you have. Mine's 4:0.5+svn20090706-2ubuntu2.2. I would suggest upgrading ffmpeg if it needs it or trying arista-transcoder. I'm fairly certain handbrake and mp4ize run off ffmpeg as well and arista is rather slow with few options. I don't think it's a gtkpod error.

**[COLOR=DarkRed]update:[/COLOR]**
```

sudo apt-get update
sudo apt-get upgrade ffmpeg

```

That could fix the problem.

---

### Post by d3v1150m471c on 2010-07-30
BTW I uploaded ibulk_1_9_5 to sourceforge and your bitrate warning shouldn't be a problem with the new version. Older versions of FFmpeg cannot accept bitrate arguments written as kilobits, however the new versions will accept both kilobits and bits, so I've patched it by making it a bps argument. Even without upgrading ffmpeg the new version should work for you now. I hope you get everything working soon and good luck to you.

---

### Post by Deersindal on 2010-07-30
Thanks for your help so far and I'm glad I was able to help ibulk development :) I am trying a clean install right now with a (coincidentally) clean iPod. I might have installed gtkpod in a way that it didn't work out right, so I will keep you posted on how it goes... It sounds like everybody else I've heard of hasn't had problems with gtkpod so I would have to assume that I'm the one at fault ;)


UPDATE: The clean install has resolved problems with music and album art syncing that were big problems. I might try gtkpod again later, but for the time being, I am just glad to be able to sync my music correctly. In the future, I will use handbrake to rip my DVDs (which I don't do that much; I just got these movies for a road trip) All in all, most things are working great in ubuntu and for things that aren't, there are pretty easy workarounds for. Thanks again for all the help :D

---

