---
title: "can't play h.264 files correctly"
date: 2010-06-20
forum: Multimedia Software
---

### Post by n00ne on 2010-06-20
I bought a new video camera that outputs HD video in a mp4 format
but when I play the files with mplayer I only get a frame every few
seconds. I can hear the audio but the images just look like a crappy slide show.
on vlc I don't get any image at all just black screen with audio.
I read some posts and installed the restricted formats but nothing changed

any help would be appreciated

---

### Post by ron999 on 2010-06-20
Hi
Use a program such as **mediainfo** to find out just what's inside those mp4 files.
Maybe you've used a bitrate that's too high for mplayer and vlc to handle or a codec that's not supported.

---

### Post by n00ne on 2010-06-20
the bit rate is 12.1 Mbps  what is the limit of mplayer ?
I'm now converting all the videos to avi using winFF.
but it would be nice if I could edit them and watch them in HD.


this is the output I get from mediainfo 

General
Complete name                    : GOPR0011.MP4
Format                           : MPEG-4
Format profile                   : JVT
Codec ID                         : avc1
File size                        : 1.73 GiB
Duration                         : 20mn 26s
Overall bit rate                 : 12.1 Mbps
Encoded date                     : UTC 2009-01-02 15:46:25
Tagged date                      : UTC 2009-01-02 15:46:25
AMBA                             : 

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 2 frames
Format_Settings_FrameMode        : Frame doubling
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 20mn 26s
Bit rate mode                    : Variable
Bit rate                         : 12.0 Mbps
Width                            : 1 280 pixels
Height                           : 960 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Constant
Frame rate                       : 29.970 fps
Original frame rate              : 14.985 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.326
Stream size                      : 1.71 GiB (99%)
Title                            : 	GoPro AVC
Language                         : English
Encoded date                     : UTC 2009-01-02 15:46:25
Tagged date                      : UTC 2009-01-02 15:46:25

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 20mn 26s
Bit rate mode                    : Constant
Bit rate                         : 128 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Stream size                      : 18.7 MiB (1%)
Title                            : 	GoPro AAC
Language                         : English
Encoded date                     : UTC 2009-01-02 15:46:25
Tagged date                      : UTC 2009-01-02 15:46:25

---

### Post by ron999 on 2010-06-20
Hi
I'm not an expert in this area.
But as mediainfo shows, that is a very high bitrate.
And the file size is 1.73 GiB for a 20 minute clip!
Perhaps check to see if there is an option to reduce the bitrate setting on your video camera, then do some experiments with mplayer and VLC.

---

### Post by n00ne on 2010-06-21
I have some other video modes but the lowest quality is 8 Mbps which still doesn't play correctly.

is there any way for me to lower the bitrate after shooting in ubuntu ?

and is this hardware or software limitation, I played the video on another laptop which isn't mine and runs XP and it worked ok but it also had a better hardware. I might buy a new computer but I need to know if this will work under linux.

---

### Post by xzero1 on 2010-06-21
What cpu speed and video card do you have now?

---

### Post by BobLand on 2010-06-21
I can play H.264 in the mov container with VLC.  It plays them better then Quicktime.  Don't know if this will fix your problem but try it.

---

### Post by freestyle45 on 2011-05-13
Did you ever solve this issue?  I'm having the exact same problem with my GoPro HD.  I also have a Casio that outputs 640x480 h.264 files which play fine -- they are in a .MOV container, while the gopro is in .MP4.  Yet the GoPro is as you described above -- a slide show with audio.

I've tried every codec I can find, starting with Ubuntu restricted extras, which of course did nothing... tried default and proprietary video drivers for both an ATI/Radeon card and an Nvidia card with no change...

So it's a high bitrate.  1080p.  Who cares?  This exact hardware plays this exact same file flawlessly with quicktime in WinXP.  Ugh.  Very unimpressed with Linux right now.

---

### Post by gecko_gr on 2011-10-17
try to change at the VLC player
/ Tools / Preferences / Input & Codecs / Codecs ... and set "Skip H.264 in-loop deblocking filter" to "All".

works with my files from the GoPro Hero 960 under Ubuntu 10.11

---

