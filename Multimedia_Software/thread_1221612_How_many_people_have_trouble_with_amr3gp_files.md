---
title: "How many people have trouble with amr/3gp files?"
date: 2009-07-24
forum: Multimedia Software
---

### Post by andrew.46 on 2009-07-24
Hi,

I have seen a rash of posts on these orums recently that are from people having trouble accessing 3gp files that for the most part have amr sound in them. I am a little curious to see how many people are eventually managing to access these files, or perhaps totally failing to access them at all.

My own solution for these files is to compile my own copy of both FFmpeg and MPlayer against the libopencore-amr libraries and this works well enough. For those who are not keen to compile I am aware that at least for Jaunty and earlier there is the Medibuntu MPlayer that will play these files.

So what are people using? For a demonstration file, so that we are all talking about the same thing, I have created a reasonable quality 3gp file that can be downloaded from my web site:

```
wget http://www.andrews-corner.org/samples/Rammstein_Du_Hast.3gp
```

which I created myself using:

```

ffmpeg -y -i Rammstein_Du_Hast.mp4 -s qcif -vcodec h263 \
-acodec libopencore_amrnb -ac 1 -ar 8000 -r 25 -ab 12200 Rammstein_Du_Hast.3gp

```

from a high quality h264/aac youtube video. The sound is I believe as good as amr sound can get although that is not really saying much, amr was never really intended for music playback after all :-). Anyway I will be interested to hear any comments.

Andrew

---

### Post by mc4man on 2009-07-24
Much, much too late to explore soemthing odd (could be local issue

your .3gp plays fine with 
(s)mplayer  - slightly older build (libarm-nb
(s)mplayer - current (opencore
vlc - 1.0.1- pre
ffplay (current

(for command line changed name to 2.3gp (can't type well

On all xine based players no audio - reports 
 > totem-xine
[libopencore_amrnb @ 0x8b74500]amr_nb: [COLOR="Blue"]multichannel decoding not supported[/COLOR]


mediainfo reports

> General

Complete name                    : /home/doug/Rammstein_Du_Hast.3gp

Format                           : MPEG-4

Format profile                   : 3GPP Media Release 4

Codec ID                         : 3gp4

File size                        : 6.19 MiB

Duration                         : 3mn 54s

Overall bit rate                 : 222 Kbps

Encoded date                     : UTC 1970-01-01 00:00:00

Tagged date                      : UTC 1970-01-01 00:00:00



Video

ID                               : 1

Format                           : H.263

Codec ID                         : s263

Duration                         : 3mn 53s

Bit rate mode                    : Variable

Bit rate                         : 206 Kbps

Width                            : 176 pixels

Height                           : 144 pixels

Display aspect ratio             : 1.504

Frame rate mode                  : Constant

Frame rate                       : 25.000 fps

Bits/(Pixel*Frame)               : 0.325

Stream size                      : 5.74 MiB (93%)

Encoded date                     : UTC 1970-01-01 00:00:00

Tagged date                      : UTC 1970-01-01 00:00:00



Audio

ID                               : 2

Format                           : AMR

Format/Info                      : Adaptive Multi-Rate

Format profile                   : Narrow band

Codec ID                         : samr

Duration                         : 3mn 54s

Bit rate mode                    : Constant

Bit rate                         : 12.8 Kbps

Channel(s)                       : [COLOR="Blue"]2 channels
[/COLOR]
Sampling rate                    : 8 000 Hz

Resolution                       : 16 bits

Stream size                      : 366 KiB (6%)

Encoded date                     : UTC 1970-01-01 00:00:00

Tagged date                      : UTC 1970-01-01 00:00:00


ffprobe reports
> doug@doug-laptop:~$ ffprobe -show_streams 2.3gp
FFprobe version SVN-r86, Copyright (c) 2007-2009 Stefano Sabatini
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  built on Jul  7 2009 18:07:10, gcc: 4.3.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '2.3gp':
  Duration: 00:03:54.08, start: 0.000000, bitrate: 221 kb/s
    Stream #0.0(und): Video: h263, yuv420p, 176x144 [PAR 12:11 DAR 4:3], 25 tbr, 25 tbn, 29.97 tbc
    Stream #0.1(und): Audio: libopencore_amrnb, 8000 Hz, [COLOR="Blue"]1 channels[/COLOR], s16
[STREAM]
codec_name=h263
codec_long_name=H.263 / H.263-1996, H.263+ / H.263-1998 / H.263 version 2
decoder_time_base=1001/30000
codec_type=video
language=&#65533;
r_frame_rate=25.000000
r_frame_rate_num=25
r_frame_rate_den=1
width=176
height=144
gop_size=12
has_b_frames=0
sample_aspect_ratio=12/11
display_aspect_ratio=4/3
pix_fmt=yuv420p
index=0
time_base=1/25
language=und
start_time=0.000000 
duration=233.640000 
nb_frames=5841
[/STREAM]
[STREAM]
codec_name=libopencore_amrnb
codec_long_name=OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
decoder_time_base=0/1
codec_type=audio
language=&#65533;&#65533;&#65533;
sample_rate=8000.000000 
channels=[COLOR="Blue"]1[/COLOR]
bits_per_sample=0
index=1
time_base=1/8000
language=und
start_time=0.000000 
duration=234.080000 
nb_frames=11704


Another .3gp plays on all players with sound (ffprobe looks about the same I think (1 diff

>  doug@doug-laptop:~$ ffprobe -show_streams 1.3gp
FFprobe version SVN-r86, Copyright (c) 2007-2009 Stefano Sabatini
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  built on Jul  7 2009 18:07:10, gcc: 4.3.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1.3gp':
  Duration: 00:02:30.73, start: 0.000000, bitrate: 94 kb/s
    Stream #0.0(eng): Video: h263, yuv420p, 176x144 [PAR 12:11 DAR 4:3], 29.97 tbr, 90k tbn, 29.97 tbc
    Stream #0.1(eng): Audio: libopencore_amrnb, 8000 Hz, 1 channels, s16
[STREAM]
codec_name=h263
codec_long_name=H.263 / H.263-1996, H.263+ / H.263-1998 / H.263 version 2
decoder_time_base=1001/30000
codec_type=video
language=&#65533;
r_frame_rate=29.970030
r_frame_rate_num=30000
r_frame_rate_den=1001
width=176
height=144
gop_size=12
has_b_frames=0
sample_aspect_ratio=12/11
display_aspect_ratio=4/3
pix_fmt=yuv420p
index=0
time_base=1/90000
language=eng
start_time=0.000000 
duration=150.733333 
nb_frames=2261
[/STREAM]
[STREAM]
codec_name=libopencore_amrnb
codec_long_name=OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
decoder_time_base=0/1
codec_type=audio
language=&#65533;&#65533;&#65533;
sample_rate=8000.000000 
channels=1
bits_per_sample=0
index=1
time_base=1/8000
language=eng
start_time=0.000000 
duration=150.640000 
nb_frames=7532

---

### Post by andrew.46 on 2009-07-24
Hi mc4man,

> **mc4man said:**
> 

your .3gp plays fine with 
(s)mplayer  - slightly older build (libarm-nb
(s)mplayer - current (opencore
vlc - 1.0.1- pre
ffplay (current

But in a disappointing result it does not play with the default Karmic Koala MPlayer:

Karmic Koala mplayer-nogui with libavcodec-unstripped-52 does not play amr files
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/403937](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/403937)

Unless I have it all terribly wrong :-).

Andrew

---

### Post by mc4man on 2009-07-24
> But in a disappointing result it does not play with the default Karmic Koala MPlayer:

I don't think the 'default' mplayer will ever be able to decode arm.

It appears they're using an mplayer source from april (04/26) which would use the nonfree arm codecs which isn't going to happen.

Even if they used a current mplayer source that used the open source arm I'm thinking it still wouldn't matter.
This is just a guess, and could be skewed because I use 8.04 (though it's more than capable lib and codec wise

It appears (and I could be very wrong here) that the default mplayer  is built without using the  ffmpeg included in the mplayer source and uses the repo version instead, which would be the 0.5 release of 03/03 (which is built without arm support

It also appears that the mplayer source used has been altered slightly from the orig for that -r

I'd assume medibuntu will pick up the slack once karmic is released

---

### Post by andrew.46 on 2009-07-24
Hi mc4man,

> **mc4man said:**
> It appears (and I could be very wrong here) that the default mplayer  is built without using the  ffmpeg included in the mplayer source and uses the repo version instead, which would be the 0.5 release of 03/03 (which is built without arm support

It also appears that the mplayer source used has been altered slightly from the orig for that -r

There is certainly something a little odd there, in particular since the command:

```
mplayer -ac help | grep amr
```

shows amr support that in fact does not exist. I am starting to suspect that that the Karmic MPlayer may not be the panacea I had expected and perhaps there might be room for one more svn MPlayer guide....

And yes it will be interesting to see what Medibuntu has in mind. So far their strongest action has been to withdraw their copy of MPlayer completely and perhaps this is the total plan. An svn snapshot taken from the svn tree, rather than svn rc3, and compiled against libopencore-amr would be very nice but perhaps a little *too* hopeful.

andrew

---

### Post by mc4man on 2009-07-24
again this on hardy, but it is a well 'fortified' install

From a build log using karmic source and applied diff
(( this is basically mplayer 'running' it's config

> Checking for LIVE555 Streaming Media libraries ... yes (using /usr/lib/live)
Checking for FFmpeg libavutil ... yes 
Checking for FFmpeg libavcodec ... yes (libavcodec.so is discouraged over static libavcodec)
Checking for FFmpeg libavformat ... yes 
Checking for FFmpeg libpostproc ... yes (using libpostproc.so, but static libpostproc is recommended)
Checking for FFmpeg libswscale ... yes (using libswscale.so, but static libswscale is recommended)
Checking for libamr narrowband ... no (libavcodec (static) is required by libamr_nb, sorry)
Checking for libamr wideband ... no (libavcodec (static) is required by libamr_wb, sorry)

From the rules file
> --disable-libavutil_a \
	--disable-libavcodec_a \
	--disable-libavformat_a \
	--disable-libpostproc_a \
	--disable-libswscale_a \


.............of no great importance

What's interesting is while I can build any -r source of mplayer, either as a configure,make, make install or as a debian package I can't build karmic's source (just unpacked, ./configure, make. - no diff applied

There's something 'changed' in the source (other than missing dvdcss.h

You might want to try for curiosity 

./configure --disable-libdvdcss-internal is the min. configure that almost succeeded here

[http://packages.ubuntu.com/karmic/mplayer](http://packages.ubuntu.com/karmic/mplayer)

Source is in box on right side

---

### Post by andrew.46 on 2009-07-24
Hi mc4man,

Thanks again for showing the light :-).

> **mc4man said:**
> From the rules file

```
--disable-libavutil_a \
--disable-libavcodec_a \
--disable-libavformat_a \
--disable-libpostproc_a \
--disable-libswscale_a \ 

```

which of course makes perfect sense when you see the build choice between libavcodec52 and libavcodec-unstripped-53. MPlayer, as you have found, is *not* using its static FFmpeg in Karmic but rather the system one, which sill be shared with FFmpeg itself. A somewhat tricky course that the Debian/Ubuntu devs have chosen to steer I would think? Great potential for breakage particularly if someone decides to build an svn FFmpeg.

> What's interesting is while I can build any -r source of mplayer, either as a configure,make, make install or as a debian package I can't build karmic's source (just unpacked, ./configure, make. - no diff applied


I shall have a go but the slackware part of me is still somewhat horrified at the carving up of the MPlayer source that has gone on here.

```
Checking for libamr narrowband ... no **[COLOR="Red"](libavcodec (static) is required by libamr_nb[/COLOR]**, sorry)
Checking for libamr wideband ... no **[COLOR="Red"](libavcodec (static) is required by libamr_wb[/COLOR]**, sorry)
```

And that is the end of amr playback out-of-the-box by the looks of it...  

Andrew

---

### Post by andrew.46 on 2009-07-26
Hi mc4man,

> **mc4man said:**
> What's interesting is while I can build any -r source of mplayer, either as a configure,make, make install or as a debian package I can't build karmic's source (just unpacked, ./configure, make. - no diff applied

In fact I also failed to build this source code, as my teenagers would probably call it: an *epic* fail :-). 

Andrew

---

### Post by mc4man on 2009-07-26
In regards to orig question what I've found (using some different 8.04 installs

(all amr means either nonfree, or opensource created or 'touched' by ffmpeg )

mplayer plays all amr,  as long as appropriate amr-dev was present during the build for the mplayer source and matching lib is installed

vlc plays all amr also as long as the shared ffmpeg libraries were built with amr enabled using whatever lib and -dev appropriate to the ffmpeg source
(( the only possible exception may be a vlc built off of a nonfree ffmpeg and then replacing the ffmpeg shared libs with ones built off of the opensource ones.

Gstreamer player (totem-gstreamer)  doesn't seem to want to play at all in regards to sound
 (possibly rebuilding the gstreamer plugins that depend on ffmpeg libs off of an enabled, shared ffmpeg would work

Xine based players in the presence of amr enabled ffmpeg shared libs will play amr as long as not touched/encoded by ffmpeg (either a nonfree or opensource enabled ffmpeg

(( based on the debian/ubuntu default for xine-lib, -  to use the external ffmpeg libraries


By "touched" i mean this
Take a .3gp that totem-xine or kaffeine plays (quicktime created..?)
Do a ffmpeg -acodec copy -vcodec copy, it will then not play sound, (the header is changed, only affects xine-based players, same whether ffmpeg is using non-free or open-source amr
The error is noted previously, seen as multichannel when if fact it's not

Some of these observations may be localized, though I think they're pretty solid

---

