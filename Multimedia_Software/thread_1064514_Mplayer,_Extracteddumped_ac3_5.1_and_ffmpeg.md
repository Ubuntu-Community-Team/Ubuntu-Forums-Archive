---
title: "Mplayer, Extracted/dumped ac3 5.1 and ffmpeg"
date: 2009-02-08
forum: Multimedia Software
---

### Post by mc4man on 2009-02-08
I sometimes like to extract (in wine) or dump (with mplayer) individual ac3 5.1 music tracks . I just noticed that while a recent mplayer can dump the ac3, it can't play it back. (neither can vlc 0.9.x, though xine based players can along with the intrepid repo version of mplayer

This is only 5.1 448k tracks, 5.1 384k  and all 2.1 are fine. I'm fairly sure it's not me, tried with my own mplayer build method, Andrew's way, the smplayer package and  Sherpya, Lord Mulder builds for windows. (same result

i figure some libav* is involved because it affects both mplayer and vlc.

What's odd then is simply doing a straight re- encode (no changes) in a recent ffmpeg fixes them for both mplayer and vlc.

I was wondering if anybody who was up on the ffmpeg or mplayer mailing lists has seen any mention?
Or if the few who may also do this, ffmpeg will fix them just fine.
some logs for curious

 mplayer dump 
> doug@doug-desktop:~$ mplayer -vc null -vo null -aid 129 -dumpaudio -dvd-device /dev/dvd1 dvd://2 -chapter 3-3
MPlayer SVN-r28450-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://2.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 4 titles on this DVD.
There are 1 angles in this DVD title.
clipped...................
audio stream: 0 format: lpcm (stereo) language: en aid: 160.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
number of audio channels on disk: 2.
number of subtitles on disk: 0
MPEG-PS file format detected.
Core dumped ;)

Exiting... (End of file)

Mplayer playback of dump
> 
doug@doug-desktop:~$ mplayer -ao alsa -channels 6 ~/stream.ac3
MPlayer SVN-r28450-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/stream.ac3.
Exiting... (End of file)


ffmpeg re encode

> doug@doug-desktop:~/Desktop/test2$ ~/fixac3
FFmpeg version SVN-r16844, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags=-Wall -g -fPIC -DPIC --cc=ccache cc --libdir=${prefix}/lib --shlibdir=${prefix}/lib --bindir=${prefix}/bin --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-libamr-nb --enable-libamr-wb --enable-x11grab --enable-libgsm --enable-libx264 --enable-libtheora --enable-swscale --enable-libdc1394 --enable-nonfree --disable-mmx --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger  --enable-libspeex --enable-avfilter-lavf --enable-xvmc --enable-vdpau --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.11. 0 / 52.11. 0
  libavformat   52.25. 0 / 52.25. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 3. 0 /  0. 3. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 28 2009 15:22:30, gcc: 4.3.3
Input #0, ac3, from 'stream.ac3':
  Duration: 00:05:51.36, bitrate: 448 kb/s
    Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Output #0, ac3, to './temp/stream.ac3':
    Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[ac3 @ 0x9c0f1f0]frame sync error
Error while decoding stream #0.0
[ac3 @ 0x9c0f1f0]incomplete framete= 448.0kbits/s    
[ac3 @ 0x9c0f1f0]invalid frame size
size=   19215kB time=351.36 bitrate= 448.0kbits/s    
video:0kB audio:19215kB global headers:0kB muxing overhead 0.000000%


Mplayer after fix
> 
doug@doug-desktop:~$ mplayer -ao alsa -channels 6 ~/test2/stream.ac3
MPlayer SVN-r28450-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/test2/stream.ac3.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 6 ch, s16le, 448.0 kbit/9.72% (ratio: 56000->576000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 6ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  20.9 (20.9) of 351.4 (05:51.3)  1.1% 
Exiting... (Quit)


The error in vlc before fixing is the pop up about doesn't support mlp streams

---

### Post by FakeOutdoorsman on 2009-02-09
What is your FFmpeg command?

---

### Post by mc4man on 2009-02-09
> What is your FFmpeg command
it's actually in a batch script I wrote, the equivalent from cli would be 
> ffmpeg -i foo.ac3 -ab 448k foo2.ac3

The encoding line in the script is

```
for f in *.ac3; do ffmpeg -i "$f" -ab 448k  ./temp/"${f%}"; done
```

It always reports 1 sync error from mplayer dumps


 Extracted ac3. (won't play ,ect. again will play fine after ffmpeg re-encode

> Input #0, ac3, from 'Title2 - Chapter 03.ac3':
  Duration: 00:05:51.32, bitrate: 448 kb/s
    Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Output #0, ac3, to './temp/Title2 - Chapter 03.ac3':
    Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[ac3 @ 0x8b61200]frame sync error
Error while decoding stream #0.0
[ac3 @ 0x8b61200]incomplete framete= 448.0kbits/s    
[ac3 @ 0x8b61200]invalid frame size
size=   19213kB time=351.33 bitrate= 448.0kbits/s    
video:0kB audio:19213kB global headers:0kB muxing overhead 0.000000%

edit:
Generally the resultant .ac3 is about 200 - 300 bytes bigger than the dumped/ extracted one. (had to bring 'unfixed' track to windows to get filesize, properties of 'unfixed' is impossible in 8.10

same track
dumped by mplayer - 19,674,144 bytes
extracted in wine - 19,674,144 bytes

extracted in xp - 19,674,144 bytes
run thru ffmpeg - 19,674,368 bytes

none of the 144 ones play in mplayer, vlc in 8.10, vlc in vista
the 368 one does and is fine start to finish

all of them play in xine based, vlc 0.9.8a in xp, powerdvd in xp,vista

---

### Post by andrew.46 on 2009-02-10
Hi,

Curious. I have noted a few errors with dumping and MPlayer to the extent that I no longer use MPlayer for this. I tried to duplicate the problem that you have mentioned as follows:

Extracted ac3 sound stream from the Matrix with:

```
 mplayer -vc null -vo null -aid 128 -dumpaudio dvd://1 -chapter 1-1
```

FFmpeg identified this file as:

```
Input #0, ac3, from 'stream.dump':
Duration: 00:03:51.78, bitrate: 384 kb/s
Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
```

and FFplay played the sound with no problem but as you suggested MPlayer would not play the file at all. I ran FFmpeg across the file as you did:

```
ffmpeg -i stream.dump -ab 384k test.ac3
```

This produced a fle that *was* playable by MPlayer:

```
Input #0, ac3, from 'test.ac3':
Duration: 00:03:51.80, bitrate: 384 kb/s
Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
```

and generated the same error messages that you noted:

```
[ac3 @ 0x806fdb0]incomplete framete= 384.0kbits/s    
[ac3 @ 0x806fdb0]invalid frame size
```

So I can confirm your findings *completely*, there seems to be an error in the manner that MPlayer extracts audio from DVDs. Are you keen enough to present this error to MPlayer-users?

I personally have shifted to tccat for extracting whole titles/chapters from DVD and then either tcextract or FFmpeg to pull out streams. But transcode is a little user-unfriendly even to my tastes :-).

Andrew

---

### Post by mc4man on 2009-02-10
> So I can confirm your findings completely, there seems to be an error in the manner that MPlayer extracts audio from DVDs. Are you keen enough to present this error to MPlayer-users?

I think I'm going to try to set up a logical test/compare of this, there are some things i can't wrap my head around yet.
While i could of been a bit more verbose in the edit of my previous post, if you glance at what's there it somewhat points to the playback side not the dump and or extract side.
Plus it just now occurred to me to throw ffplay into the mix. (ATM I don't have any 'unfixed" .ac3 to test with

Because it came up in a post earlier (dumping the audio from a main menu ), I broke out something I hadn't used in a while, DGIndex.
Demuxing a 6 ch .ac3 with it shows the exact same behavior, ala no playback, then in ffmpeg
> Input #0, ac3, from 'VTS_01_1 T80 3_2ch 448Kbps DELAY 0ms.ac3':
  Duration: 00:16:44.98, bitrate: 448 kb/s
    Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Output #0, ac3, to './temp/VTS_01_1 T80 3_2ch 448Kbps DELAY 0ms.ac3':
    Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[ac3 @ 0x85ac210]incomplete framete= 448.0kbits/s    
[ac3 @ 0x85ac210]invalid frame size
size=   54960kB time=1004.99 bitrate= 448.0kbits/s    

 

Before I reaized the 'fixed' files were being added to byte wise I thought maybe this was somehow related to the .wav thing that came up in 8.10. (fairly sure it's not an 8.10 specific thing now

If you wanted to ck. that out pop in an audio cd, browse the folder and drag a track to the desktop. It will not play in gstreamer apps, though it will in everything else.

If you run it thru sox (.wav in .wav out) 70 bytes are removed and it becomes playable....?


Edit : just noticed you already tried ffplay and it plays fine, will have to try on a 448k file also

---

### Post by andrew.46 on 2009-02-14
Hi,

Don't know if this will help but I am putting a web page together on encoding a movie with transcode / MPlayer / FFmpeg etc and I have finally cracked the best method of 'surgically' removing an ac3 track using Transcode 1.1.0. Perhaps this could be involved in your cogitations?

```

tccat -i /dev/dvd -T 1,-1 | \
tcdemux -x ac3 -A 0x80 > $HOME/Desktop/matrix.ac3

```

Of course this pipes the extracted Title 1 + chapters to tcdemux which looks for ac3 files only and then only the audio stream 0x80 and creates matrix.ac3.

Any use? The ac3 file plays with everything and subsequently transcodes cleanly.

Andrew

---

### Post by mc4man on 2009-02-14
Andrew, that sounds good, just installed 1.10 on Intrepid, will ck. out tommorrow (very late here
When your new page is done I'm assuming a link at the corner?

(A quick look at transcode -h | more, it seems some things have changed from 0.7, your new page will prove very useful i'm sure

---

### Post by andrew.46 on 2009-02-14
Hi mc4man,

> **mc4man said:**
> Andrew, that sounds good, just installed 1.10 on Intrepid, will ck. out tommorrow (very late here
When your new page is done I'm assuming a link at the corner?

Well I really need to weigh things up a little I suspect. Web site, Ubuntu Forums, Slackware commitments + the 'real' world ....... but the bones of the page are in place.

> (A quick look at transcode -h | more, it seems some things have changed from 0.7, your new page will prove very useful i'm sure

Lucky for me I am learning Transcode with this new version so nothing to unlearn :-).

Andrew

---

### Post by mc4man on 2009-02-14
Andrew
This format doesn't work here, at least when using different values
> tccat -i /dev/dvd -T 1,-1

Ex.

> tccat -i /dev/dvd -T 2,-3 | tcdemux -x ac3 -A 0x81 > $HOME/Desktop/track3.ac3


doesn't work

> tccat -i /dev/dvd -T 2,3 | tcdemux -x ac3 -A 0x81 > $HOME/Desktop/track3.ac3


works great!

Edit: using transcode 1.1.0 (on 8.10

---

### Post by andrew.46 on 2009-02-14
Hi,

The -1 should simply pick up *all* of the chapters in that particular title:

>  -T  t[,c[,a]]
           select DVD title[,chapter[,angle]] [1,1,1]. Only a single chapter
           is transcoded. Use -T 1,-1 to trancode all chapters in a row. You
           can even specify chapter ranges.

But sounds like you have it working anyway by *specifying* a chapter. I almost fell out of my chair when I saw how easy this was to pipe to MPlayer. Using your example:

```
tccat -i /dev/dvd -T 2,3 | tcdemux -x ac3 -A 0x81 | mplayer -
```

How cool is that!

Andrew

---

### Post by mc4man on 2009-02-14
My mistake, I thought you were only doing chapter 1.

Anyway works great, gonna forget about the whole mplayer dump / ffmeg mess. (I think the issue lies more with ffmpeg in mplayer on playback.

What sealed that deal is if you take the the transcode demux (which plays fine in mplayer) and run it thru ffmpeg - it reports the same error as is seen with the mplayer dumps!

If you process it it removes bytes vs. adding in mplayer dumps

---

### Post by andrew.46 on 2009-02-14
Hi,

> **mc4man said:**
> My mistake, I thought you were only doing chapter 1.

Oops my apologies for as usual being less than clear :-).

> Anyway works great, gonna forget about the whole mplayer dump / ffmeg mess. (I think the issue lies more with ffmpeg in mplayer on playback.

I have abandoned dumpstream / vobcopy etc myself for extracting information from dvds. But I definitely need a little more time with the transcode man pages, information online (web) seems either non-existent or just plain wrong.

FFmpeg development is running white-hot at the moment, it will be interesting to revisit the issue after the upcoming release of MPlayer/FFmpeg? Can't remember the exact date but it is soon.

Andrew

---

