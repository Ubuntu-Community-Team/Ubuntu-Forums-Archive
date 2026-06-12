---
title: "Dump audio from vorbis file"
date: 2008-09-09
forum: Multimedia Software
---

### Post by soxs on 2008-09-09
**EDIT: ARGH! PLX SOMEONE EDIT THE TITLE , IT'S NOT A VORBIS BUT A VOB FILE!**
I would like to dump audio from a .vob file.
I tried various options but all failed, maily based on mencoder.
So, I'd like to hear what options I have to dumpaudio (I know how to recode audio, I thought I knew how to dump audio aswell..*g*)

---

### Post by soxs on 2008-09-11
**bump!**

---

### Post by FakeOutdoorsman on 2008-09-11
You can use ffmpeg.  First, determine what the audio codec is:
```
ffmpeg -i donkeywrangling.vob
```
My particualr vob file gives me the following:
```
Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 64 kb/s
```
Now you can extract the audio without re-encoding:
```
ffmpeg -i frinkahedron.vob -vn -acodec copy nerdville.mp2
```
-vn tells ffmpeg to ignore video.  -acodec copy tells it to just copy the audio stream.

If you want to transcode the file to something else (you don't always need -vn):
```
ffmpeg -i LegislativeApe.vob monkeypoop.wav
```
VOB isn't Vorbis, but a container format for MPEG-2 type streams.

---

### Post by mc4man on 2008-09-12
> what options I have to dumpaudio

Some add. options if doing direct from dvd is to use mplayer.

Assuming 'dump' means keep the audio format I use for complete stream (variables in red

```
mplayer -vc null -vo null -aid [COLOR="Red"]128[/COLOR] -dumpaudio dvd://[COLOR="Red"]1[/COLOR]
```
produces a stream.dump, rename to <whatever>.ac3 or <whatever>.<appropriate ext.>

Per chapter
```
mplayer -vc null -vo null -aid [COLOR="Red"]128[/COLOR] -dumpaudio dvd://[COLOR="Red"]1[/COLOR] -chapter [COLOR="Red"]9-9[/COLOR]
```
again produces a stream.dump (appears as a file though - renaming gives audio icon and playability)

for a group of chapters use for ex. -chapter 7-10

For conversion to .wav or for dumping a lpcm stream

```
mplayer -vc null -vo null -aid 1[COLOR="Red"]28[/COLOR] -ao pcm:fast:waveheader:file=[COLOR="Red"]foo[/COLOR].wav dvd://[COLOR="Red"]1[/COLOR] 
```

```
mplayer -vc null -vo null -aid [COLOR="Red"]128[/COLOR] -ao pcm:fast:waveheader:file=[COLOR="Red"]foo9[/COLOR].wav dvd://[COLOR="Red"]1[/COLOR] -chapter [COLOR="Red"]9-9[/COLOR]

```

In this case 'rips' to a specified output name, haven't figured out how to -dumpaudio to specified name yet (if possible

A little more info on finding aid, ect. for the 'rip/dump' to .wav here

[http://ubuntuforums.org/showthread.php?p=5454243#post5454243](http://ubuntuforums.org/showthread.php?p=5454243#post5454243)

---

### Post by soxs on 2008-09-12
I allready tried mplayer, but it didn't work (at least the vob file refuses to give me the audio from it):
```
mplayer -vc null -vo null -aid 128 -dumpaudio ./XXX.vob
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) 9500 Quad-Core Processor (Family: 16, Model: 2, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Warning unknown option download at line 2
Warning unknown option cachesize at line 3
Warning unknown option cache-percent at line 4
Warning unknown option keep-download at line 5
Warning unknown option dload-dir at line 6
Warning unknown option noembed at line 7
Warning unknown option autoplay at line 8
Warning unknown option enable-wmp at line 9
Warning unknown option enable-qt at line 10
Warning unknown option enable-rm at line 11
Warning unknown option enable-gmp at line 12
Warning unknown option enable-dvx at line 13
Warning unknown option enable-mpeg at line 14
Warning unknown option enable-mp3 at line 15
Warning unknown option enable-midi at line 16
Warning unknown option enable-pls at line 17
Warning unknown option enable-ogg at line 18
Warning unknown option enable-smil at line 19
Warning unknown option enable-helix at line 20
Warning unknown option nomediacache at line 21
Warning unknown option nopauseonhide at line 22
Warning unknown option black-background at line 23
Warning unknown option rtsp-use-http at line 24
Warning unknown option rtsp-use-tcp at line 25
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing ./XXX.vob.
TS file format detected.
VIDEO MPEG2(pid=68) NO AUDIO!  NO SUBS (yet)!  PROGRAM N. 0
TS_PARSE: COULDN'T SYNC
Core dumped ;)

Exiting... (End of file)

```

But the file stream.dump is sized zer0 bytes, that's the reason I asked here.
Btw. outpufile can be determined for mplayer by the switch -of (at least as far as I know)

---

### Post by mc4man on 2008-09-12
What I was referring to in previous post was for 'direct from dvd'.(meaning disk
I've never tried from an individual .vob (seems the **ffmpeg way may be more suitable for what you have** or structure the command based on successfully playing the. vob thru mplayer

If you had the complete title on hdd then if it was made into an .iso and mounted you could easily use those commands (using for ex.  -dvd-device /[COLOR="Red"]media[/COLOR]/[COLOR="Red"]cdrom2[/COLOR] or whatever your iso mountpoint is


edit any of these worked here ( from VIDEO_TS file on hdd

> mplayer -vc null -vo null -dumpaudio /home/doug/Movie_name/VIDEO_TS/VTS_02_1.VOB
> mplayer -vc null -vo null -aid [COLOR="Red"]128[/COLOR] -dumpaudio /home/doug/Movie_name/VIDEO_TS/VTS_02_1.VOB

or moving/ renaming the .vob to by itself in home dir.
 > mplayer -vc null -vo null -aid [COLOR="Red"]128[/COLOR] -dumpaudio /home/doug/test.VOB


Ex. 
> doug@doug-desktop:~$ mplayer -vc null -vo null -aid 128 -dumpaudio /home/doug/test.VOB
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
......clipped
Playing /home/doug/test.VOB.
[COLOR="Red"]MPEG-PS[/COLOR] file format detected.
Core dumped ;)

Exiting... (End of file)




I always see Mpeg-PS (whether from disk, directory, or file

Edit: I do see that on the current mplayer rev.'s (actually since april, not the hardy ver. though) the chapter end appears to be non functional
for instance '-chapter 5-5' will start on chapter 5 and do the remainder of the title. Can't figure how to get it to use chapter end

---

### Post by soxs on 2008-09-16
Usually it works like that with .vob files too.. but this time it somehow didn't...

---

