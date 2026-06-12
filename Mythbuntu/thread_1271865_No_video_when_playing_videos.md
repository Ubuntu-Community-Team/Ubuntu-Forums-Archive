---
title: "No video when playing videos"
date: 2009-09-21
forum: Mythbuntu
---

### Post by trevs.bronco on 2009-09-21
I am trying to get VDPAU working on my frontend as my processor can't handle HD video. My previous attempts failed miserably so I have done a fresh install of 9.04 and have installed the NVidia 190.32 drivers. I added Jean-Yeves repository and did an apt-get update apt-get upgrade. in play back I followed the settings on [this]("http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html") page the best I could, but i was unable to enter anything for renderer and could not change the deinterlacer to the prescribed settings.
What did i mess up on and how might i fix it?

Thanks,

Trev

---

### Post by trevs.bronco on 2009-09-21
I guess i should have said what is happening. When I start a video from Myth the loading page stays on the screen and then the audio starts but no video. the only way i am able to stop the audio is to kill mplayer from a command line. Mplayer does work from outside Myth, but does not have VDPAU.

Trev

---

### Post by trevs.bronco on 2009-09-21
here is the output from my frontend log when I tried to play an SD movie.

```
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Atom(TM) CPU  330   @ 1.60GHz (Family: 6, Model: 28, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /mnt/movies/Gran Torino.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x272  12bpp  23.976 fps  823.6 kbps (100.5 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2542/release)
Error opening/initializing the selected video_out (-vo) device.
```

And here is a log entry from trying to play a HD movie.

```
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Atom(TM) CPU  330   @ 1.60GHz (Family: 6, Model: 28, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /mnt/movies/8_Mile.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS) "English DTS 1509kbps", -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8) "English", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x544  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Error opening/initializing the selected video_out (-vo) device.
```

---

### Post by laffinet on 2009-09-21
What is the video player line in the frontend set up ?

Setup -> Media Settings -> Player settings

---

### Post by trevs.bronco on 2009-09-22
OK I have had some success, I was playing with the playback settings when after making some changes i could not change back to the VDPAU profile. so what tried which worked was.
```
aptitude update
aptitude upgrade
```why this worked and apt-get didn't i don't know but my video is now working and topping out the CPU at 19% as opposed to the 102% it hit before.
now my problem is no audio. I have check that nothing is muted in mixer, checked that asound.conf is unchanged and tried changing the sound output settings in myth to a few different configerations and nothing has worked yet. The log files say that audio playback is working.

Here is the front end log during playback.

```
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 1280 x 544 (preferred colorspace: H.264 VDPAU acceleration)
VDec: using H.264 VDPAU acceleration as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x544 => 1280x544 H.264 VDPAU acceleration  [fs] [zoom]
[Mixer] No hardware mixing, inserting volume filter.
```I do have audio when watching TV and outside of myth. Where else may the problem lie?

Trev

---

