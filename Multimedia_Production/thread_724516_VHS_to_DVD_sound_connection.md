---
title: "VHS to DVD sound connection"
date: 2008-03-14
forum: Multimedia Production
---

### Post by cotcot on 2008-03-14
I am capturing old VHS tapes from a camcorder to my pc. Capturing the video is ok but i do not get sound.
I am not sure how to connect the sound. The camcorder has only a yellow and white RCA (composite) connector. If i connect the yellow and the white plug with a cable to the yellow and white connector of the video card in my pc i do not get sound.
Is this connection OK or should i connect the sound output to the microphone in of the video card. (but then i need a cable with an RCA connector at one side and a 3.5 mm audio jack at the other side).
Thanks in advance for any advise.

My video card is  Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)


Here is the terminal info during the capturing after i stoppep it with ctrl C :
> ~$ mencoder -tv norm=PAL:driver=v4l2:width=720:height=576:input=1:fps=25 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o capture.mpg 
MEncoder 2:1.0~rc2-0ubuntu8 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Medion 7134
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO STEREO LANG1 LANG2
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = PAL-BG; 2 = PAL-I; 3 = PAL-DK; 4 = NTSC; 5 = SECAM; 6 = SECAM-DK; 7 = SECAM-L; 8 = SECAM-Lc; 9 = PAL-M; 10 = PAL-Nc; 11 = PAL-60;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 1
 Current format: BGR24
v4l2: current audio mode is : STEREO
Audio block size too low, setting to 16384!
[V] filefmt:9  fourcc:0x32315659  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
PACKET SIZE: 2048 bytes, deltascr: 43885
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [hqdn3d]
Opening video filter: [pp=lb/ha/va/dr]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (720x576 fourcc=3267706d [mpg2])
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Limiting audio preload to 0.4s.
Increasing audio density to 4.
Forcing audio preload to 0, max pts correction to 0.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
INITV: 0.200, 0.160, fps: 25.000

1 duplicate frame(s)!
Pos:  15.8s    394f ( 0%) 17.63fps Trem:   0min   0mb  A-V:0.000 [7096:191]
1 duplicate frame(s)!
Pos:  21.7s    541f ( 0%) 20.20fps Trem:   0min   0mb  A-V:0.000 [7093:191]
Flushing video frames.
Writing index...

Overhead: 1.712% (338558 / 19776898)
Writing header...

Video stream: 7093.841 kbit/s  (886730 B/s)  size: 19259778 bytes  21.720 secs  541 frames

Audio stream:  192.000 kbit/s  (23999 B/s)  size: 520704 bytes  21.696 secs
v4l2: 669 frames successfully processed, 0 frames dropped.


---

### Post by cotcot on 2008-03-15
I made some progress but i am not going to thank meself for it. After having connecting the camcorder with the RCA cable (yellow) and sound with a white RCA to 3.5 mm jack I get sound. However the sound is distorted. I think it is because of the mencoder options because I get the sound normally with the default sound recorder.
Any help on better setting is welcome.
My mencoder instruction is >  mencoder -tv norm=PAL:driver=v4l2:width=720:height=576:input=1:fps=25 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o capture.mpg 


I was also searching for a tutorial or so on the meaning of all the alsamixer parameters (master, PCM, line-in, ...).
Any suggestions.

---

