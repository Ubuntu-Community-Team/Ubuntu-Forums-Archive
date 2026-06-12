---
title: "ffmpeg convert errors; files seem ok"
date: 2009-06-07
forum: Multimedia Software
---

### Post by logos34 on 2009-06-07
Noticing some strange errors with ffmpeg...I hope I can overlook them because I put a lot of effort into recompiling it with added codec support.

Here's what I always get when converting any format to mp3:

> $ffmpeg -i 04\ -\ Chinatown.ogg -acodec libmp3lame -ab 175k 04\ -\ Chinatown.mp3
FFmpeg version SVN-r18839, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 21 2009 13:57:06, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, ogg, from '04 - Chinatown.ogg':
  Duration: 00:04:01.01, start: 0.000000, bitrate: 164 kb/s
    Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 192 kb/s
Output #0, mp3, to '04 - Chinatown.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, s16, 175 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[COLOR="Red"][libmp3lame @ 0x109c030]lame: output buffer too small (buffer index: 8882, free bytes: 910)
Audio encoding failed[/COLOR]

File seems/sounds ok (although the bitrate is off):
> 
$ mediainfo 04\ -\ Chinatown.mp3 
General #0
Complete name                : 04 - Chinatown.mp3
Format                       : MPA1L3
File size                    : 4.60 MiB
PlayTime                     : 4mn 1s
Bit rate                     : 160 Kbps
[COLOR="Red"]Writing library              : Lavf52.32.0[/COLOR]

Audio #0
Codec                        : MPEG-1 Audio layer 3
Codec profile                : Joint stereo
Bit rate mode                : CBR
Bit rate                     : [COLOR="Red"]160[/COLOR] Kbps
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
[COLOR="Red"]Writing library              : LAME3.98.2[/COLOR]

EDIT: when I use target bitrate of 192k, that works.  Maybe you can only set the CBR for 128, 160, 192, 224, etc)

There was a thread ([here, post #6]("http://drupal.org/node/376012")) about this being a minor bug in the way ffmpeg interfaces with lame 3.98 codec, which doesn't affect anything, and nothing to worry about.  Maybe someone can verify this.

Another thing is, unless I specify '-acodec libvorbis' when converting to ogg vorbis, it will make a flac!

ex:

> $ ffmpeg -i 12\ -\ The\ Book\ of\ Hanging\ Gardens\,\ Op.\ 15.mpc -ab 160k 12\ -\ The\ Book\ of\ Hanging\ Gardens\,\ Op.\ 15.ogg
FFmpeg version SVN-r18839, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 21 2009 13:57:06, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mpc, from '12 - The Book of Hanging Gardens, Op. 15.mpc':
  Duration: 00:01:23.33, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: mpc7, 44100 Hz, stereo, s16
Output #0, ogg, to '12 - The Book of Hanging Gardens, Op. 15.ogg':
    Stream #0.0: Audio: [COLOR="Red"]flac,[/COLOR] 44100 Hz, stereo, s16, 160 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    3416kB time=83.38 [COLOR="Red"]bitrate= 335.6kbits/s [/COLOR]   
video:0kB audio:3382kB global headers:0kB muxing overhead 1.029008%
@ubuntu:~/videos/audio test files$ mediainfo 12\ -\ The\ Book\ of\ Hanging\ Gardens\,\ Op.\ 15.ogg General #0
Complete name                : 12 - The Book of Hanging Gardens, Op. 15.ogg
Format                       : OGG
File size                    : [COLOR="Red"]3.34 MiB[/COLOR]


---

### Post by logos34 on 2009-06-07
Also, does anyone know how to set output for quality?

> **-aq** *quality*

I tried every integer 1-12, but no rhyme or reason

it definitely needs an integer, because if you put in like V2, it complains:

> Expected number for aq but found: V2

---

### Post by mc4man on 2009-06-07
Mp3 encoding in ffmpeg is remedial at best, best to use lame instead. The -aq works but tends to screw up the runtime, varies in effect from player to player
Screen shows orig., -aq 6, -aq 2, -aq 0 in audacious (I believe the k is the avg, as reported by aud.
6= 64k vbr
2= 192k vbr
0= 224k vbk

Amarok is worse in regards to playtime, the lower the -aq the higher the runtime, -aq 0 shows 34 min. runtime !! (track still plays thru in 5 min.

If you need to use ffmpeg to decode I'd pipe to lame which you can use whatever lame options you wish.

Ex. from a folder to test folder in home, not recommending the command per se, just the method.to pipe "-" 

 > for f in *.ogg; do ffmpeg -i "$f" -f wav - | lame -V 2 -q 0 "-" ~/test/"${f%.wav}.mp3"; done

> doug@doug-desktop:~/vorbis/Ella Fitzgerald & Louis Armstrong (1958) Porgy & Bess#1$ for f in *.ogg; do ffmpeg -i "$f" -f wav - | lame -V 2 -q 0 "-" ~/test/"${f%.wav}.mp3"; done 
FFmpeg version SVN-r18890, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --libdir=${prefix}/lib --shlibdir=${prefix}/lib --bindir=${prefix}/bin --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-libamr-nb --enable-libamr-wb --enable-x11grab --enable-libgsm --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --enable-libopenjpeg --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.33. 0 / 52.33. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 31 2009 23:42:11, gcc: 4.3.2
Input #0, ogg, from '02 - Summertime.ogg':
  Duration: 00:04:58.22, start: 0.000000, bitrate: 212 kb/s
    Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 256 kb/s
Output #0, wav, to 'pipe:':
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   51377kB time=298.24 bitrate=1411.2kbits/s    
video:0kB audio:51377kB global headers:0kB muxing overhead 0.000084%
LAME 3.98.2 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), SSE (ASM used), SSE2
Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding <stdin> to /home/doug/test/02 - Summertime.ogg.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III VBR(q=2)

---

### Post by logos34 on 2009-06-07
ok, thanks.  You're a fount of useful tips 

strange though I couldn't find anbything googling for -aq ffmpeg

I hardly ever need to to do lossy-to-lossy conversion, but it would be nice to know it works like it's supposed to...and I was surprised I had any problems, since I'm using the latest svn ffmpeg + lame 3.98

any idea why it defaults to flac unless libvorbis is specified?

---

### Post by mc4man on 2009-06-07
> any idea why it defaults to flac unless libvorbis is specified? 
Not exactly sure but may have to do  with ogg being a (quote from wikipedia

> The name &#8216;Ogg&#8217; refers to the file format which can multiplex a number of separate independent free and open source codecs for audio, video, text (such as subtitles), and metadata.

In the Ogg multimedia framework, Theora provides a lossy video layer, while the music-oriented Vorbis codec most commonly acts as the audio layer. The human speech compression codec Speex, lossless audio compression codec FLAC, and OggPCM may also act as audio layers.
,,,,,,,,,,ect.



> strange though I couldn't find anbything googling for -aq ffmpeg

search lame vbr in ffmpeg and you'll find some older pages. I think it once was 'supported' but no longer, though it does work to some degree

[https://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-October/004628.html](https://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-October/004628.html)

no longer listed
[http://ffmpeg.org/ffmpeg-doc.html](http://ffmpeg.org/ffmpeg-doc.html)

---

### Post by andrew.46 on 2009-06-08
Hi logos,

> **logos34 said:**
> strange though I couldn't find anbything googling for -aq ffmpeg

The online help is not terribly *helpful*:

```

andrew@skamandros~$ ffmpeg -h | grep 'aq'
[...]
**[COLOR="Purple"]-aq quality         set audio quality (codec-specific)[/COLOR]**
naq                     E.V.. normalize adaptive quantization

```

Mind you my favourite FFmpeg page mentions the -aq option in passing and also gives an idea of the best options for ogg:

Using ffmpeg to manipulate audio and video files
[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

All the best,

Andrew

---

### Post by logos34 on 2009-06-08
> **andrew.46 said:**
> 
Using ffmpeg to manipulate audio and video files
[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)


yeah, saw that page ages ago...frustratingly brief audio section...60 on a scale of what? 100? But it doesn't work:
> 
$ ffmpeg -i CapaRezza\ -\ Hamebus\ Capa\ -\ 12\ -\ Tii-Yan.wma **-acodec libvorbis -aq 60** CapaRezza\ -\ Hamebus\ Capa\ -\ 12\ -\ Tii-Yan.ogg

...

Input #0, asf, from 'CapaRezza - Hamebus Capa - 12 - Tii-Yan.wma':
  Duration: 00:00:24.42, start: 1.580000, bitrate: 206 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, stereo, s16, 192 kb/s
Output #0, ogg, to 'CapaRezza - Hamebus Capa - 12 - Tii-Yan.ogg':
   ** Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, [COLOR="Red"]64 kb/s[/COLOR]**
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1331kB time=24.47 **[COLOR="Red"]bitrate= 445.4kbits/s[/COLOR]**    
video:0kB audio:1277kB global headers:4kB muxing overhead 3.851545%


> $ ogginfo CapaRezza\ -\ Hamebus\ Capa\ -\ 12\ -\ Tii-Yan.ogg 
Processing file "CapaRezza - Hamebus Capa - 12 - Tii-Yan.ogg"...

Note: Stream 1 has serial number 0, which is legal but may cause problems with some tools.
New logical stream (#1, serial: 00000000): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: AO; aoTuV b5 [20061024] (based on Xiph.Org's libVorbis)
Channels: 2
Rate: 44100

Nominal bitrate: 499.821000 kb/s
Upper bitrate not set
Lower bitrate not set
User comments section follows...
	encoder=Lavc52.29.0
Vorbis stream 1:
	Total data length: 1358502 bytes
	Playback length: 0m:24.473s
	Average bitrate: 444.066786 kb/s
Logical stream 1 ended

so in the end I get some kind of flac file! WTF?

(I even tried just -acodec **vorbis** but that really screws it up so ogginfo can't read it)

As far as oggs go, it seems as if -ab bitrate option is already producing a quality setting equal to the nominal (target bitrate):

this: 

> $ ffmpeg -i CapaRezza\ -\ Hamebus\ Capa\ -\ 12\ -\ Tii-Yan.wma **-acodec libvorbis [COLOR="Red"]-ab 192k[/COLOR]** CapaRezza\ -\ Hamebus\ Capa\ -\ 12\ -\ Tii-Yan.ogg

... 

Output #0, ogg, to 'CapaRezza - Hamebus Capa - 12 - Tii-Yan.ogg':
    Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=     611kB time=24.47 **[COLOR="Red"]bitrate= 204.4kbits/s[/COLOR]**    
video:0kB audio:574kB global headers:4kB muxing overhead 5.760112%

results in this:

> $ ogginfo CapaRezza\ -\ Hamebus\ Capa\ -\ 12\ -\ Tii-Yan.ogg Processing file "CapaRezza - Hamebus Capa - 12 - Tii-Yan.ogg"...

Note: Stream 1 has serial number 0, which is legal but may cause problems with some tools.
New logical stream (#1, serial: 00000000): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: AO; aoTuV b5 [20061024] (based on Xiph.Org's libVorbis)
Channels: 2
Rate: 44100
[B][COLOR="Red"]
Nominal bitrate: 192.000000 kb/s[/COLOR][/B]
Upper bitrate: 4294967.295000 kb/s
Lower bitrate: 4294967.295000 kb/s
User comments section follows...
	encoder=Lavc52.29.0
Vorbis stream 1:
	Total data length: 621518 bytes
	Playback length: 0m:24.473s
	[COLOR="Red"]**Average bitrate: 203.161645 kb/s**[/COLOR]
Logical stream 1 ended

---

### Post by mc4man on 2009-06-08
The -aq range would be 0 - 10, any number higher would be treated as 10.

to test cross compare with oggenc (be aware oggenc outputs filename in, filename out.ogg

Ex.
> doug@doug-laptop:~$ ffmpeg -i pro.wma -acodec libvorbis -aq 10 pro1.ogg
FFmpeg version SVN-r19087, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --libdir=${prefix}/lib --shlibdir=${prefix}/lib --bindir=${prefix}/bin --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-libamr-nb --enable-libamr-wb --enable-libgsm --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.30. 2 / 52.30. 2
  libavformat   52.34. 0 / 52.34. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jun  7 2009 05:25:00, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, asf, from 'pro.wma':
  Duration: 00:01:32.29, start: 1.451000, bitrate: 293 kb/s
    Stream #0.0(eng): Audio: wmapro, 48000 Hz, stereo, s16, 288 kb/s
Output #0, ogg, to 'pro1.ogg':
    Stream #0.0(eng): Audio: vorbis, 48000 Hz, stereo, s16, 64 kb/s  [COLOR="Red"]<- ignore[/COLOR]
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    3704kB time=92.00 bitrate= 329.8kbits/s   

> doug@doug-laptop:~$ oggenc pro.wav -q 10
Opening with wav module: WAV file reader
Encoding "pro.wav" to 
         "pro.ogg" 
at quality 10.00
	[ 99.2%] [ 0m00s remaining] - 

Done encoding file "pro.ogg"

	File length:  1m 33.0s
	Elapsed time: 0m 05.5s
	Rate:         16.9886
	Average bitrate: 310.7 kb/s


On the mp3 runtime length
same encoded to mp3 with ffmpeg (sox player

>  play -V4 test.mp3
play: SoX v14.2.0
time:  May  1 2009 19:24:41
issue: Ubuntu 8.04.2
uname: Linux doug-laptop 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686
gcc:   4.2.4 (Ubuntu 4.2.4-1ubuntu3)
arch:  1248 48 44 L
play mp3-duration: [COLOR="Blue"]got approx. duration by CBR extrapolation[/COLOR]

Input File     : 'test.mp3'
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Duration       : [COLOR="Blue"]00:10:42.78 = 30853440 samples ~ 48208.5 CDDA sectors[/COLOR]
Sample Encoding: MPEG audio (layer I, II or III)


Output File    : 'default' (alsa)
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Duration       : 00:10:42.78 = 30853440 samples ~ 48208.5 CDDA sectors
Sample Encoding: 16-bit Signed Integer PCM
Endian Type    : little
Reverse Nibbles: no
Reverse Bits   : no


Encoded by lame

> play -V4 test1.mp3
play: SoX v14.2.0
time:  May  1 2009 19:24:41
issue: Ubuntu 8.04.2
uname: Linux doug-laptop 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686
gcc:   4.2.4 (Ubuntu 4.2.4-1ubuntu3)
arch:  1248 48 44 L
[COLOR="Blue"]play mp3-duration: got exact duration from XING frame count (3902)[/COLOR]

Input File     : 'test1.mp3'
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Duration       : [COLOR="Blue"]00:01:33.65 = 4495104 samples ~ 7023.6 CDDA sectors[/COLOR]
Sample Encoding: MPEG audio (layer I, II or III)


Output File    : 'default' (alsa)
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Duration       : 00:01:33.65 = 4495104 samples ~ 7023.6 CDDA sectors
Sample Encoding: 16-bit Signed Integer PCM
Endian Type    : little
Reverse Nibbles: no
Reverse Bits   : no


---

### Post by andrew.46 on 2009-06-08
Hi logos,

Can I suggest another option that in my experience has been great for transcoding to ogg? I have been a big fan of transcode for some time:

```

andrew@skamandros~$ transcode --version
transcode v1.1.2 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team

```

and it can use oggenc as an *export* module and probably most usefully use MPlayer as an *import* module. Thus it can transcode such things as the [wmal file]("http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wma") we have all been tossing around for a while:

```

andrew@skamandros~/Desktop$ [B][COLOR="Purple"]transcode -H 0 -x null,mplayer -i luckynight.wma -y null,ogg \
>           -b 192 -E 44100,16,2 -o test.ogg [/COLOR][/B]
transcode v1.1.2 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | disabled
[transcode] V: bits/pixel       | 0.000 (unknown)
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: video format     | YUV420 (4:2:0) aka I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG ES Layer 3 [44100,16,2]  192 kbps
[transcode] V: export format    | unknown (module dependant)
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 sse2 sse mmx cmove asm 
[transcode] V: video buffer     | 10 @ 0x0 [0x2]
[transcode] A: audio buffer     | 10 @ 48000x2x16
[import_mplayer.so] v0.1.2 (2007-11-01) (video) rendered by mplayer | (audio) rendered by mplayer
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[export_ogg.so] v0.0.5 (2003-08-31) (video) null | (audio) ogg
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[import_mplayer.so] mplayer -slave -hardframedrop -vo null -ao pcm:nowaveheader:file="/tmp/mplayer2transcode-audio.VSw2oQ"  "luckynight.wma" > /dev/null 2>&1
[import_mplayer.so] tcextract -i /tmp/mplayer2transcode-audio.VSw2oQ -x pcm -t raw
[export_ogg.so] Writing audio to "/dev/null" (no -m option)
[export_ogg.so] oggenc -r -B 16 -C 2 -b 192 --resample 44100 -R 48000 -Q -o "test.ogg"  -
[export_ogg.so] Hint: Now merge the files with0:55,  ( 8| 0|12) 
[export_ogg.so] Hint: ogmmerge -o complete.ogg test.ogg test.ogg
[decoder.c] cancelling the import threads

[transcode] encoded 1386 frames (0 dropped, 0 cloned), clip length  55.44 s

```

This produces a very nice ogg vorbis file:

```

andrew@skamandros~/Desktop$ **[COLOR="Purple"]ogginfo test.ogg [/COLOR]**
Processing file "test.ogg"...

New logical stream (#1, serial: 35331451): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: Xiph.Org libVorbis I 20070622 (1.2.0)
Channels: 2
Rate: 44100

Nominal bitrate: 192.000000 kb/s
Upper bitrate not set
Lower bitrate not set
Vorbis stream 1:
	Total data length: 1201941 bytes
	Playback length: 0m:55.439s
	Average bitrate: 173.440260 kb/s
Logical stream 1 ended

```

But I will admit that Transcode is one of those applications that is not unfriendly, just a little picky about who it wants to make friends with :-).

Andrew

---

### Post by mc4man on 2009-06-08
Is the transcode command for 0.7 (or whatever is available for 8.04) much different than the 1.x one?

Only mentioning because as I recollect 1.x is a bit of work to build on 8.04 (and I get the feeling Logos needs a bit of a break in that regard

---

### Post by andrew.46 on 2009-06-08
Hi mc4man,

> **mc4man said:**
> Is the transcode command for 0.7 (or whatever is available for 8.04) much different than the 1.x one?

Hmmm.... I have a deep suspicion that version 1.x marked something of a break from the older series. So the commandline is probably different and I am not entirely sure when the MPlayer import module was created. Not a big problem for me as I only really started using transcode from version 1 and upwards :-).

> Only mentioning because as I recollect 1.x is a bit of work to build on 8.04 (and I get the feeling Logos needs a bit of a break in that regard

Oops you have caught me out there as I [cheated a little]("http://slackbuilds.org/repository/12.2/multimedia/transcode/") to compile transcode 1.1.2. I forget which distro I am using sometimes....

Andrew

---

### Post by mc4man on 2009-06-08
Actually doesn't look to difficult depending on what's enabled.
 By default almost nothing is. (and probably half the available options may not be used depending on ones usage.

Edit: built fine with a fair amount enabled, as long as you have a recent ffmpeg and x264
> Summary for transcode 1.1.2:
----------------------------------------

core options
----------------------------------------
enable experimental code       no
enable deprecated code         no
static AV-frame buffering      yes
A52 default decoder            yes
FFmpeg support                 yes

ffmpeg libraries
----------------------------------------
libavcodec  build              3415554
libavcodec  version            52.30.2
libavformat build              3416576
libavformat version            52.34.0

hardware support
----------------------------------------
v4l/v4l2                       yes
ALSA                           yes
OSS                            yes
bktr                           no
sunau                          no

optional module support
----------------------------------------
PV3                            no
NuppelVideo                    no

optional package support
----------------------------------------
IBP (libxio)                   no
X11                            yes
    Xv      extension          yes
    Xshm    extension          yes
    Xaw     library            yes
    Xpm     library            yes

libmpeg2                       yes
libpostproc                    yes
freetype2                      yes
lame                           yes
xvid                           yes
x264                           yes
ogg                            yes
vorbis                         yes
theora                         yes
libdvdread                     yes
pvm3                           no
libdv                          yes
libquicktime                   yes
lzo                            yes
a52                            yes
faac                           yes
libxml2                        yes
mjpegtools                     yes
sdl                            yes
imagemagick                    yes
libjpeg                        yes
bsdav                          no
iconv                          yes


Edit:
The default hardy is 1.02, as i remember now things changed after the **1.07** version,  when it went to 1.1.x

---

### Post by logos34 on 2009-06-08
I already use transcode for ripping dvd audio tracks.  Does a great job.

But I'd prefer ffmpeg for straight audio conversion--no piping, commands are succinct, etc. I really like it.  But now I'm sad because it's not working like it should. :(

It shouldn't put out false mp3 errors, or convert to flac when your output file suffix clearly has '.ogg' or one of the options like '-aq' is wrong, etc.  The first apparently was supposed to have been fixed by now, and I'm using svn ffmpeg.  A number of other apps call ffmpeg to do converting, so I need to sort this out for some peace of mind. I hate not knowing what is happening and why

---

### Post by logos34 on 2009-06-08
nope, I guessed wrong--the **-b *bitate* **ffmpeg option *is* giving a different rate than the **-aq **setting, which seems spot on variable/quality output.  

on same random file:

-acodec libvorbis -ab 160k = ~169kbps (Nominal bitrate: 160.000000 kb/s)
-acodec libvorbis -aq 5 = ~153kbps (Nominal bitrate: 160.000000 kb/s)

The **-aq** option takes (up to a point) the same quality settings numbers for argument as **oggenc** does, as mc4man suggested, i.e. **1-10** (or is it 12?).  But the **-b** option is NOT producing a CBR file, but rather something like am **ABR** file (since the rate is always slightly higher than nominal rate)--again, maybe following oggenc:

> **-b n, --bitrate=n **   
Sets  target  bitrate to n (in kb/s). The encoder will attempt to encode [COLOR="Red"]at approximately this bitrate[/COLOR]. By default, this remains a **VBR** encoding. See the --managed option to force a  managed bitrate encoding at the selected bitrate.

I'm also getting annoying error messages from ffmpeg with ogg output too, like:
> 
$ **ogginfo** 04\ -\ Vivaldi\ -\ The\ Four\ Seasons\ Winter\ -\ Largo.ogg 
Processing file "04 - Vivaldi - The Four Seasons Winter - Largo.ogg"...

Note: Stream 1 has serial number 0, which is legal but may cause problems with some tools.
New logical stream (#1, serial: 00000000): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: AO; aoTuV b5 [20061024] (based on Xiph.Org's libVorbis)
Channels: 2
Rate: 44100

Nominal bitrate: 160.000000 kb/s
Upper bitrate: 4294967.295000 kb/s
Lower bitrate: 4294967.295000 kb/s
User comments section follows...
	**encoder=Lavc52.29.0**
[COLOR="Red"]Negative or zero granulepos (0) on vorbis stream outside of headers. This file was created by a buggy encoder
Vorbis stream 1:[/COLOR]

...



I'm ignoring them for the time being.  can't be right

---

### Post by logos34 on 2009-06-08
Does anyone use anything other than -q settings with oggenc?

I use it strictly with quality option...Is it true that for CBR ogg, you have to specify three different parameters:

oggenc --max-bitrate=n --min-bitrate=n bitrate_average=n file.wav

> bitrate_average=N
              Set the average bitrate for the file to N bits per second.  When
              used without hard minimum or maximum limits, this option selects
              reservoirless Average  Bit  Rate  encoding,  where  the  encoder
              attempts  to  perfectly  track a desired bitrate, but imposes no
              strict momentary fluctuation limits.  When  used  along  with  a
              minimum  or  maximum  limit,  the average bitrate still sets the
              average overall bitrate of the file, but will  work  within  the
              bounds  set by the bit reservoir.  [COLOR="Blue"]When the min, max and average
              bitrates are identical, oggenc produces Constant Bit Rate Vorbis
              data.[/COLOR]


seems like a clumsy line for simple constant rate.  I have no need to use it, since I don't stream or anything, just wondering

---

### Post by mc4man on 2009-06-08
I think you could drive yourself nuts with this...

In regards to ffmpeg and it's -aq for the 2 formats in play here (mp3 and vorbis

The -aq seems to work fine and corresponds to the respective quality settings, -V 0-9 for lame and -q 1-10 for vorbis

Sometimes for mp3's the runtime is wrong, other times it's correct, sometimes it's correct in one player, wrong in an other or wrong with different runtimes in different players

Most likely for correct is a source of flac or ogg, most likely for incorrect is any wma and aac, but not always for any of them, a wav source goes either way, with a wav coming from a decompressed lossless following the above most times

The encodes themselves seem to fine in all cases, though lame seems to be the best choice for mp3 if additional options are desired or the runtime is wrong or wrong for chosen player

I haven't seen any of those errors you've posted

---

### Post by logos34 on 2009-06-09
> **mc4man said:**
> I think you could drive yourself nuts with this

LOL, I think I'm already there...


to hell with it, it's not all that important, I can find other ways to convert if need be, just wondering about these error messages and oddities with output format and options...although you're right, the quality setting does correspond to the respective codecs--I guess I was thrown by the initial erroneous bitrate (i.e. '64 k/bits', etc.), and the errors introduced additional uncertainty.

---

