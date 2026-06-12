---
title: "Need help extracting audio from DVD"
date: 2009-01-02
forum: Multimedia Software
---

### Post by transmition on 2009-01-02
Hello, I seem to be having difficulty extracting audio from a DVD.
I am using the command:

```

transcode -i /dev/dvd -x null,dvd -T 1,-1 -N 0×55 -y null,raw -m audio.mp3

```

and while no errors are produced during transcoding, I do not seem to be produced with an audio file. In addition I do not think that any data is actually being written as:

```

df /

```

doesn't show a decrease in space during the transcoding process. 
When I try and search for the file, using:

```

find -name "audio.mp3"
or
locate audio.mp3

```

nothing comes up. Does anyone have any advice?

---

### Post by mc4man on 2009-01-03
I was fooling around a ways back with transcode till I realized a prog T had from a few yrs. ago worked in wine. (and is honestly superior to transcode.

Any way looking thru one of my histories I see this for mp3 (was mainly trying ac3 and .wav (obviously red is to be changed

```
transcode -i /dev/dvd -x dvd -T [COLOR="Red"]2,3[/COLOR] -a 0 -y raw -m track[COLOR="Red"]3[/COLOR].mp3
```

Edit; I also see this (using a preset, you could use one other than 'insane'

```
transcode -i /dev/dvd -x dvd -T 2,3 -a 0 -y raw --lame_preset insane -m track3.mp3
```

---

### Post by logos34 on 2009-01-03
Here's about as far as I got with transcode and .mp3:

transcode -i /dev/dvd -x dvd -T 1,12,1 -E 44100 -a 0 -y null,lame -m audiotrack

but all I get is audiotrack.mp3 @ CBR 128 kbps.

I wish I knew how to get -V2 vbr-new

---

### Post by transmition on 2009-01-03
It only seems to encode at 128 kb/s...

---

### Post by mc4man on 2009-01-03
Most of the available presets work (lame --preset help
insane = 320 cbr
the rest are vbr
this also works
```
transcode -i /dev/dvd -x null,dvd -T 1,3 -a 0 -y raw --lame_preset [COLOR="Red"]256[/COLOR] -m track6.mp3
```


As far as ... with or with a prepended preset
> (aud_aux.c) Error: Lame preset `V2' not supported. Falling back defaults.


This also works for cbr

```
transcode -i /dev/dvd -x null,dvd -T 1,3 -a 0 -y raw [COLOR="Red"]-b [/COLOR][COLOR="Red"]256 [/COLOR]-m track33.mp3
```


A couple of scripts I just saw, could be interesting, 3 on the page

[http://ubuntuforums.org/showthread.php?t=330856&page=2](http://ubuntuforums.org/showthread.php?t=330856&page=2)

---

### Post by WildeBeest on 2009-01-03
I need some help also extracting audio tracks from a DVD,

I have tried all the above commands and from the link mc4man posted.

The output I get is a 0 byte file:

This is the terminal output.

```
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
(dvd_reader.c) DVD title 2/2: 20 chapter(s), 1 angle(s), title set 2
(dvd_reader.c) title playback time: 01:58:10.15  7091 sec
(dvd_reader.c) [Chapter 01] 00:00:00.000 , block from 0 to 75487
(dvd_reader.c) [Chapter 02] 00:03:42.200 , block from 75488 to 205556
(dvd_reader.c) [Chapter 03] 00:10:10.900 , block from 205557 to 298655
(dvd_reader.c) [Chapter 04] 00:14:59.000 , block from 298656 to 375782
(dvd_reader.c) [Chapter 05] 00:18:48.800 , block from 375783 to 463958
(dvd_reader.c) [Chapter 06] 00:23:14.900 , block from 463959 to 531005
(dvd_reader.c) [Chapter 07] 00:26:35.100 , block from 531006 to 659621
(dvd_reader.c) [Chapter 08] 00:32:56.000 , block from 659622 to 730937
(dvd_reader.c) [Chapter 09] 00:36:40.400 , block from 730938 to 888896
(dvd_reader.c) [Chapter 10] 00:44:28.600 , block from 888897 to 972075
(dvd_reader.c) [Chapter 11] 00:48:29.200 , block from 972076 to 1083196
(dvd_reader.c) [Chapter 12] 00:54:05.900 , block from 1083197 to 1152602
(dvd_reader.c) [Chapter 13] 01:03:37.700 , block from 1152603 to 1271335
(dvd_reader.c) [Chapter 14] 01:08:25.100 , block from 1271336 to 1359826
(dvd_reader.c) [Chapter 15] 01:20:00.700 , block from 1359827 to 1584441
(dvd_reader.c) [Chapter 16] 01:30:42.800 , block from 1584442 to 1784008
(dvd_reader.c) [Chapter 17] 01:34:42.100 , block from 1784009 to 1861471
(dvd_reader.c) [Chapter 18] 01:40:31.200 , block from 1861472 to 1968668
(dvd_reader.c) [Chapter 19] 01:49:30.300 , block from 1968669 to 2140468
(dvd_reader.c) [Chapter 20] 01:58:10.100 , block from 2140469 to 2306504
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /dev/dvd (ok)
[transcode] V: import format    | MPEG-2 DVD NTSC (V=dvd|A=dvd)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  encoded @ 4:3
[transcode] V: bits/pixel       | 0.217
[transcode] V: decoding fps,frc | 23.976,1
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x1000f unknown      [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 23.976,1
[transcode] A: language         | en
[transcode] A: bytes per frame  | 8008 (8008.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
tc_memcpy: using amd64 for memcpy
[transcode] V: video buffer     | 10 @ 720x480
[import_dvd.so] v0.4.0 (2003-10-02) (video) DVD | (audio) MPEG/AC3/PCM
[export_raw.so] v0.3.12 (2003-08-04) (video) * | (audio) MPEG/AC3/PCM
[import_dvd.so] 
[import_dvd.so] tccat -T 2,1,1 -i "/dev/dvd" -t dvd -d 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 2 -f 23.976024 -P /tmp/file5DUh19 -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
[import_dvd.so] delaying DVD access by 3 second(s)
...tc_memcpy: using amd64 for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: mmxext
Audio: using new version
Audio: using lame-3.97
[export_raw.so] codec=YV12, fps=23.976, width=720, height=480

clean up | frame threads | unload modules | cancel signal | internal threads | done
[transcode] encoded 0 frames (6654 dropped, 0 cloned), clip length   0.00 s

```

---

### Post by mc4man on 2009-01-03
Just so there's no confusion, no code lines posted can be copied verbatim, more for form.
Everything in red is/should be set, blue optional

```
transcode -i /dev/dvd -x null,dvd -T [COLOR="Red"]1,3[/COLOR] -a [COLOR="Red"]0[/COLOR] -y [COLOR="Blue"]null,[/COLOR]raw [COLOR="Red"]-b 256 [/COLOR]-m [COLOR="Red"]track33[/COLOR].mp3
```

```
transcode -i /dev/dvd -x null,dvd -T [COLOR="Red"]2,3[/COLOR] -a [COLOR="Red"]0[/COLOR] -y [COLOR="Blue"]null,[/COLOR]raw --lame_preset [COLOR="Red"]insane[/COLOR] -m [COLOR="Red"]track3[/COLOR].mp3

```

@ WildeBeest
do you have libdvdcss2 installed?

typical output

> doug@doug-desktop:~$ transcode -i /dev/dvd -x dvd -T 2,3 -a 1 -y raw -b 256 -m track3.mp3
transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Using libdvdcss version 1.2.10 for DVD access
..................clipped
[import_dvd.so] delaying DVD access by 3 second(s)
.libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
,.........................ect.




Edit: plus this doesn't look good, if you still have issues after libdvdcss2 post command used

> [transcode] A: import format    | 0x1000f unknown      [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps

Your also using an old version, don't know if that matters (1.0.2

---

### Post by WildeBeest on 2009-01-03
I do have libdvdcss2 as well as libdvdread3 installed.

Where do I get transcode version 1.0.7?
I was able to download the source for v1.0.6, but have no idea how to build it.

The output I had posted was from the command:  transcode -i /dev/dvd -x dvd -T 2,1 -a 0 -y raw --lame_preset 256 -m track1.mp3

With this command ( transcode -i /media/cdrom0 -x null,dvd -T 2,1,1 -a 0 -y null,raw -m track1.mp3), I get the following:

```
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
(dvd_reader.c) DVD title 2/2: 20 chapter(s), 1 angle(s), title set 2
(dvd_reader.c) title playback time: 01:58:10.15  7091 sec
(dvd_reader.c) [Chapter 01] 00:00:00.000 , block from 0 to 75487
(dvd_reader.c) [Chapter 02] 00:03:42.200 , block from 75488 to 205556
(dvd_reader.c) [Chapter 03] 00:10:10.900 , block from 205557 to 298655
(dvd_reader.c) [Chapter 04] 00:14:59.000 , block from 298656 to 375782
(dvd_reader.c) [Chapter 05] 00:18:48.800 , block from 375783 to 463958
(dvd_reader.c) [Chapter 06] 00:23:14.900 , block from 463959 to 531005
(dvd_reader.c) [Chapter 07] 00:26:35.100 , block from 531006 to 659621
(dvd_reader.c) [Chapter 08] 00:32:56.000 , block from 659622 to 730937
(dvd_reader.c) [Chapter 09] 00:36:40.400 , block from 730938 to 888896
(dvd_reader.c) [Chapter 10] 00:44:28.600 , block from 888897 to 972075
(dvd_reader.c) [Chapter 11] 00:48:29.200 , block from 972076 to 1083196
(dvd_reader.c) [Chapter 12] 00:54:05.900 , block from 1083197 to 1152602
(dvd_reader.c) [Chapter 13] 01:03:37.700 , block from 1152603 to 1271335
(dvd_reader.c) [Chapter 14] 01:08:25.100 , block from 1271336 to 1359826
(dvd_reader.c) [Chapter 15] 01:20:00.700 , block from 1359827 to 1584441
(dvd_reader.c) [Chapter 16] 01:30:42.800 , block from 1584442 to 1784008
(dvd_reader.c) [Chapter 17] 01:34:42.100 , block from 1784009 to 1861471
(dvd_reader.c) [Chapter 18] 01:40:31.200 , block from 1861472 to 1968668
(dvd_reader.c) [Chapter 19] 01:49:30.300 , block from 1968669 to 2140468
(dvd_reader.c) [Chapter 20] 01:58:10.100 , block from 2140469 to 2306504
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /media/cdrom0 (ok)
[transcode] V: import format    | MPEG-2 DVD NTSC (V=null|A=dvd)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | disabled
[transcode] V: bits/pixel       | 0.000 (unknown)
[transcode] V: decoding fps,frc | 23.976,1
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x1000f unknown      [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 23.976,1
[transcode] A: language         | en
[transcode] A: bytes per frame  | 8008 (8008.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
tc_memcpy: using amd64 for memcpy
[transcode] V: video buffer     | 10 @ 0x0
[import_dvd.so] v0.4.0 (2003-10-02) (video) DVD | (audio) MPEG/AC3/PCM
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[export_raw.so] v0.3.12 (2003-08-04) (video) * | (audio) MPEG/AC3/PCM
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[import_dvd.so] 
Audio: using new version
Audio: using lame-3.97

clean up | frame threads | unload modules | cancel signal | internal threads | done
[transcode] encoded 0 frames (0 dropped, 0 cloned), clip length   0.00 s

```

---

### Post by mc4man on 2009-01-03
Just tried 1.02 on another box - it doesn't give any indication of using libdvdread or libdvdcss so that's not an issue.

Here's the source page, site isn't working atm, isn't that hard to build but you may need a more recent ffmpeg than the repo 

[http://developer.berlios.de/project/showfiles.php?group_id=10094](http://developer.berlios.de/project/showfiles.php?group_id=10094)

Tried both your commands, worked fine, maybe a 64 bit thing? (red lines main diff.


......................................................................

It seems using null is better for time, more than twice as fast.

> 
Ex.
(256k cbr
doug@doug-desktop:~$ transcode -i /dev/dvd -x null,dvd -T 2,3 -a 0 -y null,raw -b 256 -m null1.mp3
transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Using libdvdcss version 1.2.10 for DVD access
(dvd_reader.c) DVD title 2/4: 41 chapter(s), 1 angle(s), title set 2
(dvd_reader.c) title playback time: 02:34:05.07  9246 sec
(dvd_reader.c) [Chapter 01] 00:00:00.000 , block from 0 to 8476
............clipped
(dvd_reader.c) [Chapter 41] 02:34:04.366 , block from 3921565 to 3921833
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /dev/dvd (ok)
[transcode] V: import format    | MPEG-2 DVD NTSC (V=null|A=dvd)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | disabled
[transcode] V: bits/pixel       | 0.000 (unknown)
[transcode] V: decoding fps,frc | 23.976,1
[transcode] V: Y'CbCr           | YV12/I420
[COLOR="Red"][transcode] A: import format    | 0x10001 LPCM         [48000,16,2][/COLOR]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  256 kbps
[transcode] V: encoding fps,frc | 23.976,1
[transcode] A: language         | en
[transcode] A: bytes per frame  | 8008 (8008.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
[transcode] V: IA32/AMD64 accel | using sse memcpy
[transcode] V: video buffer     | 10 @ 0x0
[import_dvd.so] v0.4.0 (2003-10-02) (video) DVD | (audio) MPEG/AC3/PCM
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[export_raw.so] v0.3.12 (2003-08-04) (video) * | (audio) MPEG/AC3/PCM
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[COLOR="Red"][import_dvd.so] tccat -T 2,3,1 -i "/dev/dvd" -t dvd -d 0   | tcdemux -a 0 -x pcm -S 0 -M 2 -d 0 | tcextract -t vob -x pcm -a 0 -d 0[/COLOR]
Audio: using new version
libdvdread: Using libdvdcss version 1.2.10 for DVD access
Audio: using lame-3.97

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013c
..........clipped
encoding frames [000000-008416], 293.09 fps, EMT: 0:05:51, ( 0| 0| 9) 
clean up | frame threads | unload modules | cancel signal | internal threads | done
[transcode] encoded 8417 frames (0 dropped, 0 cloned), clip length 351.06 s


256k cbr only null on video (slightly slower

> doug@doug-desktop:~$ transcode -i /dev/dvd -x null,dvd -T 2,3 -a 0 -y raw -b 256 -m null2.mp3
.......clipped
encoding frames [000000-008416], 288.32 fps, EMT: 0:05:51, ( 0| 0| 9) 
clean up | frame threads | unload modules | cancel signal | internal threads | done
[transcode] encoded 8417 frames (0 dropped, 0 cloned), clip length 351.06 s



---

### Post by WildeBeest on 2009-01-04
I'm attempting to build the 1.06 version of transcode. Not having much success.

Can you tell me how it's done or where to find the executable?

---

### Post by logos34 on 2009-01-04
actually, [1.0.7 is the latest stable release.]("http://www.transcoding.org/cgi-bin/transcode?Download") 

unzip it first:

tar xjvf transcode-1.0.7.tar.bz2

cd transcode-1.0.7.tar

According to [this page]("http://www.transcoding.org/cgi-bin/transcode?Building_Transcode"), looks like

./configure 
make
sudo make install

should do it.  You can also do what I do and use checkinstall to make a .deb pkg--easy to keep track of and uninstall if you need to:

auto-apt run ./configure
make 
sudo checkinstall

You should have all the dependencies.  Default options should work fine.

[http://www.transcoding.org/cgi-bin/transcode?General_Information](http://www.transcoding.org/cgi-bin/transcode?General_Information)

---

### Post by WildeBeest on 2009-01-04
I'll try that once I can download the 1.0.7 version. The server is down ATM.

Where do I find auto-apt?

I get the following error: bash: auto-apt: command not found

---

### Post by mc4man on 2009-01-05
I think the 1.07 may have been pulled or something, still isn't available, though 1.06 is from same site. It's pretty easy to build, depending on what you want enabled. 

What are you running, 8.10 or 8.04?
Asking because you should run an apt-get build-dep, makes life easy and should pull in most of the deps.

The problem on 8.10 is the build-deps will want liblame0, but 8.10 has switched to libmp3lame so build-deps will fail to install (and transcode runs fine with libmp3lame installed

I guess there's a way to force it or certainly to fill in manually.

if your on 8.04 run this and then we'll take it from there
```
sudo apt-get build-dep transcode
```

you should run a ./configure --help to see what's disabled by default (alot

side note on compiling on 8.10

All build-deps are now marked as auto installed and will immediately show up for autoremoval, and will be removed if you use aptitude.
That's ok unless you intend to to continue to build.

the way around that is to do this instead. Ex. mplayer

```
sudo apt-get build-dep mplayer -o APT::Get::Build-Dep-Automatic=false
```

My main setup is on 8.04 and will stay that way. On another machine I have 8.10 so I'm trying a little experiment.

Most of the AV libs and codecs are outdated in 8.10 and medibuntu is somewhat empty. So rather than build them I've just replaced all of them with ones from Christian Marillat's debian multimedia repo (sid- unstable)(all the libav's. ffmpeg, libx264, x264,ect. ect.

He also has a 1.07 transcode, installed it and it works fine in a quick test. 

I figure a couple of weeks to see if there are any unintended consequences, though everything works great ATM.

---

### Post by WildeBeest on 2009-01-05
I am running 8.04.

When I run "sudo apt-get build-deb transcode", I get "E: Invalid operation build-deb".

When I run ./configure 
I get:

ERROR: requirement failed: cannot link against libavcodec
libavcodec can be found in the following packages:
  FFmpeg  [http://www.ffmpeg.org/](http://www.ffmpeg.org/)

ERROR: option '--enable-lame' failed: cannot link against libmp3lame
libmp3lame can be found in the following packages:
  lame  [http://www.mp3dev.org/](http://www.mp3dev.org/)

ERROR: option '--enable-libdvdread' failed: cannot link against libdvdread
libdvdread can be found in the following packages:
  libdvdread  [http://www.dtek.chalmers.se/groups/dvd/downloads.shtml](http://www.dtek.chalmers.se/groups/dvd/downloads.shtml)

---

### Post by mc4man on 2009-01-05
@WildeBeest
I'm sorry. I usually re check posts, should have been build-dep, corrected

---

### Post by logos34 on 2009-01-05
> **WildeBeest said:**
> I'll try that once I can download the 1.0.7 version. The server is down ATM.

Where do I find auto-apt?

I get the following error: bash: auto-apt: command not found

forgot to include link:

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by logos34 on 2009-01-05
> **mc4man said:**
> 
The problem on 8.10 is the build-deps will want liblame0, but 8.10 has switched to libmp3lame so build-deps will fail to install (and transcode runs fine with libmp3lame installed

Interesting.  

> I guess there's a way to force it or certainly to fill in manually.

maybe

--with-lame-libs=/DIR/with/liblame0

lame option ??


> you should run a ./configure --help to see what's disabled by default (alot

yes, I noticed the vorbis and theora audio **import** was disabled by default, as shown [here]("http://www.transcoding.org/cgi-bin/transcode?Building_Transcode").  That doesn't affect ripping dvd audio (export) does it?  



> Most of the AV libs and codecs are outdated in 8.10 and medibuntu is somewhat empty. So rather than build them I've just replaced all of them with ones from Christian Marillat's debian multimedia repo (sid- unstable)(all the libav's. ffmpeg, libx264, x264,ect. ect.

He also has a 1.07 transcode, installed it and it works fine in a quick test. 

I figure a couple of weeks to see if there are any unintended consequences, though everything works great ATM.

hmm

---

### Post by WildeBeest on 2009-01-05
@logos34

When I use your procedure:

[I]auto-apt run ./configure
make
sudo checkinstall[/I]

for ffmpeg I get:
```
========================= Installation results ===========================
rm -f libavdevice/libavdevice.a
ar rc libavdevice/libavdevice.a libavdevice/alldevices.o libavdevice/dv1394.o libavdevice/audio.o libavdevice/v4l2.o libavdevice/v4l.o 
ranlib libavdevice/libavdevice.a
install -d "/usr/local/lib"
install -m 644 libavdevice/libavdevice.a "/usr/local/lib"
ranlib "/usr/local/lib/libavdevice.a"
gcc -shared -Wl,-soname,libavutil.so.49  -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/willy/Code/ffmpeg"/libpostproc -Wl,-rpath-link,"/home/willy/Code/ffmpeg"/libswscale -Wl,-rpath-link,"/home/willy/Code/ffmpeg"/libavfilter -Wl,-rpath-link,"/home/willy/Code/ffmpeg"/libavdevice -Wl,-rpath-link,"/home/willy/Code/ffmpeg"/libavformat -Wl,-rpath-link,"/home/willy/Code/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/willy/Code/ffmpeg"/libavutil -Wl,-Bsymbolic -o libavutil/libavutil.so.49 libavutil/adler32.o libavutil/aes.o libavutil/base64.o libavutil/crc.o libavutil/des.o libavutil/fifo.o libavutil/intfloat_readwrite.o libavutil/lfg.o libavutil/lls.o libavutil/log.o libavutil/lzo.o libavutil/mathematics.o libavutil/md5.o libavutil/mem.o libavutil/random.o libavutil/rational.o libavutil/rc4.o libavutil/sha1.o libavutil/string.o libavutil/tree.o libavutil/utils.o  -lz -lbz2 -pthread -lm    -ldl -ldl 
/usr/bin/ld: libavutil/lls.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
libavutil/lls.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libavutil/libavutil.so.49] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

@mc4man
I was finally able to download the 1.0.7 version of transcode, used your suggestion ```
sudo apt-get build-dep transcode
```

After the configure I still have this error. 

```
ERROR: requirement failed: cannot link against libavcodec
libavcodec can be found in the following packages:
  libavcodec  http://www.ffmpeg.org/

```

---

### Post by mc4man on 2009-01-05
> After the configure I still have this error. 
Rather than chase these deps back and forth I can probably give you a complete list in about an hr or so. 

If you haven't already, add medibuntu to your sources, you'll get better versions of some needed libs.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list


```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

As far as that error ck. and see if libavcodec-dev is installed


This is the configure I used (maybe overkill..??

Definitely  don't use the red, requires extra work for not much gained

./configure --prefix=/usr --enable-libmpeg3 --enable-text --enable-v4l --enable-libfame --disable-libfametest --enable-ogg --enable-mjpegtools --enable-lzo --enable-gtk --enable-imagemagick --enable-theora --enable-libquicktime --enable-libdv --enable-libxml2 --enable-vorbis --enable-a52 --enable-pvm3 --enable-netstream --enable-sdl --enable-freetype2 --enable-avifile --enable-a52-default-decoder [COLOR="Red"]--enable-libpostproc[/COLOR] --enable-libmpeg3 --enable-nuv --enable-oss [COLOR="Red"]--with-libavcodec-includes=/home/doug/ffmpeg --with-libpostproc-includes=/home/doug/ffmpeg --with-libpostproc-libs=/home/doug/ffmpeg[/COLOR]

That produces this, (we can eliminate what you don't need
> 
Summary for transcode 1.0.7:
----------------------------------------

core options
----------------------------------------
static AV-frame buffering      yes
network (sockets) streams      yes
NUV format support             yes
experimental xio               no
Default xvid export            xvid4
A52 default decoder            yes

libavcodec
----------------------------------------
headers                        -I/home/doug/ffmpeg
libraries                       -lavcodec -lavcodec -ltheora -lvorbisenc -lraw1394 -lavutil -lvorbis -lm -logg
build                          3408640
version                        52.3.0
statically linked              

hardware support
----------------------------------------
v4l/v4l2                       yes
OSS                            yes
bktr                           no
sunau                          no

optional package support
----------------------------------------
IBP                            no
X11                            yes
libmpeg2                       yes
libpostproc                    yes
freetype2                      yes
avifile                        yes
lame                           yes
ogg                            yes
vorbis                         yes
theora                         yes
libdvdread                     yes
pvm3                           yes
libdv                          yes
libquicktime                   yes
lzo                            yes
a52                            yes
libmpeg3                       yes
libxml2                        yes
mjpegtools                     yes
sdl                            yes
libfame                        yes
imagemagick                    yes
libjpeg                        yes
bsdav                          no
iconv                          yes


---

### Post by WildeBeest on 2009-01-05
Otherwise or in the meantime open up synaptic -> file -> history. In there you'll find listings of what you've installed. Find the one from the build-dep and it's easy to copy, paste and post

This it, doesn't look like anything from the build-dep
Commit Log for Mon Jan  5 16:01:14 2009


Upgraded the following packages:
libsensors4 (1:3.0.0-4ubuntu1) to 1:3.0.0-4ubuntu2
lm-sensors (1:3.0.0-4ubuntu1) to 1:3.0.0-4ubuntu2

If you haven't already, add medibuntu to your sources, you'll get better versions of some needed libs.

Already have.


As far as that error ck. and see if libavcodec-dev is installed. It is.


I tried the following command:
```
./configure --prefix=/usr --enable-text --enable-v4l --enable-libfame --disable-libfametest --enable-ogg --enable-mjpegtools --enable-lzo --enable-gtk --enable-imagemagick --enable-theora --enable-libquicktime --enable-libdv --enable-libxml2 --enable-vorbis --enable-a52 --enable-pvm3 --enable-netstream --enable-sdl --enable-freetype2 --enable-a52-default-decoder --enable-libpostproc --enable-nuv --enable-oss --with-libavcodec-includes=/home/willy/Code/ffmpeg --with-libpostproc-includes=/home/willy/Code/ffmpeg --with-libpostproc-libs=/home/willy/Code/ffmpeg

```

The result is the same. 

[COLOR="Red"]ERROR: requirement failed: cannot link against libavcodec
libavcodec can be found in the following packages:
  libavcodec  [http://www.ffmpeg.org/](http://www.ffmpeg.org/)[/COLOR]


I really appreciate you taking the time to get this working.

---

### Post by mc4man on 2009-01-05
It appears you can't build ver. 1.07 on hardy unless you get updated versions of ffmpeg and the libav*'s. 

In my case I had built a newer version of ffmpeg  but didn't install it. Linking to it in the configure allowed the build to work.

The current 8.04 ffmpeg and libav*'s are sufficient to build 1.06 thiough you do want to enable some things.

Otherwise there is a guide around to building and installing a new ffmpeg and x264 (installs to /usr/local/, or try what I did (right. wrong ..?

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)




You may find easier to just do 1.06

With a straight configure> 

Summary for transcode 1.0.6:
----------------------------------------

core options
----------------------------------------
static AV-frame buffering      yes
network (sockets) streams      no
NUV format support             yes
experimental xio               no
Default xvid export            xvid4
A52 default decoder            no

libavcodec
----------------------------------------
headers                        
libraries                      -L/usr/lib -lavcodec -lavcodec -ltheora -lvorbisenc -lraw1394 -lavutil -lvorbis -lm -logg
build                          3352064
version                        1d.51.38.0
statically linked              no

hardware support
----------------------------------------
v4l/v4l2                       no
OSS                            no
bktr                           no
sunau                          no

optional package support
----------------------------------------
IBP                            no
X11                            yes
libmpeg2                       yes
libpostproc                    no
freetype2                      no
avifile                        no
lame                           yes
ogg                            no
vorbis                         no
theora                         no
libdvdread                     yes
pvm3                           no
libdv                          no
libquicktime                   no
lzo                            no
a52                            no
libmpeg3                       no
libxml2                        no
mjpegtools                     no
sdl                            no
libfame                        no
imagemagick                    no
libjpeg                        yes
bsdav                          no
iconv                          yes


---

### Post by mc4man on 2009-01-05
If you want to build 1.06 then in addition to the build-deps install these. (some are probably not needed, it's hard to track down on my install which has several hundred -dev's

If you get a configure error on avifile then reboot once or twice or remove blue from the configure

At this point any errors will be easy to fix.

If you just want for mp3's then ./configure will probably be good.


```
sudo apt-get install libavifile-0.7-dev libxvidcore4-dev libfame-dev libmpeg2-4-dev mjpegtools libavahi-client-dev libavformat-dev libavahi-glib-dev libmpeg4ip-dev libmpeg3-dev libmp4v2-dev ffmpeg w32codecs libswscale-dev libdvdnav-dev libfame-dev liba52-0.7.4-dev libdvdcss2
```

```
./configure --prefix=/usr --enable-libmpeg3 --enable-text --enable-v4l --enable-libfame --disable-libfametest --enable-ogg --enable-mjpegtools  --enable-gtk --enable-imagemagick --enable-theora --enable-libquicktime --enable-libdv --enable-libxml2 --enable-vorbis --enable-a52 --enable-pvm3 --enable-netstream  --enable-freetype2  --enable-a52-default-decoder  --enable-libmpeg3 --enable-oss [COLOR="Blue"]--enable-avifile[/COLOR]
```

> I tried the following command

I probably should have been clearer, everything marked in red in that post you can't use unless you've built a new version of ffmpeg (in this case in home directory
Plus I'm not 100% sure that was the correct way, it just happened to be there for something else so I figured I'd use it. (as it turns out that's why I could build 1.07


> 
I really appreciate you taking the time to get this working.

!NYG!

---

### Post by andrew.46 on 2009-01-06
Hi,

I can see that you have your heart set on transcode but MPlayer can also easily extract audio from dvds. The classic way is to first identify which audio stream you want:

```
$ **[COLOR="Red"]mplayer dvd://1 -identify -frames 0 -vo null | grep -i 'audio stream'[/COLOR]**
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (stereo) language: en aid: 130.
```

and then extract the desired audio stream (aid 128 for example) as follows:

```
$ mplayer -aid 128 dvd://1 -vc null -vo null \
-ao pcm:fast:waveheader:file=output.wav
```

and finally encode output.wav to whichever format you wish. But I guess if you are keen on transcode you might want to stick with that.

All the best,

 Andrew

---

### Post by jocheem67 on 2009-01-06
I agree that mplayer, once you know the commands, is the most reliable tool to rip audio from a dvd....

However there's also the poss. to use fa vobcopy in combination with avidemux. Or even dvddecrypter with wine to create a wav.

---

### Post by logos34 on 2009-01-06
> **jocheem67 said:**
> I agree that mplayer, once you know the commands, is the most reliable tool to rip audio from a dvd....



Do you know if it's possible to rip straight to vbr .mp3 (like, say, -V2 --vbr-new), and if so, what is the command?  I can only get cbr in transcode

---

### Post by WildeBeest on 2009-01-06
@mc4man

I downloaded ffmpeg and x264 and followed the install procedure.
Everything went well.

I tried this and the output was that I already have the latest versions.

```
sudo apt-get install libavifile-0.7-dev libxvidcore4-dev libfame-dev libmpeg2-4-dev mjpegtools libavahi-client-dev libavformat-dev libavahi-glib-dev libmpeg4ip-dev libmpeg3-dev libmp4v2-dev ffmpeg w32codecs libswscale-dev libdvdnav-dev libfame-dev liba52-0.7.4-dev libdvdcss2
```


I run your configure( for v1.0.6)

```
./configure --prefix=/usr --enable-libmpeg3 --enable-text --enable-v4l --enable-libfame --disable-libfametest --enable-ogg --enable-mjpegtools  --enable-gtk --enable-imagemagick --enable-theora --enable-libquicktime --enable-libdv --enable-libxml2 --enable-vorbis --enable-a52 --enable-pvm3 --enable-netstream  --enable-freetype2  --enable-a52-default-decoder  --enable-libmpeg3 --enable-nuv --enable-oss [COLOR="Blue"]--enable-avifile[/COLOR]
```

and got

```
ERROR: option '--enable-avifile' failed: cannot compile avifile.h
avifile.h can be found in the following packages:
  avifile  http://avifile.sourceforge.net/

ERROR: option '--enable-avifile' failed: cannot link against libaviplay
libaviplay can be found in the following packages:
  avifile  http://avifile.sourceforge.net/

ERROR: option '--enable-libmpeg3' failed: cannot link against libmpeg3
libmpeg3 can be found in the following packages:
  libmpeg3  http://heroinewarrior.com/libmpeg3/


Please see the INSTALL file in the top directory of the
transcode sources for more information about building
transcode with this configure script.

```

What am I doing wrong? :(

---

### Post by WildeBeest on 2009-01-06
@Andrew.46

I tried your method with mplayer and got:

```
mplayer -aid 128 dvd://1 -vc null -vo null \
> -ao pcm:fast:waveheader:file=track.wav

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 6, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 2 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (stereo) language: en aid: 130.
number of audio channels on disk: 3.
number of subtitles on disk: 0
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  5000.0 kbps (625.0 kbyte/s)
==========================================================================
Forced video codec: null
Opening video decoder: [null] Null video decoder
VDec: vo config request - 720 x 480 (preferred colorspace: BGR 24-bit)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [null] 720x480 => 720x540 Planar YV12 
Selected video codec: [null] vfm: null (NULL codec (no decoding!))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO PCM] File: track.wav (WAVE)
PCM: Samplerate: 48000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   2.3 V:   2.0 A-V:  0.280 ct:  0.071  56/ 56  0%  0% 176.5% 51 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  11.3 V:  11.2 A-V:  0.088 ct:  0.119 331/331  0%  0% 34.2% 291 0 

Exiting... (End of file)

```

---

### Post by mc4man on 2009-01-06
You can always remove -enable-avifile from end of configure, you may not need it, the libmpeg3 I"m not sure. You have the needed -devs (libmpeg3-dev, libavifile-0.7-dev


Last night I quickly tried on another machine with a fresh hardy install and ran into same avifile problem, that's why I suggested removing it in prior post. (marked in blue
 I was able to get it found, not 100% sure how.( and I tried many things - most of what I did

 removing the 2 packages (4 in total for you) I just mentioned, then re installing

```
 sudo apt-get purge libmpeg3-1  libavifile-0.7c2

```
```
sudo apt-get install libmpeg3-dev libavifile-0.7-dev 
```

Then reboot

Cd to your build folder and run this, then try configure again

```
make distclean
```

I did all that and it still wouldn't link with libavi.... so I tried linking in the configure (no good)
In a little bit of frustration I installed build-deps for mplayer - still no good
Then I rebooted yet again and everything was fine.

If you can't get them found then remove both from the configure  and see what you have


Did you look in your home folder for track.wav? ( that error message with mplayer can be ignored in this use
..................

I did work out an easy way to do 1.07 in hardy, in any event you need the 1.06 configure to work

While transcode is faster using mplayer affords you more options to re encode.
That's pretty much what I use(d), though I'd do it in individual chapters or blocks of chapters
(for blocks use for ex. 2-4
Here's a thread on it with some add. info
[http://ubuntuforums.org/showthread.php?t=869258](http://ubuntuforums.org/showthread.php?t=869258)

---

### Post by andrew.46 on 2009-01-06
Hi WildeNeest,

> **WildeBeest said:**
> @Andrew.46

I tried your method with mplayer and got:

```

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************


```

Ignore this .... the output wave will still be generated.

Andrew

---

### Post by WildeBeest on 2009-01-06
The resultant wav file was 2MB in size and was only 11 seconds long with no audio.

I also tried aid 129 and 130, same thing.

---

### Post by WildeBeest on 2009-01-06
@mc4man

The configure command without the [COLOR="Blue"]avifile argument[/COLOR] worked fine:

```
----------------------------------------
Summary for transcode 1.0.6:
----------------------------------------

core options
----------------------------------------
static AV-frame buffering      yes
network (sockets) streams      yes
NUV format support             yes
experimental xio               no
Default xvid export            xvid4
A52 default decoder            yes

libavcodec
----------------------------------------
headers                        
libraries                      -L/usr/lib -lavcodec -L/usr/local/lib -lavcodec
build                          3410432
version                        52.10.0
statically linked              no

hardware support
----------------------------------------
v4l/v4l2                       yes
OSS                            yes
bktr                           no
sunau                          no

optional package support
----------------------------------------
IBP                            no
X11                            yes
libmpeg2                       yes
libpostproc                    no
freetype2                      yes
avifile                        no
lame                           yes
ogg                            yes
vorbis                         yes
theora                         yes
libdvdread                     yes
pvm3                           yes
libdv                          yes
libquicktime                   yes
lzo                            no
a52                            yes
libmpeg3                       yes
libxml2                        yes
mjpegtools                     yes
sdl                            no
libfame                        yes
imagemagick                    yes
libjpeg                        yes
bsdav                          no
iconv                          yes


```


The make command gives me these errors:

```
make[3]: *** [import_ffmpeg.lo] Error 1
make[3]: Leaving directory `/home/willy/Code/transcode-1.0.6/import'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/willy/Code/transcode-1.0.6/import'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/willy/Code/transcode-1.0.6'
make: *** [all] Error 2

```

sudo make install gives me these errors:

```
make[2]: *** [import_ffmpeg.lo] Error 1
make[2]: Leaving directory `/home/willy/Code/transcode-1.0.6/import'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/willy/Code/transcode-1.0.6/import'
make: *** [install-recursive] Error 1

```

The import directory has a file named "import_ffmpeg.loT" but not "import_ffmpeg.lo". Could this be the problem?

This is getting very frustrating.  :confused:

---

### Post by andrew.46 on 2009-01-07
Hi WildeBeest,

A little frustration creeping in for you I suspect, sorry i I have made it a little worse for you :(.

> **WildeBeest said:**
> The resultant wav file was 2MB in size and was only 11 seconds long with no audio.

I also tried aid 129 and 130, same thing.

Just in case there was a little weirdness in the copy and paste from the forum try this all on one line:

```
mplayer -aid 128 dvd://1 -vc null -vo null -ao pcm:fast:waveheader:file=track.wav
```

Just to be sure I was not talking rubbish I ran the full command myself on a DVD. The following shows a successful rip of a DVD audio track using the syntax I suggested. You will note that I am using the *svn* MPlayer but this should work with the older version you are using:

```
andrew@skamandros:~/Desktop$ mplayer -aid 128 dvd://1 -vc null -vo null -ao pcm:fast:waveheader:file=track.wav
MPlayer dev-SVN-r28239-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing dvd://1.
There are 17 titles on this DVD.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (stereo) language: en aid: 130.
number of audio channels on disk: 3.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Forced video codec: null
Opening video decoder: [null] Null video decoder
VDec: vo config request - 720 x 576 (preferred colorspace: BGR 24-bit)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [null] 720x576 => 1024x576 Planar YV12 
Selected video codec: [null] vfm: null (NULL codec (no decoding!))
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO PCM] File: track.wav (WAVE)
PCM: Samplerate: 48000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   2.5 V:   2.2 A-V:  0.293 ct:  0.103  56/ 56  0%  0%  1.1% 50 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:6974.8 V:6974.7 A-V:  0.108 ct:  0.139 174370/174370  0%  0% 12.1% 153926 0 

Exiting... (End of file)
andrew@skamandros:~/Desktop$ 
```

All the best,

Andrew

---

### Post by mc4man on 2009-01-07
hopefully you got mplayer going, plus since in this case your extracting the stream as one track may prove easier.

If you want to get transcode resolved 2 things. First don't run a make install till you get a successful make.

Actually you should use the checkinstall command instead. (will give you a .deb and easy way to install or upgrade

So after a make error, while not always needed, you should at the build prompt run
```
make clean
```

Then run your make again and post at least 15 lines previous to where it fails. If you take a look at makes you'll see they run in sections, we need the complete section from which it fails.

I'm very sure you can do this

---

### Post by jocheem67 on 2009-01-07
I can confirm that mplayer is behaving strangely, I'm using a svn from the medibuntu repositories. 
I'm getting the "way too slow" warning and furthermore ot won't dump any audio or create a vob:

```
mplayer dvd://1 -dumpstream -dumpfile title1.vob
```

I suspect we've got a buggy mplayer version here.....as in the past it was working fine. For the TS and other interested this is not helpful.
What I did is using vobcopy on the same dvd which gave me a normal vob

```
 command "vobcopy -l" (large file)
[Info] DVD-name: NIEUW

[Info] Outputting to /home/jochem/NIEUW2.vob
[Info] Successfully copied file /home/jochem/NIEUW2.vob

[Info] Copying finished! Let's see if the sizes match (roughly)
[Info] Combined size of title-vobs: 2805610496 (2676 MB)
[Info] Copied size (size on disk):  2805610496 (2676 MB)
[Info] Everything seems to be fine, the sizes match pretty good ;-)
[Hint] Have a lot of fun!
jochem@jochem-desktop:~$ 
```

Now I create the wav with mplayer.....

Next load the wav in audacity to split it into nice oggs. If one already compresses using mplayer, audacity and splitting does an other compression, which I don't like....

---

### Post by WildeBeest on 2009-01-07
@andrew.46

I ran your command and still only got a file 11 seconds long of silence.

```
 mplayer -aid 128 dvd://1 -vc null -vo null -ao pcm:fast:waveheader:file=track.wav
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 6, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 2 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (stereo) language: en aid: 130.
number of audio channels on disk: 3.
number of subtitles on disk: 0
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  5000.0 kbps (625.0 kbyte/s)
==========================================================================
Forced video codec: null
Opening video decoder: [null] Null video decoder
VDec: vo config request - 720 x 480 (preferred colorspace: BGR 24-bit)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [null] 720x480 => 720x540 Planar YV12 
Selected video codec: [null] vfm: null (NULL codec (no decoding!))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO PCM] File: track.wav (WAVE)
PCM: Samplerate: 48000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   2.3 V:   2.0 A-V:  0.280 ct:  0.071  56/ 56  0%  0%  5.3% 51 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  11.3 V:  11.2 A-V:  0.088 ct:  0.119 331/331  0%  0%  5.8% 291 0 

Exiting... (End of file)

```

---

### Post by WildeBeest on 2009-01-07
@mc4man

Still have errors:

```
ioxml.c: In function 'f_parse_tree':
ioxml.c:275: warning: pointer targets in assignment differ in signedness
ioxml.c:279: warning: pointer targets in assignment differ in signedness
ioxml.c:322: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:324: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:326: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:328: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:330: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:332: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:334: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:361: warning: pointer targets in assignment differ in signedness
ioxml.c:370: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:372: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:374: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:376: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:385: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:387: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:389: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:391: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:400: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:402: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:404: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:406: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:408: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
ioxml.c:424: warning: pointer targets in passing argument 1 of 'xmlStrcmp' differ in signedness
mv -f .deps/ioxml.Tpo .deps/ioxml.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib   -I/usr/include  -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo   -I/usr/include  -I/usr/include/lqt   -I../libxio    -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT probe_xml.lo -MD -MP -MF .deps/probe_xml.Tpo -c -o probe_xml.lo probe_xml.c
 gcc -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib -I/usr/include -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo -I/usr/include -I/usr/include/lqt -I../libxio -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT probe_xml.lo -MD -MP -MF .deps/probe_xml.Tpo -c probe_xml.c  -fPIC -DPIC -o .libs/probe_xml.o
probe_xml.c: In function 'f_check_video_H_W':
probe_xml.c:57: warning: comparisons like X<=Y<=Z do not have their mathematical meaning
probe_xml.c:67: warning: comparisons like X<=Y<=Z do not have their mathematical meaning
mv -f .deps/probe_xml.Tpo .deps/probe_xml.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib   -I/usr/include  -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo   -I/usr/include  -I/usr/include/lqt   -I../libxio    -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT zoom.lo -MD -MP -MF .deps/zoom.Tpo -c -o zoom.lo `test -f '../src/zoom.c' || echo './'`../src/zoom.c
 gcc -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib -I/usr/include -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo -I/usr/include -I/usr/include/lqt -I../libxio -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT zoom.lo -MD -MP -MF .deps/zoom.Tpo -c ../src/zoom.c  -fPIC -DPIC -o .libs/zoom.o
mv -f .deps/zoom.Tpo .deps/zoom.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -module -avoid-version   -o import_xml.la -rpath /usr/lib/transcode import_xml.lo ioxml.lo probe_xml.lo zoom.lo -lxml2 -lxml2 -lm -lm -lz -ldl 
gcc -shared  .libs/import_xml.o .libs/ioxml.o .libs/probe_xml.o .libs/zoom.o  /usr/lib/libxml2.so -lm -lz -ldl  -Wl,-soname -Wl,import_xml.so -o .libs/import_xml.so
creating import_xml.la
(cd .libs && rm -f import_xml.la && ln -s ../import_xml.la import_xml.la)
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib   -I/usr/include  -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo   -I/usr/include  -I/usr/include/lqt   -I../libxio    -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_mplayer.lo -MD -MP -MF .deps/import_mplayer.Tpo -c -o import_mplayer.lo import_mplayer.c
 gcc -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib -I/usr/include -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo -I/usr/include -I/usr/include/lqt -I../libxio -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_mplayer.lo -MD -MP -MF .deps/import_mplayer.Tpo -c import_mplayer.c  -fPIC -DPIC -o .libs/import_mplayer.o
mv -f .deps/import_mplayer.Tpo .deps/import_mplayer.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -module -avoid-version   -o import_mplayer.la -rpath /usr/lib/transcode import_mplayer.lo  -lm -lz -ldl 
gcc -shared  .libs/import_mplayer.o  -lm -lz -ldl  -Wl,-soname -Wl,import_mplayer.so -o .libs/import_mplayer.so
creating import_mplayer.la
(cd .libs && rm -f import_mplayer.la && ln -s ../import_mplayer.la import_mplayer.la)
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib   -I/usr/include  -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo   -I/usr/include  -I/usr/include/lqt   -I../libxio    -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_rawlist.lo -MD -MP -MF .deps/import_rawlist.Tpo -c -o import_rawlist.lo import_rawlist.c
 gcc -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib -I/usr/include -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo -I/usr/include -I/usr/include/lqt -I../libxio -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_rawlist.lo -MD -MP -MF .deps/import_rawlist.Tpo -c import_rawlist.c  -fPIC -DPIC -o .libs/import_rawlist.o
import_rawlist.c: In function 'import_rawlist_decode':
import_rawlist.c:396: warning: pointer targets in passing argument 2 of 'p_read' differ in signedness
import_rawlist.c:406: warning: pointer targets in passing argument 2 of 'p_read' differ in signedness
mv -f .deps/import_rawlist.Tpo .deps/import_rawlist.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -module -avoid-version  -o import_rawlist.la -rpath /usr/lib/transcode import_rawlist.lo ioaux.lo -lm -lm -lz -ldl 
gcc -shared  .libs/import_rawlist.o .libs/ioaux.o  -lm -lz -ldl  -Wl,-soname -Wl,import_rawlist.so -o .libs/import_rawlist.so
creating import_rawlist.la
(cd .libs && rm -f import_rawlist.la && ln -s ../import_rawlist.la import_rawlist.la)
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib   -I/usr/include  -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo   -I/usr/include  -I/usr/include/lqt   -I../libxio    -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_ogg.lo -MD -MP -MF .deps/import_ogg.Tpo -c -o import_ogg.lo import_ogg.c
 gcc -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib -I/usr/include -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo -I/usr/include -I/usr/include/lqt -I../libxio -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_ogg.lo -MD -MP -MF .deps/import_ogg.Tpo -c import_ogg.c  -fPIC -DPIC -o .libs/import_ogg.o
mv -f .deps/import_ogg.Tpo .deps/import_ogg.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -module -avoid-version   -o import_ogg.la -rpath /usr/lib/transcode import_ogg.lo  -lm -lz -ldl 
gcc -shared  .libs/import_ogg.o  -lm -lz -ldl  -Wl,-soname -Wl,import_ogg.so -o .libs/import_ogg.so
creating import_ogg.la
(cd .libs && rm -f import_ogg.la && ln -s ../import_ogg.la import_ogg.la)
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib   -I/usr/include  -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo   -I/usr/include  -I/usr/include/lqt   -I../libxio    -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_xvid.lo -MD -MP -MF .deps/import_xvid.Tpo -c -o import_xvid.lo import_xvid.c
 gcc -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib -I/usr/include -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo -I/usr/include -I/usr/include/lqt -I../libxio -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_xvid.lo -MD -MP -MF .deps/import_xvid.Tpo -c import_xvid.c  -fPIC -DPIC -o .libs/import_xvid.o
import_xvid.c: In function 'import_xvid_open':
import_xvid.c:288: warning: pointer targets in assignment differ in signedness
mv -f .deps/import_xvid.Tpo .deps/import_xvid.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -module -avoid-version   -o import_xvid.la -rpath /usr/lib/transcode import_xvid.lo  -lm -lz -ldl 
gcc -shared  .libs/import_xvid.o  -lm -lz -ldl  -Wl,-soname -Wl,import_xvid.so -o .libs/import_xvid.so
creating import_xvid.la
(cd .libs && rm -f import_xvid.la && ln -s ../import_xvid.la import_xvid.la)
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib   -I/usr/include  -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo   -I/usr/include  -I/usr/include/lqt   -I../libxio    -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_ffmpeg.lo -MD -MP -MF .deps/import_ffmpeg.Tpo -c -o import_ffmpeg.lo import_ffmpeg.c
 gcc -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -DMOD_PATH=\"/usr/lib/transcode\" -I.. -I../src -I../libtc -I/usr/include -I../libac3 -I../avilib -I/usr/include -I/usr/include -I/usr/include -I/usr/include/libxml2 -I../libvo -I/usr/include -I/usr/include/lqt -I../libxio -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -g -O2 -MT import_ffmpeg.lo -MD -MP -MF .deps/import_ffmpeg.Tpo -c import_ffmpeg.c  -fPIC -DPIC -o .libs/import_ffmpeg.o
import_ffmpeg.c: In function 'import_ffmpeg_open':
import_ffmpeg.c:364: error: 'AVCodecContext' has no member named 'error_resilience'
import_ffmpeg.c:412: warning: pointer targets in assignment differ in signedness
import_ffmpeg.c:441: warning: pointer targets in assignment differ in signedness
import_ffmpeg.c: In function 'import_ffmpeg_decode':
import_ffmpeg.c:553: warning: pointer targets in passing argument 1 of 'mpeg4_is_key' differ in signedness
import_ffmpeg.c:589: warning: pointer targets in passing argument 4 of 'avcodec_decode_video' differ in signedness
import_ffmpeg.c:670: warning: pointer targets in passing argument 1 of 'yuv2rgb' differ in signedness
import_ffmpeg.c:670: warning: pointer targets in passing argument 2 of 'yuv2rgb' differ in signedness
import_ffmpeg.c:670: warning: pointer targets in passing argument 3 of 'yuv2rgb' differ in signedness
import_ffmpeg.c:670: warning: pointer targets in passing argument 4 of 'yuv2rgb' differ in signedness
import_ffmpeg.c:756: warning: pointer targets in passing argument 1 of 'yuv2rgb' differ in signedness
import_ffmpeg.c:756: warning: pointer targets in passing argument 2 of 'yuv2rgb' differ in signedness
import_ffmpeg.c:756: warning: pointer targets in passing argument 3 of 'yuv2rgb' differ in signedness
import_ffmpeg.c:756: warning: pointer targets in passing argument 4 of 'yuv2rgb' differ in signedness
make[3]: *** [import_ffmpeg.lo] Error 1
make[3]: Leaving directory `/home/willy/Code/transcode-1.0.6/import'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/willy/Code/transcode-1.0.6/import'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/willy/Code/transcode-1.0.6'
make: *** [all] Error 2

```

---

### Post by WildeBeest on 2009-01-07
@jocheem67

I'll try your method when I get home from work.

---

### Post by mc4man on 2009-01-07
@WildeBeest
I can ck. on your transcode later, but as far as mplayer I'm not sure your 100% getting the idea.
To try something use the [U]dvd you were using in post 6.
[/U]
Use this as a command, your just going to extract chapter **2** from title **2** using the first audio track.(-aid 128

```
mplayer -vc null -vo null -aid [COLOR="Red"]128[/COLOR] -ao pcm:fast:waveheader:file=foo1.wav dvd://[COLOR="Red"]2[/COLOR] -chapter [COLOR="Red"]2-2[/COLOR]
```

See if that works

---

### Post by jocheem67 on 2009-01-07
Here's a summary of the commands used:

```
"vobcopy -l" gives one big vob, to specify the drive is not necessary in my rig
```

```
mplayer *.vob -vc null -vo null -ao pcm:fast:waveheader:file=*.wav
```

And there's the wav:)

---

### Post by mc4man on 2009-01-07
For transcode 1.0.6

I don't have the time to track exactly what's missing but this should fulfill everything  (see note

```
sudo apt-get build-dep mplayer
```

Then because you should use checkinstall
```
sudo apt-get install checkinstall
```

Then at your build prompt
```
make distclean
```

Then run the configure again, you should see this in the summary
> headers                        
libraries                      -L/usr/lib -lavcodec -lavcodec -ltheora -lvorbisenc -lraw1394 -lavutil -lvorbis -lm -logg

run make and when successful use this to install ( instead of sudo make install

```
sudo checkinstall --fstrans=no --install=yes --pkgname=transcode --pkgversion "2:1.0.6`date +%Y%m%d`-0.8ubuntu7"
```

Note: on a 8.04 install that had *nothing but transcode 1.0.2 installed *getting the build-deps for transcode and mplayer plus the additional apt-get install in post 22 resulted in a full configure with successful make and install.
If you get this going try on anytjing but that particular dvd's title 2 chapter 1 ( there's something odd there.

---

### Post by mc4man on 2009-01-07
> I can confirm that mplayer is behaving strangely, I'm using a svn from the medibuntu repositories.
I'm getting the "way too slow" warning and furthermore ot won't dump any audio or create a vob:


You should probably get a more recent mplayer, if you don't want to build then you can get one from Rvm (smplayer) either from adding his ppa or a direct download. (ppa is better

[http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php)

The only thing that would stray from standard commands is dumping to a chapter stop if you have a dvdnav enabled version of mplayer. (extract to .wav doesn't need dvdnav
Then you use something like this
Ex. audio dump chap.3
```
mplayer -vc null -vo null  -aid 128 -dumpaudio dvdnav://1 -chapter 3-3
```

---

### Post by WildeBeest on 2009-01-07
@mc4man

The configure command only displays this in the summary section:

```
headers                        
libraries                      -L/usr/lib -lavcodec -L/usr/local/lib -lavcodec

```

Still get the same error when executing the make command as above:

---

### Post by mc4man on 2009-01-07
Sorta at a loss. on my main machine it built as is and on an new install with nothing installed other than transcode 1.0.2 it also built with the *transcode and mplayer build-deps + the added line previously posted.*

you could try carefully copying and pasting the below into a terminal and running. It should report nothing to install. It it does install something then try your configure and make again.

If it reports nothing to install then open a *maximized text file* and paste the below into it. Replace sudo apt-get install with sudo aptitude reinstall, carefully copy and run again.

(make sure that the complete command runs, from sudo to libdvdcss2, a break in the lines will stop there.

Did you get mplayer to work?



> sudo apt-get install autotools-dev build-essential debhelper dpatch dpkg-dev g++ g++-4.2 gettext html2text intltool-debian liba52-0.7.4-dev libatk1.0-dev libavcodec-dev libavutil-dev libbz2-dev libc6-dev libcairo2-dev libdc1394-13 libdc1394-13-dev libdjvulibre-dev libdv4-dev libdvdread-dev libexif-dev libexpat1-dev libfaac0 libfame-dev libfontconfig1-dev libfreetype6-dev libgl1-mesa-dev libglib1.2-dev libglib2.0-dev libglu1-mesa-dev  libgraphviz-dev libgsm1-dev libgtk1.2-dev libgtk2.0-dev libice-dev libjasper-dev libjpeg62-dev liblame-dev liblcms1-dev libltdl3-dev liblzo-dev libmagick9-dev libmjpegtools-dev libmpeg2-4-dev libncurses5-dev libogg-dev libopenexr-dev libpango1.0-dev libpixman-1-dev libpng12-dev libpopt-dev libpostproc-dev libpthread-stubs0 libpthread-stubs0-dev libquicktime-dev libraw1394-dev libreadline5-dev librsvg2-dev libsdl1.2-dev libsm-dev  libstdc++6-4.2-dev libtheora-dev libtiff4-dev libtiffxx0c2 libtimedate-perl libvorbis-dev libwmf-dev libx11-dev libx264-57 libxau-dev libxaw-headers libxaw7-dev libxcb-xlib0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxmu-dev libxmu-headers libxpm-dev libxrandr-dev libxrender-dev libxt-dev libxv-dev libxvidcore4 libxvidcore4-dev libxxf86vm-dev linux-libc-dev mesa-common-dev nasm patch po-debconf pvm pvm-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev em8300-headers ladspa-sdk libaa1-dev libartsc0 libartsc0-dev libasound2-dev libaudio-dev libaudio2 libaudiofile-dev libcaca-dev libcdparanoia0-dev libcucul-dev libdbus-glib-1-dev libdts-dev libenca-dev libenca0 libesd0-dev libfaac-dev libfreebob0 libfribidi-dev libggi2 libggi2-dev libgif-dev libgii1 libgii1-dev libgii1-target-x libjack-dev libjack0 liblircclient-dev liblivemedia-dev liblzo2-dev libmad0 libmad0-dev libmpcdec-dev libmpcdec3 libopenal-dev libpulse-dev libpulse-mainloop-glib0 libslang2-dev libsmbclient-dev libspeex-dev libsvga1 libsvga1-dev libtwolame-dev libtwolame0 libx264-dev libxvmc-dev libxvmc1 libxxf86dga-dev sharutils x11proto-xf86dga-dev libavifile-0.7-dev libxvidcore4-dev libfame-dev libmpeg2-4-dev mjpegtools libavahi-client-dev libavformat-dev libavahi-glib-dev libmpeg4ip-dev libmpeg3-dev libmp4v2-dev ffmpeg w32codecs libswscale-dev libdvdnav-dev libfame-dev liba52-0.7.4-dev libdvdcss2


---

### Post by WildeBeest on 2009-01-07
I ran the sudo apt-get and I do get an error.

```
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

mplayer is a no go either.

Side note: running  "ImTOO DVD Audio Ripper 5" eval version under wine works.
I'm too cheap to pay for the real one. :) lol

I would really like to get this to work without having to use a windoze app.

---

### Post by andrew.46 on 2009-01-07
Hi,

I am a little puzzled by the failure of the Ubuntu and Medibuntu MPlayers. If you are keen you could uninstall all of these older MPlayers and install the svn:

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

This is the version I use, in part because it is my guide. It is a little like using a sledgehammer to crack a walnut though :-).

Andrew

---

### Post by mc4man on 2009-01-07
If you can't get w32codecs then that is suggestive that you don't have medibuntu enabled as a source.

This may also mean your using the hardy repo mplayer, libav*'s and ffmpeg.

Could you check and see in System -> Admin... -> software sources -> third party.


edit : For mplayer, if your continuing to try that title in post6 have you switched the command to extract from title 2?

---

### Post by WildeBeest on 2009-01-07
@andrew

I'll try that.

@mc4man

I have everything checked except the source code ones.

This is what's checked.

```
http://archive.canonical.com/ubuntu
http://ppa.launchpad.net/psyke83/ubuntu
http://download.virtualbox.org/virtualbox/debian
http://packages.medibuntu.org/
http://wine.budgetdedicated.com/apt

```

By the way, can it be because I'm running 64 bit?

---

### Post by mc4man on 2009-01-07
> By the way, can it be because I'm running 64 bit?

Yeah, the w32codecs (or in your case w64codecs) aren't needed for building transcode, I threw them in as an addition.

I have no idea if 64 bit has issues with building transcode.

I'd go back and just use the repo 1.0.2 version. It should be suffecient to extract and convert to mp3. You should try if again with any other track than track 1 on that dvd. This way you'll know if it works.

This doesn't look right

> transcode] A: import format    | 0x1000f unknown      [48000,16,2]


Edit: this is the configure for the repo 1.0.2, it should be fairly functional for you, it's just a matter of using it correctly (transcode 

-> -disable-libmpeg3 --enable-text --enable-v4l --enable-libfame \
	--disable-libfametest --enable-lzo --enable-ogg --enable-mjpegtools \
	--enable-gtk --enable-imagemagick --enable-theora --enable-libquicktime \
	--enable-libdv --enable-libxml2 --enable-vorbis --enable-a52 \
	--enable-pvm3 --enable-netstream --enable-ffbin --enable-sdl \
	--enable-libpostproc $(AVIFILE) --enable-freetype2 \
	--with-libpostproc-includes=/usr/include/postproc

---

### Post by WildeBeest on 2009-01-07
Other tracks don't work either.
The file name is generated and 0 bytes long.

The last line is always "[transcode] encoded 0 frames (xxxx dropped, 0 cloned), clip length   0.00 s"

I guess I have to "cough" up the $ to get the registered version of "ImTOO DVD Audio Ripper 5".

:(

Thanks for all your help and patience.

---

### Post by mc4man on 2009-01-07
In that case try this first ( I believe it's a 30 day full function trail. works in wine

[http://www.castudio.org/dvdaudioextractor/](http://www.castudio.org/dvdaudioextractor/)


Edit: ImTOO DVD Audio Ripper 5 is a re packing of the dvd audio extractor, which is better supported I don't know, dae is the  I have from windows days.

---

### Post by WildeBeest on 2009-01-08
> **andrew.46 said:**
> Hi,

I am a little puzzled by the failure of the Ubuntu and Medibuntu MPlayers. If you are keen you could uninstall all of these older MPlayers and install the svn:

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

This is the version I use, in part because it is my guide. It is a little like using a sledgehammer to crack a walnut though :-).

Andrew

Is this for Hardy 64 bit also?

---

### Post by jocheem67 on 2009-01-08
Ever tried vobcopy ??

I am thinking of removing mplayer and compile it, just for the fun of it...did that before...

---

### Post by WildeBeest on 2009-01-08
Yes I did. Your commands from yesterday.
Can't remember what it did, but I know it did not work either.

---

### Post by jocheem67 on 2009-01-09
Well , there is of course the possibility that this particular dvd has a protection that can't  be beaten by the linux native tools.
I use dvd fab hd decrypter with wine to rip dvdmovies, it's imho the best tool as there's is no dvd that can't be ripped..however this is a tool that is not that easily installed. Furthermore it's necessary to open the vob's with avidemux and to copy the ac-3 streams from there, it's all not that easy...:(

Maybe the paid option is the one to go here, pity that linux doesn't really deliver this time.

---

### Post by andrew.46 on 2009-02-14
Hi,

This thread has gone a little cold but I thought I would just mention that transcode 1.1.0 is out now and the issue of finding FFmpeg libraries appears to have been resolved with this release.

I have successfully compiled and installed it but not on Ubuntu I am afraid. Compiling on Ubuntu can be a right royal PITA at times. For the record I managed:

```

----------------------------------------
Summary for transcode 1.1.0:
----------------------------------------

core options
----------------------------------------
enable experimental code       no
enable deprecated code         no
static AV-frame buffering      yes
A52 default decoder            yes

ffmpeg libraries
----------------------------------------
libavcodec  build              3411712
libavcodec  version            52.15.0
libavformat build              3414784
libavformat version            52.27.0

hardware support
----------------------------------------
v4l/v4l2                       yes
ALSA                           yes
OSS                            no
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

```

but unfortunately since I managed this on another distro I have little to offer here :confused:.

Andrew

---

### Post by WildeBeest on 2009-02-16
@ andrew.46

I was able to build version 1.0.7 a while ago.

I just down loaded 1.1 and attempted to build it.

I got the following errors:

```
ERROR: requirement failed: cannot compile ffmpeg/avformat.h
ffmpeg/avformat.h can be found in the following packages:
  libavformat  http://www.ffmpeg.org/

ERROR: requirement failed: cannot link against libavformat
libavformat can be found in the following packages:
  libavformat  http://www.ffmpeg.org/


```

```
checking for pkgconfig support for libavcodec... yes
checking how to determine LIBAVCODEC_CFLAGS... user
checking libavcodec/avcodec.h usability... yes
checking libavcodec/avcodec.h presence... yes
checking for libavcodec/avcodec.h... yes
checking how to determine LIBAVCODEC_LIBS... user
checking for avcodec_thread_init in -lavcodec... yes
VER=52.10.0
BUILD=3410432
checking for pkgconfig support for libavformat... yes
checking how to determine LIBAVFORMAT_CFLAGS... pkg-config
checking libavformat/avformat.h usability... yes
checking libavformat/avformat.h presence... yes
checking for libavformat/avformat.h... yes
checking how to determine LIBAVFORMAT_LIBS... pkg-config
checking for av_register_all in -lavformat... no
checking for pkgconfig support for libavformat... yes
checking how to determine LIBAVFORMAT_CFLAGS... pkg-config
checking ffmpeg/avformat.h usability... no
checking ffmpeg/avformat.h presence... no
checking for ffmpeg/avformat.h... no
checking how to determine LIBAVFORMAT_LIBS... pkg-config
checking for av_register_all in -lavformat... (cached) no

```


The configure command that worked for 1.0.7 which I tried with 1.1

```
./configure --prefix=/usr --enable-libmpeg3 --enable-text --enable-v4l --enable-libfame --disable-libfametest --enable-ogg --enable-mjpegtools --enable-lzo --enable-gtk --enable-imagemagick --enable-theora --enable-libquicktime --enable-libdv --enable-libxml2 --enable-vorbis --enable-a52 --enable-pvm3 --enable-netstream --enable-sdl --enable-freetype2 --enable-avifile --enable-a52-default-decoder --enable-libpostproc --enable-libmpeg3 --enable-nuv --enable-oss --enable-libavformat --with-libavcodec-includes=/usr/local/include/libavcodec --with-libavcodec-libs=/usr/lib --with-libpostproc-includes=/usr/local/include/libpostproc --with-libpostproc-libs=/usr/lib --with-libavformat-includes=/usr/local/include/libavformat --with-libavformat-libs=/usr/lib
```

Any ideas what might be wrong?

---

### Post by andrew.46 on 2009-02-17
Hi WildeBeest,

> **WildeBeest said:**
> 

I just down loaded 1.1 and attempted to build it.

I got the following errors:

```
ERROR: requirement failed: cannot compile ffmpeg/avformat.h
ffmpeg/avformat.h can be found in the following packages:
  libavformat  http://www.ffmpeg.org/

ERROR: requirement failed: cannot link against libavformat
libavformat can be found in the following packages:
  libavformat  http://www.ffmpeg.org/


```



Unfortunately I did not compile under Ubuntu, and in fact I don't actuallu have Ubuntu running at all at the moment :(. I notice that you gave the full paths to FFmpeg in your configure line. Easiest thing to try first is to eliminate all of this and let Transcode look itself. So:

```
./configure --enable-libavcodec \
--enable-libavformat \
--enable-libavformat

```

*without* the full path and then the other options. I believe that Transcode can find these headers better than it used to.

Have you installed the lastest svn FFmpeg? This would be your best bet and the FakeOutdoorsman has an excellent guide for this [on these forums]("http://ubuntuforums.org/showthread.php?t=786095").

Andrew

---

### Post by WildeBeest on 2009-02-17
The "shortened" configure command didn't work either, still got the same results.
The only thing I noticed, is that I don't have an 'avformat.so' file.

As far as ffmpeg goes, I believe that I have the lastest installed. That's the guide I followed when I installed it.

Is there a way to tell? 
Looks like the newest was released on 12/20/08, I installed it on 1/6/09.

---

### Post by andrew.46 on 2009-02-18
Hi WildeBeest,

> **WildeBeest said:**
> The "shortened" configure command didn't work either, still got the same results.
The only thing I noticed, is that I don't have an 'avformat.so' file.

I suspect it would be foolish of me to try give advice on installing transcode under Ubuntu since or the moment I don't actually have it on my computer. Perhaps make a new thread and attract the attention of mc4man who has installed this using Ubuntu recently?

> As far as ffmpeg goes, I believe that I have the lastest installed. That's the guide I followed when I installed it.

Is there a way to tell? 
Looks like the newest was released on 12/20/08, I installed it on 1/6/09.
 
FFmpeg development is white-hot at the moment so there will be updates each and every day :-).

Andrew

---

### Post by mc4man on 2009-02-18
@ wildebeast
Unfortunately while I'm running 8.10 on my main machine it's a 'hybrid of sorts, very multimedia specific towards certain apps. (vlc, mplayer, audacious, amarok, avidemux, transcode, rubyripper, sox and a few others.

Initially I had no intention to use 8.10 for various reasons, one of which is the split of the ffmpeg libs into stripped and unstripped versions with no -dev's for the unstripped.

While you can work around this by building your own versions ect., ect., I already do that in 8.04 and had/have no reason to repeat.

As an experiment I decided to try to use 8.10 and stay current with the core A/V libs and newest versions of apps with the least amount of compiling, actually limiting that to vlc, rubyripper, and mplayer. (with a few minor exceptions.

The basis of the experiment (which I've come to love) is to 'replace' medibuntu with debian-multimedia.(sid and experimental). The 'restraints' were to use absolutely  no debian repo packages other than debian-multimedia, though I allowed the use of some jaunty packages as long as they were 'dead end' so to speak. (no possibility for dep issues with intrepid updates.

For my use it's worked out better than I expected and overall there has been very little  'loss of function' in terms of a 'normal' intrepid install and certainly nothing that I've ever used.

It not something I'd intend to recommend.

So for instance when I wanted to try the latest transcode I just opened up synaptic and  installed it.

---

### Post by mc4man on 2009-02-18
Well out of curiosity decided to build, was actually fairly easy.
Your going to want to get as current as possible with x264, libx264(-dev), and libavformat (-dev). (at least 64 on x264 and probably 52 on libavformat. The libavformat-dev version may prove the biggest issue (if 52 version is needed, same for libavcodec-dev

Other than that read your ./configure and fill in as wanted/needed/possible

Example ./configure

> ./configure --prefix=/usr --enable-libmpeg3 --enable-text --enable-v4l --enable-libfame --disable-libfametest --enable-ogg --enable-mjpegtools  --enable-gtk --enable-imagemagick --enable-theora --enable-libquicktime --enable-libdv --enable-libxml2 --enable-vorbis --enable-a52 [COLOR="Blue"]--enable-pvm3[/COLOR] --enable-netstream  --enable-freetype2  --enable-a52-default-decoder  --enable-libmpeg3 --enable-oss --enable-avifile --enable-x264 --enable-libpostproc --enable-alsa --enable-faac -enable-xvid --enable-lzo --enable-sdl [COLOR="Blue"]--enable-experimental[/COLOR]

> Summary for transcode 1.1.0:
----------------------------------------

core options
----------------------------------------
enable experimental code       yes
enable deprecated code         no
static AV-frame buffering      yes
A52 default decoder            yes

ffmpeg libraries
----------------------------------------
libavcodec  build              3410688
libavcodec  version            52.11.0
libavformat build              3414272
libavformat version            52.25.0

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
pvm3                           yes
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




---

