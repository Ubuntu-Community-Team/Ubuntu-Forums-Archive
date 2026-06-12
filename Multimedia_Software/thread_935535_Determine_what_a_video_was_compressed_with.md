---
title: "Determine what a video was compressed with?"
date: 2008-10-01
forum: Multimedia Software
---

### Post by jakev383 on 2008-10-01
Okay, so I record shows off of TV and record in my DVDs to keep from swapping disks all the time in my Myth setup.  This uses a lot of space; VOB files are huge!
Now I download a TV episode off of a torrent, and it's a HD sample but is only 370M.  It has the extension .avi (which I know is just a container) and it says (in the filename) it's an XviD. How do I find out what it's been sampled at so I can convert my other movie files to this same format?  It's good quality, but the size comparison is unbelievable! I'd like to know what settings were used so I can convert the rest of my library to the same format!
Thanks for any suggestions!

---

### Post by shirilover on 2008-10-02
Try using [MediaInfo](http://mediainfo.sourceforge.net).

It will give you a great deal of information on the A/V streams within most containers. It will give you average bit rates and encoding libraries used, but not any of the settings or filters used.

---

### Post by jakev383 on 2008-10-02
That was great!
I downloaded the CLI version and ran it on one of the videos and got back a WEALTH of information:
```

Video
Format                           : MPEG-4 Visual
Format profile                   : Streaming Video@L1
Format settings, BVOP            : Yes
Format settings, QPel            : No
Format settings, GMC             : No warppoints
Format settings, Matrix          : Default
Muxing mode                      : Packed bitstream
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 42mn 23s
Bit rate                         : 1 021 Kbps
Width                            : 624 pixels
Height                           : 352 pixels
Display aspect ratio             : 16/9
Frame rate                       : 23.976 fps
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.194
Stream size                      : 309 MiB (88%)
Writing library                  : XviD 1.1.2 (UTC 2006-11-01)

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Codec ID                         : 55
Codec ID/Hint                    : MP3
Duration                         : 42mn 23s
Bit rate mode                    : Variable
Bit rate                         : 123 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 37.3 MiB (11%)
Alignment                        : Aligned on interleaves
Interleave, duration             : 24 ms (0.58 video frame)
Interleave, preload duration     : 505 ms

```

I'll print this out and sit down to see how to turn all the switches on for these settings this weekend and see if I can't reproduce the results.

---

### Post by aeiah on 2008-10-02
since you seem to be new to the world of xvid compression and other such things, you might want to play around before compressing all of your stuff. with xvid, you get the best results if you do a multipass encoding. better codecs exist than xvid now, such as x264, although it isnt as widespread and you will probably have to mess around with it more to get the best results. what you choose is up to you. i wouldnt worry about emulating the compression used for that video specifically. just try and aim for the same filesize and resolution i guess

---

### Post by jakev383 on 2008-10-02
Yeah, I've been playing with xvid for a few weeks now, but have never been able to get my vob files compressed down enough to keep the quality. I saw this vid that downloaded and the quality is great, but the size is small and I wanted to use it as a guideline to try and compress my vob files - I won't do my entire library until I'm happy.
One big problem I kept running into was when I watched my vob on MythTV it was in English, but when I compressed it with xvid it would be in Spanish. I just got done compressing one so I'll go check it out in a little bit and see if the quality came out the way I want and then see if the language is correct.
Thanks for the tips though.

---

### Post by FakeOutdoorsman on 2008-10-02
I agree with aeiah that encoding with two-pass x264 usually gives excellent results, but it can mean a longer encoding time compared to xvid.  Recent ffmpeg now has good x264 presets, but you'll have to compile ffmpeg yourself to use them.  The version of ffmpeg from the Ubuntu repository does not support restricted formats.  Instead of compiling you could also modify the presets for not-so-new ffmpeg versions such as the one from Medibuntu.  If you decide to try ffmpeg, save yourself some time when testing by only encoding a certain number of frames with "-vframes 300" (300 frames will be encoded with this example).

I don't know what you're encoding with, but VOB can contain multiple audio steams (english, spanish, commentary, etc).  You'll just have to tell it which stream you want.  With ffmpeg you can use the -map option.  I'm mencoder ignorant, so I can't help there.

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")
[FFmpeg libx264 presets]("http://rob.opendot.cl/index.php/2008/09/17/ffmpeg-libx264-presets/")

---

### Post by jakev383 on 2008-10-02
Okay, so I've played with mpeg4 and seem to have come up with a combo that works for me:
```

mencoder -ovc frameno -o frameno.avi -oac mp3lame -lameopts abr:br=128 -alang en movie.vob

mencoder -oac copy -o /dev/null -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200:vhq:vpass=1:vqmin=1:vqmax=31 -vop scale -zoom -xy 720 movie.vob

mencoder -oac copy -o recoded-movie.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200:vhq:vpass=2:vqmin=1:vqmax=31 -vop scale -zoom -xy 720 movie.vob

```
Now the original movie shows at 57:19 minutes.  The new one (.avi) shows as 1:25:23. Huh?
Also have a weird issue where my Myth frontend skips the first 20 seconds of the show for some reason - it plays fine on my desktop though (both are mapped to a NFS share for the video). Figure that one out later.

---

