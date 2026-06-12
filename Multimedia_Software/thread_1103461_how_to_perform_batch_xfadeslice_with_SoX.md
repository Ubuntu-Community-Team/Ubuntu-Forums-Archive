---
title: "how to perform batch xfade/slice with SoX???"
date: 2009-03-22
forum: Multimedia Software
---

### Post by logos34 on 2009-03-22
I'm trying use a bash script to perform crossfades on a bunch of .wav tracks with SoX following these instructions on the man page:

i.e.:
> **[COLOR="Red"]splice[/COLOR]**  { position[,excess[,leeway]] }
    Splice together audio sections. This effect provides two things over simple audio concatenation: a (usually short) cross-fade is applied at the join, and a wave similarity comparison is made to help determine the best place at which to make the join.

    To perform a splice, first use the trim effect to select the audio sections to be joined together. As when performing a tape splice, the end of the section to be spliced onto should be trimmed with a small excess (default 0.005 seconds) of audio after the ideal joining point. The beginning of the audio section to splice on should be trimmed with the same excess (before the ideal joining point), plus an additional leeway (default 0.005 seconds). SoX should then be invoked with the two audio sections as input files and the splice effect given with the position at which to perform the splice - this is length of the first audio section (including the excess).

    For example, a long song begins with two verses which start (as determined e.g. by using the play command with the trim (start) effect) at times 0:30.125 and 1:03.432. The following commands cut out the first verse:

            sox too-long.au part1.au trim 0 30.130

    (5 ms excess, after the first verse starts)

            sox long.au part2.au trim 1:03.422

    (5 ms excess plus 5 ms leeway, before the second verse starts)

            sox part1.au part2.au just-right.au splice 30.130

    Provided your arithmetic is good enough, multiple splices can be performed with a single splice invocation. For example:
[B]
    #!/bin/sh
    # Audio Copy and Paste Over
    # acpo infile copy-start copy-stop paste-over-start outfile
    # All times measured in samples.
    rate=`soxi -r "$1"`
    e=`expr $rate '*' 5 / 1000`  # Using default excess
    l=$e                         # and leeway.
    sox "$1" piece.au trim `expr $2 - $e - $l`s \
            `expr $3 - $2 + $e + $l + $e`s
    sox "$1" part1.au trim 0 `expr $4 + $e`s
    sox "$1" part2.au trim `expr $4 + $3 - $2 - $e - $l`s
    sox part1.au piece.au part2.au "$5" splice \
            `expr $4 + $e`s \
            `expr $4 + $e + $3 - $2 + $e + $l + $e`s[/B]

    In the above Bourne shell script, two splices are used to `copy and paste' audio.

    The SoX command

      play "|sox -n -p synth 1 sin %1" "|sox -n -p synth 1 sin %3"

    generates and plays two notes, but there is a nasty click at the transition; the click can be removed by appending splice 1 to the command. (Clicks at the beginning and end of the audio can be removed by preceding the splice effect with fade q .01 2 .01).
    *        	*        	*

    It is also possible to use this effect to perform general cross-fades, e.g. to join two songs. In this case, excess would typically be an number of seconds, and leeway should be set to zero. 

I just get this error:

> $ ~/./crossfade-sox.sh 
/home/user/./crossfade-sox.sh: 5: soxi: not found
expr: syntax error
expr: syntax error
expr: non-numeric argument
sox stio: Can't open input file `': No such file or directory
expr: syntax error
sox stio: Can't open input file `': No such file or directory
expr: non-numeric argument
sox stio: Can't open input file `': No such file or directory
expr: syntax error
expr: non-numeric argument
sox stio: Can't open input file `s': No such file or directory


Anyone know what the problem is?

---

### Post by loudness on 2009-03-23
Splice came in SoX 14.1; hardy has 14.0 -- I guess the man page you quoted is not the installed one.

There is a script here that you might be able to use (or knock into shape) though: 

[http://sox.cvs.sourceforge.net/viewvc/*checkout*/sox/sox/scripts/crossfade_cat.sh?revision=1.7](http://sox.cvs.sourceforge.net/viewvc/*checkout*/sox/sox/scripts/crossfade_cat.sh?revision=1.7)

HTH

---

### Post by logos34 on 2009-03-23
> **loudness said:**
> Splice came in SoX 14.1; hardy has 14.0 -- I guess the man page you quoted is not the installed one.

There is a script here that you might be able to use (or knock into shape) though: 

[http://sox.cvs.sourceforge.net/viewvc/*checkout*/sox/sox/scripts/crossfade_cat.sh?revision=1.7](http://sox.cvs.sourceforge.net/viewvc/*checkout*/sox/sox/scripts/crossfade_cat.sh?revision=1.7)

HTH

wow, I'm not even at 14.0:

> $ sox --version
sox: v13.0.0

Yet I should be using version 14.0.  Wonder what the deal is.  

(That's the online man page I quote, BTW).

Anyway, thanks for the tip--I'll install the latest and check out that script.!

---

### Post by logos34 on 2009-03-23
ok, dl'd the latest (14.2.0.tar.gz). But there's this at the end of ./configure:

> Debugging build................... no
External module support........... yes
ALSA driver....................... yes
libao driver...................... no
OSS driver........................ yes
SUN audio driver.................. no
CoreAudio driver.................. no
symlinks enabled.................. yes
play and rec symlinks............. yes
libgsm............................ in-tree
liblpc10.......................... in-tree
libsndfile formats................ no
Ogg Vorbis format................. yes
FLAC format....................... no
ffmpeg formats.................... no
magic library..................... no
MAD MP3 reader.................... no
id3tag library.................... no
LAME MP3 writer................... yes
AMR-WB format..................... no
AMR-NB format..................... no
WavPack format.................... no
LADSPA effects.................... yes
PNG support....................... yes
Secret Rabbit Code resampling..... no
pkg-config location............... $(libdir)/pkgconfig

Configure finished.  Do 'make && make install' to compile and install SoX.

But I want flac, ffmpeg. wavpack, mad, etc. etc. support included, so how do I enable  it?  I'm checking ./configure --help for options now...

---

### Post by logos34 on 2009-03-23
Nevermind, found it in --help:

i.e.:

> Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --without-libltdl       Don't try to use libltdl for external dynamic
                          library support
  --with-gnu-ld           assume the C compiler uses GNU ld [default=no]
  --with-pic              try to use only PIC/non-PIC objects [default=use
                          both]
  --with-tags[=TAGS]      include additional configurations [automatic]
  --with-pkgconfigdir     location to install .pc files or "no" to disable
                          (default=$(libdir)/pkgconfig)
  --without-sndfile       Don't try to use libsndfile
  --without-ogg           Don't try to use Ogg Vorbis
  --without-flac          Don't try to use FLAC
  --without-ffmpeg        Don't try to use ffmpeg
  --without-magic         Don't try to use magic
  --without-mad           Don't try to use MAD (MP3 Audio Decoder)
  --without-id3tag        Don't try to use id3tag
  --without-lame          Don't try to use LAME (LAME Ain't an MP3 Encoder)
  --without-amr-wb        Don't try to use amr-wb
  --without-amr-nb        Don't try to use amr-nb
  --without-wavpack       Don't try to use wavpack
  --without-png           Don't try to use png
  --without-samplerate    Don't try to use libsamplerate (aka Secret Rabbit
                          Code)
  --without-ladspa        Don't try to use LADSPA
  --with-ladspa-path      Default search path for LADSPA plugins

---

### Post by logos34 on 2009-03-23
Here is one of the reasons I hate compiling:


What I get with 

$ [COLOR="Blue"]./configure --with-flac --with-ffmpeg --with-mad --with-id3tag --with-wavpack
[/COLOR]
> checking FLAC/all.h usability... no
checking FLAC/all.h presence... no
checking for FLAC/all.h... no
configure: error: in `/home/user/downloads/sox-14.2.0':
[COLOR="Red"]configure: error: cannot find FLAC[/COLOR]
See `config.log' for more details.

Flac is installed -- /usr/bin/flac

Why???

UPDATE: heck I'd use the intrepid .deb pkg (14.1.0) but, alas, it won't install (dependency issues)

---

### Post by logos34 on 2009-03-23
UPDATE:

ok, so I try to run configure w/o flac, and still errors out:
> 
checking FLAC/all.h usability... no
checking FLAC/all.h presence... no
checking for FLAC/all.h... no
[COLOR="Red"]checking for FFMPEG... yes
checking libavformat/avformat.h usability... yes
checking libavformat/avformat.h presence... yes
checking for libavformat/avformat.h... yes
checking for av_open_input_file in -lavformat... no
configure: error: in `/home/user/downloads/sox-14.2.0':
configure: error: cannot find ffmpeg[/COLOR]
See `config.log' for more details.


WTF ???

---

### Post by mc4man on 2009-03-23
For flac install libflac-dev
what are you running (8.04 ?

you should be able to fill in as much as this as desired
> 
.................
Debugging build................... no
External module support........... yes
ALSA driver....................... yes
libao driver...................... yes
OSS driver........................ yes
SUN audio driver.................. no
CoreAudio driver.................. no
symlinks enabled.................. yes
play and rec symlinks............. yes
libgsm............................ external
liblpc10.......................... in-tree
libsndfile formats................ yes
Ogg Vorbis format................. yes
FLAC format....................... yes
ffmpeg formats.................... yes
magic library..................... yes
MAD MP3 reader.................... yes
id3tag library.................... yes
LAME MP3 writer................... yes
AMR-WB format..................... yes
AMR-NB format..................... yes
WavPack format.................... yes
LADSPA effects.................... yes
PNG support....................... yes
Secret Rabbit Code resampling..... yes
pkg-config location............... $(libdir)/pkgconfig

Configure finished.  Do 'make && make install' to compile and install SoX.


edit; you can get 14.0 straight up from repo

---

### Post by logos34 on 2009-03-23
> **mc4man said:**
> For flac install libflac-dev
what are you running (8.04 ?

you should be able to fill in as much as this as desired


edit; you can get 14.0 straight up from repo

thnx, mc4man, I'll try that.  Be back with the results in a bit...

It appears there's error in the version output...I have 14.0 even though it's saying "v13.0" for some reason.

---

### Post by logos34 on 2009-03-24
making some progress...

But now it's choking on ffmpeg..can't find it (despite the fact I just installed all the ffmpeg related -dev packages):

> checking whether to try building ALSA sound driver... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for snd_pcm_open in -lasound... yes
checking whether to try building libao sound driver... yes
checking ao/ao.h usability... no
checking ao/ao.h presence... no
checking for ao/ao.h... no
checking whether to try building OSS sound driver... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking whether to try building Sun audio driver... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking sun/audioio.h usability... no
checking sun/audioio.h presence... no
checking for sun/audioio.h... no
checking whether to try building CoreAudio driver... yes
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking whether to enable symlinks... yes
checking gsm/gsm.h usability... yes
checking gsm/gsm.h presence... yes
checking for gsm/gsm.h... yes
checking for gsm_create in -lgsm... yes
checking lpc10.h usability... no
checking lpc10.h presence... no
checking for lpc10.h... no
checking for lpc10.h... (cached) no
checking for create_lpc10_encoder_state in -llpc10... no
checking for SNDFILE... no
checking sndfile.h usability... no
checking sndfile.h presence... no
checking for sndfile.h... no
checking vorbis/codec.h usability... yes
checking vorbis/codec.h presence... yes
checking for vorbis/codec.h... yes
checking for ogg_packet_clear in -logg... yes
checking for vorbis_analysis_headerout in -lvorbis... yes
checking for ov_clear in -lvorbisfile... yes
checking for vorbis_encode_init_vbr in -lvorbisenc... yes
checking FLAC/all.h usability... yes
checking FLAC/all.h presence... yes
checking for FLAC/all.h... yes
checking for FLAC__stream_encoder_new in -lFLAC... yes
checking for FFMPEG... yes
checking libavformat/avformat.h usability... yes
checking libavformat/avformat.h presence... yes
checking for libavformat/avformat.h... yes
checking for av_open_input_file in -lavformat... no
configure: error: in `/home/user/downloads/sox-14.2.0':
[COLOR="Red"]configure: error: cannot find ffmpeg[/COLOR]
See `config.log' for more details.

Any ideas?

---

### Post by logos34 on 2009-03-24
maybe it has something to do with [this]("http://osdir.com/ml/audio.sox/2008-02/msg00039.html")

---

### Post by logos34 on 2009-03-24
a bit more progress to report but it's like dragging along a stubborn mule.  It now recognises ffmpeg after I put in this export path for the ffmpeg libs (libav*.pc stuff):
> 
$ [COLOR="Blue"]**export PKG_CONFIG_PATH=/usr/lib/pkgconfig**[/COLOR]
user@ubuntu:~/downloads/sox-14.2.0$ **auto-apt run ./configure --with-flac --with-ffmpeg --with-mad --with-id3tag --with-wavpack**
Entering auto-apt mode: ./configure --with-flac --with-ffmpeg --with-mad --with-id3tag --with-wavpack
Exit the command to leave auto-apt mode.

...

EDIT: Actually it had nothing to do with "export PKG_CONFIG_PATH" option...All I needed were the -dev pkgs for each codec (which still didn't prevent a 'make' error--see below)


> 
...

$ checking FLAC/all.h usability... yes
checking FLAC/all.h presence... yes
checking for FLAC/all.h... yes
checking for FLAC__stream_encoder_new in -lFLAC... yes
checking for FFMPEG... yes
checking libavformat/avformat.h usability... yes
checking libavformat/avformat.h presence... yes
checking for libavformat/avformat.h... yes
checking for av_open_input_file in -lavformat... yes
checking magic.h usability... no
checking magic.h presence... no
checking for magic.h... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
configure: error: in `/home/zazen/downloads/sox-14.2.0':
[COLOR="Red"]configure: error: cannot find libmad[/COLOR]
See `config.log' for more details.


But no go for mad...

---

### Post by loudness on 2009-03-24
In fact, if you use the script I linked to, you should be able to use the version of SoX you've already got installed, since the script doesn't use the splice effect, just things such as trim, fade, etc.

Also, cross-fades (of more than a couple of seconds) should ideally be constant power (quarter sine/cosine envelope); neither splice nor the script currently do this, but it's easy to change the script to do this (fade t becomes fade q; but be aware that constant power cross-fades can clip so you might want to create some headroom first, or just ignore the clipping if it still sounds okay during the fade.)

Hopefully, this should be an easier route than rebuilding everything...

---

### Post by logos34 on 2009-03-24
UPDATE:

If at first you don't succeed...

Turns out I need the -dev packages for each and every codec! 

> Debugging build................... no
External module support........... yes
ALSA driver....................... yes
libao driver...................... no
OSS driver........................ yes
SUN audio driver.................. no
CoreAudio driver.................. no
symlinks enabled.................. yes
play and rec symlinks............. yes
libgsm............................ external
liblpc10.......................... in-tree
libsndfile formats................ no
Ogg Vorbis format................. yes
FLAC format....................... yes
ffmpeg formats.................... yes
magic library..................... no
MAD MP3 reader.................... yes
id3tag library.................... yes
LAME MP3 writer................... yes
AMR-WB format..................... no
AMR-NB format..................... no
WavPack format.................... yes
LADSPA effects.................... yes
PNG support....................... yes
Secret Rabbit Code resampling..... no
pkg-config location............... $(libdir)/pkgconfig

Configure finished.  Do 'make && make install' to compile and install SoX.


Hope this is the ticket...jeez what a royal pain in the a**.  All to get the splice feature that I may end up hardly ever using!  (But when I get stuck on a problem I'm like a dog with his bone--won't let go till it's solved!)

UPDATE2: getting 'make' error...I've about had it --
> 
[COLOR="Red"]libtool: link: warning: `/usr/lib64/libltdl.la' seems to be moved
.libs/ffmpeg.o: In function `write_samples':
/home/user/downloads/sox-14.2.0/src/ffmpeg.c:419: undefined reference to `av_init_packet'
collect2: ld returned 1 exit status
make[2]: *** [libsox_fmt_ffmpeg.la] Error 1[/COLOR]
make[2]: Leaving directory `/home/user/downloads/sox-14.2.0/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/user/downloads/sox-14.2.0/src'
make: *** [all-recursive] Error 1

---

### Post by logos34 on 2009-03-24
> **loudness said:**
> In fact, if you use the script I linked to, you should be able to use the version of SoX you've already got installed, since the script doesn't use the splice effect, just things such as trim, fade, etc.

Also, cross-fades (of more than a couple of seconds) should ideally be constant power (usually half sine/cosine envelope); neither splice nor the script currently do this, but it's easy to change the script to do this (fade t becomes fade h; but be aware that constant power cross-fades can clip so you might want to create some headroom first, or just ignore the clipping if it still sounds okay during the fade.)

Hopefully, this should be an easier route than rebuilding everything...

just saw your post (duh)...so busy talking to myself I didn't notice.

ok, maybe I'll just go with the script you recommended and forget compiling (which is really becoming annoying).  thnx

---

### Post by mc4man on 2009-03-24
Your probably going to need to have a more current version of ffmpeg (can't say for sure because I have an up to date ver. (and am also currently trying sox 14.3

What you could do is follow the how to here and install ffmpeg to /usr/local

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

If so in the 'optional dependencies' section, if used, make sure to remove libmp3lame-dev from list (for hardy

you need an updated yasm (as shown

Why there usually isn't any need to build as shared, for sox you'll need to, you could check thru ./configure --help if something was omitted you want (something like this

.```
/configure --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-shared --enable-libvorbis 
  
```

You need to remove your current ffmpeg (you can leave existing libav*'s

If you do don't forget sudo ldconfig after installing



Otherwise you could try to configure sox with --without-ffmpeg

Install libsamplerate0-dev

---

### Post by logos34 on 2009-03-24
> **mc4man said:**
> Your probably going to need to have a more current version of ffmpeg ...

thnx.  normally I'd do it just for an exercise in problem-solving, but I'm just not up to it today.  I'll try the script for now.

---

### Post by logos34 on 2009-03-24
> **loudness said:**
> In fact, if you use the script I linked to...

ok, here's the error I get:
> 
$ ~/**./crossfade_cat.sh [COLOR="Red"]1[/COLOR] 01\ -\ U2\ -\ Gloria.wav 02\ -\ U2\ -\ 11\ O\'Clock\ Tick\ Tock.wav [COLOR="Red"]no yes[/COLOR]**
crossfade and concatenate files

Finding length of 01 - U2 - Gloria.wav...
Length is  seconds
Obtaining 1 seconds of fade out portion from 01 - U2 - Gloria.wav...
/home/user/./crossfade_cat.sh: line 75: ../src/sox: No such file or directory
/home/user/./crossfade_cat.sh: line 93: ../src/sox: No such file or directory
Obtaining 1 seconds of fade in portion from 02 - U2 - 11 O'Clock Tick Tock.wav...
/home/user/./crossfade_cat.sh: line 97: ../src/sox: No such file or directory
/home/user/./crossfade_cat.sh: line 111: ../src/sox: No such file or directory
Crossfading...
/home/user/./crossfade_cat.sh: line 115: ../src/sox: No such file or directory
Trimming off crossfade sections from original files...
/home/user/./crossfade_cat.sh: line 119: ../src/sox: No such file or directory
/home/user/./crossfade_cat.sh: line 120: ../src/sox: No such file or directory
/home/user/./crossfade_cat.sh: line 121: ../src/sox: No such file or directory
Removing temporary files...

rm: cannot remove `fadeout1.wav': No such file or directory
rm: cannot remove `fadeout2.wav': No such file or directory
rm: cannot remove `fadein1.wav': No such file or directory
rm: cannot remove `fadein2.wav': No such file or directory
rm: cannot remove `crossfade.wav': No such file or directory
rm: cannot remove `song1.wav': No such file or directory
rm: cannot remove `song2.wav': No such file or directory
The crossfade in mix.wav occurs at around 0 mins -1 secs


any ideas?

---

### Post by logos34 on 2009-03-24
nm--I got it...had to change $SOX path on line 30 from '../src/sox' to just 'sox' (i.e. '/usr/bin/sox')

---

### Post by logos34 on 2009-03-24
it works fine--for only two (wav) files at a time.  

Anyone know of a script to *batch* process *.mp3s*?  Like this:

[http://www.st4ck.com/projects/posts-crossfade](http://www.st4ck.com/projects/posts-crossfade)

but one that actually *works*? It's choking when it calls mplayer...can't figure out the problem is
> 
$ ~/./cdcreate.pl 1
[COLOR="Red"]Conversione di "01 - Gloria.mp3" in 1.wavmplayer: could not connect to socket
mplayer: No such file or directory[/COLOR]

---

### Post by logos34 on 2009-03-24
edit: spoke too soon...

---

