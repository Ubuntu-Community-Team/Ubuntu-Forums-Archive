---
title: "need help encoding xvid with ffmpeg"
date: 2012-01-09
forum: Multimedia Software
---

### Post by bnut on 2012-01-09
I'm trying to encode a kids cartoon from .ts source into a reasonable sized avi file.  The resulting output is a bit too blocky. 

Does anyone have a good ffmpeg instruction that they would use or see any mistakes in my instruction?

I'm using the following ffmpeg instruction:
**ffmpeg -i input.ts -y -pass 1 -c:v mpeg4 -s hd480 -b:v 1072k -bf 2 -level 5 -deinterlace -an -f avi /dev/null && ffmpeg -i input.ts -y -pass 2 -c:v mpeg4 -s hd480 -b:v 1072k -bf 2 -level 5 -deinterlace -c:a libmp3lame -b:a 128k -ac 2 output.avi**

Using the source described here:[B]
mediainfo input.ts[/B]
General
ID                                       : 1 (0x1)
Complete name                            : input.ts
Format                                   : MPEG-TS
File size                                : 2.38 GiB
Duration                                 : 25mn 32s
Overall bit rate mode                    : Variable
Overall bit rate                         : 13.4 Mbps

Video
ID                                       : 2048 (0x800)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@High
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Default
Format settings, GOP                     : M=3, N=15
Codec ID                                 : 2
Duration                                 : 25mn 32s
Bit rate mode                            : Variable
Bit rate                                 : 12.3 Mbps
Maximum bit rate                         : 14.5 Mbps
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.198
Stream size                              : 2.20 GiB (92%)

The mediainfo of the result (sample) shows the following:
**mediainfo output.avi**
General
Complete name                            : output.avi
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 4.37 MiB
Duration                                 : 30s 48ms
Overall bit rate                         : 1 220 Kbps
Writing application                      : Lavf53.24.2

Video
ID                                       : 0
Format                                   : MPEG-4 Visual
Format profile                           : Advanced Simple@L5
Format settings, BVOP                    : 2
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (H.263)
Codec ID                                 : FMP4
Duration                                 : 30s 30ms
Bit rate                                 : 1 076 Kbps
Width                                    : 852 pixels
Height                                   : 480 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.088
Stream size                              : 3.85 MiB (88%)
Writing library                          : Lavc53.42.4


pertinent version info
**ffmpeg -version**
ffmpeg 0.9.1-4:0.9.1-0ubuntu1~jon1
libavutil    51. 32. 0 / 51. 32. 0
libavcodec   53. 42. 4 / 53. 42. 4
libavformat  53. 24. 2 / 53. 24. 2
libavdevice  53.  4. 0 / 53.  4. 0
libavfilter   2. 53. 0 /  2. 53. 0
libswscale    2.  1. 0 /  2.  1. 0
libpostproc  52.  0. 0 / 52.  0. 0


**uname -a**
Linux server 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by andrew.46 on 2012-01-10
Do you have a particular reason for using xvid and avi? A better choice might be x264 and mp4 or even mkv...

---

### Post by coffeecat on 2012-01-10
@bnut, if you do really want to create an xvid/avi file and you don't mind using a GUI app, try DeVeDe. Although it's primarily for DVD creation it does have an option to re-encode video files (including *.ts) to xvid/AVI. In my experience results are good. Open DeVeDe and choose the last option (DivX/MPEG-4) in the disc type selection window.

---

### Post by bnut on 2012-01-10
@andrew.46: xvid and the avi container are more portable.  These files are not intended for display by a computer, but rather can be transferred to dvd or a flashdrive for playback on a wide variety of devices.  I do use x264 and the mkv container when portability is not the requirement.

@coffecat: I prefer commandline since it can be scripted, but I will give DeVeDe a shot.  I have found my Handbrake transcodes have not been up to par, Arista output looked good but was out of sync, and Transmageddon had problems loading the codec.

I'm confident ffmpeg can satisfy the task, but the switches and options have changed so frequently that I'm not able to pin them down.  I'm still looking for an appropriate set of flags.

---

### Post by andrew.46 on 2012-01-10
> **bnut said:**
> @andrew.46: xvid and the avi container are more portable.  These files are not intended for display by a computer, but rather can be transferred to dvd or a flashdrive for playback on a wide variety of devices.  I do use x264 and the mkv container when portability is not the requirement.

Fair enough. Perhaps you could consider adding:

```
-vtag XVID
```

to ensure portability as some devices baulk at FFmpeg's mpeg4 fourcc. This is [documented here]("http://ffmpeg.org/faq.html#How-do-I-encode-Xvid-or-DivX-video-with-ffmpeg_003f") btw. If you have a look at [the next section]("http://ffmpeg.org/faq.html#Which-are-good-parameters-for-encoding-high-quality-MPEG_002d4_003f") you will see some of the flags you could try manipulating to get a better video encode and this should make a difference.

A final thought is perhaps try qscale rather than 2 pass / bitrate for your video?

---

### Post by bnut on 2012-01-11
Thanks, andrew.46.

I set the vtag to xvid and the recommended flags 'mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300'.   I ran it through a couple of times with varying qscale values.  Qscale 5 got me down to the file size I'm looking for but the edges are a bit less sharp that I'd like (I am fully expecting them to be lossy xvid quality, I'm not expecting zero artifacts).  I tried a couple of multipasses with maxrate set instead of cbr.  Those didn't come out as well as I'm looking for either (plus the filesizes were way too small).  

I'll keep playing with the flags and some short runs to see if I can get this drilled down to a successful instruction set.  I'll probably add bframes on the next run and do a little bit of research on the others that I'm unfamiliar with (qprd, mv0, and skiprd) to see how those affect the output.  I'll post that here whenever I settle on one.

Mark solved for the time being.

---

### Post by andrew.46 on 2012-01-11
> **bnut said:**
> T I'll post that here whenever I settle on one.

I would be interested to see your final commandline, I struggled with the options myself and also found the end results a little unsatisfactory. Another option of course is to try the same options with the external xvid library, if it is compiled in to your copy of FFmpeg:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs 2>/dev/null | grep libxvid[/COLOR]**
  EV    libxvid         libxvidcore MPEG-4 part 2

```

Just to add another layer of complexity to your investigations :)

---

### Post by SeijiSensei on 2012-01-11
You can give **mencoder** a whirl instead of ffmpeg.  A quick howto for XviD encoding is [here]("http://en.gentoo-wiki.com/wiki/Mencoder#XviD").

---

### Post by bnut on 2012-01-13
I got sidetracked with another project but will be getting back to this shortly.  My initial mencoder run didn't come very impressive either but I'll give it a more exhaustive set of tests.  I'll post the results of the comparison along with my final commands here when I have completed the tests.

---

### Post by SeijiSensei on 2012-01-13
Did you use two-pass encoding?  One of the nice features in mencoder is the ability to control the size of the final output in the second pass.

I converted a number of 720p/H.264 videos to XviD back when my computer couldn't handle the decoding task involved to watch them.  I followed the same approach as described in the Gentoo document to which I linked and thought the results were quite acceptable.

---

### Post by satanselbow on 2012-01-13
Another good reason to stick with Xvid/mp3 is "picky" USB equipped televisions ;)

This is my "standard" one-liner for a reasonable size/quality avi I can chuck on a USB stick and play on any of the tellies in the house :D

It's good to go with anything from movies to iplayer downloads ;)

```
ffmpeg -i 'nemo.avi' -r 25 -s 640x368 -aspect 16:9 -b 988k -vcodec libxvid -vtag xvid -metadata title='Finding Nemo' -acodec libmp3lame -ac 2 -ab 128k '~/Videos/Finding Nemo.avi'
```

Might not be quite up to scratch but watchable enough when you don't want to have to wait all day :popcorn:

---

### Post by bnut on 2012-01-15
SeijiSensei: My initial mencoder test did not include 2 pass.  I will use the gentoo based guide on my followup tests.  I probably overlooked it originally as I was searching for Ubuntu specific posts.  I'll definitely give it a shot and followup here.  Thanks for the tip.  :D

Satanselbow:  I'll test that instruction out, too!  Thanks.

---

