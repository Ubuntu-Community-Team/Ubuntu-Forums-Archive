---
title: "Ripping My DVDs: So close, yet so far"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by jabster on 2007-12-06
Hi.

I am trying to rip all of my DVDs to my hard drive, and am having a problem with a high quality rip/encode.

I am currently using dvdrip to rip the dvd tracks to my hard drive, giving me all the VOB files. I am then trying to tanscode into an AVI/ffmpeg/h264, which appears to give me me a nice high quality video.

I am also setting BPP to 1.00, Audio bitrate to 384, 0 (best but slowest) audio qualilty, and no deinterlacing.

However, I am having a problem with the transcode process. Please see the attached pictures, but basically, some frames/sections of the video are a lighter shade of grey instead of the color they are supposed to be.

First, my transcode command. I am running this manually, as running it within dvdrip ends up giving me a 27k file. I am pasting this into a konsole, copied from the dvdrip log. All I removed from the command that dvdrip uses are the mkdir commands and the execcode portion. I'm running it from within the vob directory:
```
transcode -H 10 -a 0 -x vob -i . -w 8286,50 -F h264 -b 256,0,0 -s 1.233 --a52_drc_off -f 24,1 -M 2 -y ffmpeg --psu_mode --nav_seek /media/extra/dvdrip_data_dir/serenity/tmp/serenity-001-nav.log --no_split  -o /media/extra/dvdrip_data_dir/serenity/avi/001/serenity.h264-001.avi --print_status 25  
```

Here's the error messages I am getting:
```
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4383
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4383
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4413TA: 1:37:34, ( 0| 0| 9)
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4423TA: 1:34:06, ( 0| 0| 9)
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4423
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389TA: 1:29:07, ( 0| 0| 9)
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389TA: 1:22:48, ( 0| 0| 9)
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389TA: 1:18:07, ( 0| 0| 9)
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389TA: 1:15:05, ( 0| 0| 9)
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389
[h264 @ 0xb55df3a8]OVERFLOW levelcode=4389TA: 1:12:26, ( 0| 0| 9)
```
And it keeps going.

So:
1) Can someone tell me what's going on and how to fix it?
2) Is there a better way of ripping my DVDs?

What I'm looking for:
I want DVD rips that give me the 6-channel audio, and give me image quality equal (or darned near) the DVD quality itself. ie: I don't want to be able to distinguish between the physical DVD and the AVI. At some point I will want subtitles (I have a handful of Indian movies), but right now I don't care about them.

I was trying xvid5, but I ended up with some nasty effects (don't know what you'd call it). It's most noticable in the first scene of serenity, as you zoom in towards Earth That Was: the outer edge of earth doesn't remain smooth and round. The h264, where it works, seems to give me the qualilty that I'm looking for, but I keep getting effects like in serenity02.png.

Screenshot index:
serenity01: Universal logo, with correct colors
serenity02: Universal logo, more gray and bad
serenity03: Nice rounded Earth That Was

Thanks in advance.
-john

---

### Post by Rhubarb on 2007-12-06
I don't have that much knowledge with transcode.
Perhaps mencoder would be better suited to the job?
```
mencoder input.vob -o output.avi -ovc x264 -x264encopts threads=3:bitrate=1500 -oac pcm
```

This line wouldn't be the best for what you're wanting, but it might help you along.
It will convert input.vob convert it to h264 using 3 threads (this is faster than 2 threads for some odd reason on a dual-core CPU) with a video bitrate of 1500.  Sound is just uncompressed pcm.

You might have to combine a few scripts (encode audio separately then mux it back in later) to get the desired quality out of it all.

The Gentoo forums have some good info about various mencoder settings.

I'd be very interested in doing some more research into this too.  Keep posting any updates you discover here please.

---

### Post by jabster on 2007-12-12
Well, I think I'm closer now.

I actually went back to K9Copy and looked thru it's MPEG capabilities again.

So I now have an AVI, h264, and I've tried the "copy" and "ac3" options for audio encoding.

Only one question: Is there a way to check what audio is actually with the AVI file? I want the 6-channel audio, but nothing I can find actually tells me what it is. mplayer just outputs
```
==> Found audio stream: 1
AVI: Searching for audio stream (id:1)
```
For the vob file I get this from mplayer:
```
==> Found audio stream: 128
```

Using konqueror/dolphin properties, the meta-info for both copy and ac3 shows the audio codec as "DVM." No idea what that means.

So, I think I'm ok, but all I need now is a way to actually check what I have.

The video looks pretty damn good tho.

-john

---

### Post by Rhubarb on 2007-12-13
I find vlc to be a good app to show the different streams + codecs + info about videos.

In vlc, open up the video, play it (you can now pause it if you want to).
View --> Stream and Media Info

You might have some luck with avidemux too.

I might get around to using k9copy aswell ;)

---

### Post by ron999 on 2007-12-13
Hi

There's a CLI app called MediaInfo.
To use it you just enter MediaInfo <filename>.
You can download mediainfo_0.7.5.4-1_i386.deb from here:-
[http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612]("http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612")

This is a typical output:-

ron@ron-desktop:~$ MediaInfo /home/ron/trial4.avi
General #0
Complete name : /home/ron/trial4.avi
Format : AVI
Format/Info : Audio Video Interleave
Format/Family : RIFF
File size : 2.70 MiB
PlayTime : 1mn 5s
Bit rate : 338 Kbps
Writing application : Lavf0d.50.5.0

Video #0
Codec : xvid
PlayTime : 1mn 5s
Bit rate : 197 Kbps
Width : 160 pixels
Height : 128 pixels
Aspect ratio : 5/4
Frame rate : 12.000 fps
Resolution : 24 bits
Bits/(Pixel*Frame) : 0.803

Audio #0
Codec : MPEG-1 Audio layer 3
Codec profile : Joint stereo
PlayTime : 1mn 5s
Bit rate : 125 Kbps
Bit rate mode : CBR
Channel(s) : 2 channels
Sampling rate : 48 KHz
Resolution : 16 bits
StreamSize : 1001 KiB
Writing library : Lame

---

### Post by jabster on 2007-12-13
> **ron999 said:**
> Hi

There's a CLI app called MediaInfo.
To use it you just enter MediaInfo <filename>.
You can download mediainfo_0.7.5.4-1_i386.deb from here:-
[http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612]("http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612")

Hi there. I tried that, and got this:
```
Audio #0
Codec                : AC3
Codec/Info           : Dolby AC3
PlayTime             : 1h 59mn
Bit rate             : 448 Kbps
Bit rate mode        : CBR
Channel(s)           : 2 channels
Sampling rate        : 48 KHz
Resolution           : 16 bits

```

Now, going by k9copy, the audio track I selected is "audio 1 English ac3 6ch 48kHz drc." But my ripped AVI appears to be only 2 channels per mediainfo.

running mediainfo on my vob file shows this:
```
Audio #0
Codec                : AC3
Bit rate             : 448 Kbps
Bit rate mode        : CBR
Channel(s)           : 6 channels
Channel positions    : Front: L C R, Rear: L R, Subwoofer
Sampling rate        : 48 KHz
```

So I appear to be back to one of my original questions: How do I get the 6 channel audio when I'm ripping my DVDs?

I have a title.vob & a title.ac3 ripped from the DVD (and a title-EN.vob with the other audio tracks removed), all with the 6-channel audio. What I apparently still need is the way to mux those two together in an h264 avi.

thanks,
-john


p.s. there was no deb file of mediainfo, just a tar.gz containing the executable. Which is fine.

---

### Post by jabster on 2007-12-13
I think I got it.

Will report back later.

-john

---

### Post by jabster on 2007-12-13
OK.

Now I'm confused.

First, here's my mencoder command (made a small shell script):
```
# First pass
mencoder -v title.vob -vf crop=720:352:0:64,scale=720:352 -ovc x264 -x264encopts subq=4:bframes=4:b_pyramid:weight_b:pass=1:psnr:bitrate=1000 -oac copy -ofps 24000/1001 -o /dev/null

# Second Pass
mencoder -v title.vob -vf crop=720:352:0:64,scale=720:352 -ovc x264 -x264encopts subq=5:partitions=4x4:8x8dct:frameref=3:me=hex:bframes=4:b_pyramid:pass=2:psnr:bitrate=1000 -oac copy -ofps 24000/1001 -o serenity.avi
```

Here's my trial mencoder command:
```
# First pass
mencoder -v title.vob -endpos 90 -vf crop=720:352:0:64,scale=720:352 -ovc x264 -x264encopts subq=4:bframes=4:b_pyramid:weight_b:pass=1:psnr:bitrate=1000 -oac copy -ofps 24000/1001 -o /dev/null

# Second Pass
mencoder -v title.vob -endpos 90 -vf crop=720:352:0:64,scale=720:352 -ovc x264 -x264encopts subq=5:partitions=4x4:8x8dct:frameref=3:me=hex:bframes=4:b_pyramid:pass=2:psnr:bitrate=1000 -oac copy -ofps 24000/1001 -o serenity.avi
```

I ran the second command first, encoding only 90 seconds of the vob to test things first. Running mediainfo on that avi gave me this
```
Audio #0
Codec                : AC3
PlayTime             : 3mn 40s
Bit rate             : 448 Kbps
Bit rate mode        : CBR
Channel(s)           : 6 channels
Channel positions    : Front: L C R, Rear: L R, Subwoofer
Sampling rate        : 48 KHz
Resolution           : 16 bits
StreamSize           : 11.7 MiB
```

So I think "great! lets encode the whole thing." I get home and run mediainfo again and get told it's 2 channel audio again (sorry, but I deleted the avi so cant paste the exact output).

Any idea why this is?

thanks,
john

---

### Post by lowebb on 2007-12-14
Jeeez's if theres a hard way to do something you guys can find it.

USE.K9COPY-YOU'RE.DONE

---

### Post by jabster on 2007-12-14
> **lowebb said:**
> Jeeez's if theres a hard way to do something you guys can find it.

USE.K9COPY-YOU'RE.DONE

Excellent idea.

Only k9copy is not giving me the 6-channel audio that I want. If you'd notice, I have tried that already.

Perhaps you can offer suggestions as to what settings to use in k9copy to get a good, high quality video with 6-channel audio?

Thanks!
-john

---

### Post by jabster on 2007-12-15
As  a brief followup, here's the mediainfo output on the 2-pass mencoder command, encoding the whole vob and not just a short portion:
```
Video #0
Codec                : h264
PlayTime             : 1h 38mn
Bit rate             : 1287 Kbps
Width                : 720 pixels
Height               : 352 pixels
Display Aspect ratio : 2.045
Frame rate           : 23.976 fps
Resolution           : 24 bits

Audio #0
Codec                : AC3
Codec/Info           : Dolby AC3
Bit rate             : 448 Kbps
Bit rate mode        : CBR
Channel(s)           : 2 channels
Sampling rate        : 48 KHz
Resolution           : 16 bits
Coherency/PlayTime   : 7142560
```

So I've got the AC3, but still only 2-channel

-john

---

### Post by jabster on 2007-12-18
Success!!!

Well, I've got it finally:
```
# First pass
mencoder -v title.vob -channels 6 -af channels=6:6:0:0:4:1:1:2:2:3:3:4:5:5,volume=11 -vf crop=720:352:0:64,scale=720:352 -ovc x264 -x264encopts subq=4:bframes=4:b_pyramid:weight_b:pass=1:psnr:bitrate=1000 -oac copy -ofps 24000/1001 -o /dev/null
# -endpos 90

# Second Pass
mencoder -v title.vob -channels 6  -af channels=6:6:0:0:4:1:1:2:2:3:3:4:5:5,volume=11 -vf crop=720:352:0:64,scale=720:352 -ovc x264 -x264encopts subq=5:partitions=4x4:8x8dct:frameref=3:me=hex:bframes=4:b_pyramid:pass=2:psnr:bitrate=1000 -oac copy -ofps 24000/1001 -o serenity.avi
```

And the output from mediainfo:
```
General #0
Complete name        : /media/extra/serenity/serenity-x264-6chDolbyAC3.avi
Format               : AVI
Format/Info          : Audio Video Interleave
Format/Family        : RIFF
File size            : 1.21 GiB
PlayTime             : 1h 38mn
Bit rate             : 1765 Kbps
Writing application  : MEncoder 2:1.0~rc1-0ubuntu13.1
Writing library      : MPlayer

Video #0
Codec                : h264
PlayTime             : 1h 38mn
Bit rate             : 1287 Kbps
Width                : 720 pixels
Height               : 352 pixels
Display Aspect ratio : 2.045
Frame rate           : 23.976 fps
Resolution           : 24 bits

Audio #0
Codec                : AC3
Codec/Info           : Dolby AC3
Bit rate             : 448 Kbps
Bit rate mode        : CBR
Channel(s)           : 6 channels
Sampling rate        : 48 KHz
Resolution           : 16 bits
Coherency/PlayTime   : 7142560
```

The channels option is apparently needed to correctly map the channel data from the DVD to channels for mplayer. I found that info in newsgroup posting from at least 1.5-2 years ago, so I don't know if that is still correct.

Only problem is, I don't know how to test my AVI right now.

I may go grab a DVD, and dump and encode the THX screen, then copy it do a DVD and play it to see how it sounds. My soundcard doesn't have 5.1 unfortunately.

As a second possibility, would someone be willing to play the THX.avi on a HTPC or whatnot to check the channel mapping?

-john

---

