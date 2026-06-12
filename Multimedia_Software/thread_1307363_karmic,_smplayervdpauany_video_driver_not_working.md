---
title: "karmic, s/mplayer/vdpau/any video driver not working"
date: 2009-10-31
forum: Multimedia Software
---

### Post by sloggerkhan on 2009-10-31
So I upgraded my desktop to karmic. Seems fine except it won't play video at all except for cpu rendering.

XV and vdpau are no goes. I am using mplayer, have tried packaged nvidia drivers and 190.42 latest stable release. Both work fine for 3-D, just fail 100% at video. Smplayer obviously fails similarly.

I have enabled a repo for the latest mplayer (which worked perfectly in 9.04).

Sample output of trying to play anything:
```

MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Video (H.264)", -vid 0
[mkv] Track ID 2: audio (A_AAC) "Japanese Audio (2ch LC-AAC)", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "English Subtitles (***)", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...


MPlayer interrupted by signal 11 in module: decode_audio
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

Anyhow, I can't seem to get any video playback in any format out of my nvidia card with karmic. (Though I get garbage cpu rendered video from totem.)

---

### Post by sloggerkhan on 2009-10-31
Side note: 
flash dies if full screened (did not hapen with 9.04)
VLC seems to work with xv/x11
xine dies no matter what

---

### Post by andrew.46 on 2009-10-31
Hi sloggerkhan,

Does MPlayer only crash with mkv files? I ask only as this was an issue with older svn revisions although I don't remember the exact number. Probably will not have much to do with your other problems though...

Andrew

---

### Post by pistacoppu on 2009-10-31
I also can't play video at all, i upgradede from 9.04, (not a new installation).
i can't play: avi , mkv , mp4 , that are the formats i've tried so far.
Using Vlc 1.0.2 , and Movie Player.

p.s. also the media player "Listen" is not working.

---

### Post by pistacoppu on 2009-10-31
> **sloggerkhan said:**
> Side note: 
flash dies if full screened (did not hapen with 9.04)
VLC seems to work with xv/x11
xine dies no matter what
What does it mean: VLC seems to work with xv/x11    ?
do i have to change some settings in vlc?
because vlc worked perfectly on 9.04 without changing any default setting.

(i have an nvidia too)

---

### Post by pistacoppu on 2009-10-31
I changed settings to x11, but it is still not working.
This is the error message:  
"No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this."

in that case i tried to open an avi

---

### Post by sloggerkhan on 2009-10-31
So I got 2:1.0~rc3+svn20090620~karmic~ppa4 from the nvidia-vdpau ppa, and it plays stuff.
I get unresolvable issues (IE neither version plays back no matter what overlay or audio output) with the 2:1.0~rc3+svn20090426-1ubuntu10 from the regular repos, and also with one dated 200909something from the rvm/mplayer ppa. 

However, the smplayer gui will refuse to play any files except the first file opened with it, so that you'd have to quit in between each file to play another. I've tried three different smplayer ppa versions and all of them will only play the first file that they open and no other files. So I now just have an issue with smplayer, as I've verified mplayer to be working from cl on the 6-20 package.

At first I wondered about the mkv thing, but it doesn't seem to be relevant.

---

### Post by sloggerkhan on 2009-10-31
Final definitive issue:
SMplayer can't cope with smb shares. 
If I open a file from an smb share directly, it will play. But if I queue them in a playlist or drag and drop them on each other, files from the smb share won't play.
It does work fine from a sshfs connection, or local files. Just not with those shared via samba.

---

### Post by pistacoppu on 2009-10-31
i've not understand your problem very much, but that is what i did to resolve all problems i had with vlc, and now smplayer works too:
$  sudo apt-get remove smplayer*
$  sudo apt-get remove mplayer*
$ sudo apt-get remove libx264-67 --purge
$ sudo apt-get install libx264*
then i reinstalled bot mplayer and smplayer
i hope it works

---

### Post by sloggerkhan on 2009-10-31
So I've finally got this all figured out.
In reality I had 2 different problems.
First, I needed to mount my samab share in fstab using cifs to get its files to really be treated as part of the filesystem.
Second, to get mplayer/smplayer/vdpau to behave properly, I needed to force them all to be specific versions.

---

