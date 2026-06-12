---
title: "Can't play avi files"
date: 2015-07-07
forum: Multimedia Software
---

### Post by BobvanderPoel on 2015-07-07
I was given a disk with some AVI files on it. I've tried all my various players ... none will play the video. Mplay, totem and VLC all play the audio. No video. Other videos work fine.

Funny, I tried the same disk on a windows 7 virtual install ... the video works, no audio (yes, audio works for other things).

I'm at my wits end with this. Here's a listing of the file:

exiftool *avi
ExifTool Version Number         : 9.46
File Name                       : Crimea.avi
Directory                       : .
File Size                       : 29 MB
File Modification Date/Time     : 2015:05:11 09:13:15-07:00
File Access Date/Time           : 2015:07:07 11:54:23-07:00
File Inode Change Date/Time     : 2015:07:07 11:53:59-07:00
File Permissions                : rw-r--r--
File Type                       : AVI
MIME Type                       : video/x-msvideo
Frame Rate                      : 25
Max Data Rate                   : 76.11 kB/s
Frame Count                     : 9399
Stream Count                    : 2
Stream Type                     : Audio
Audio Codec                     : .
Audio Sample Rate               : 43.07
Audio Sample Count              : 16194
Quality                         : Default
Sample Size                     : Variable
Encoding                        : AAC
Num Channels                    : 2
Sample Rate                     : 44100
Avg Bytes Per Sec               : 12000
Bits Per Sample                 : 16
Video Codec                     : H264
Video Frame Rate                : 25
Video Frame Count               : 9399
Image Width                     : 480
Image Height                    : 360
Planes                          : 1
Bit Depth                       : 24
Compression                     : H264
Image Length                    : 518400
Pixels Per Meter X              : 0
Pixels Per Meter Y              : 0
Num Colors                      : Use BitDepth
Num Important Colors            : All
Software                        : Lavf55.12.100
Duration                        : 0:06:15
Image Size                      : 480x360

Does this light up any bells :)

Thanks.

---

### Post by Rob Sayer on 2015-07-08
Maybe  wacky codec packs were used to produce that file.  Fortunately that's a Windoze issue.  Linux is better behaved.  Opening it with mediainfo would give better info.

I can tell you one thing though.  Putting h.264 video in an avi container is a dead giveaway that whoever encoded it doesn't know what the frak he or she is doing.  That wouldn't in itself stop any decent software player from dealing with it, but it usually indicates other problems.

---

### Post by BobvanderPoel on 2015-07-08
> **Rob Sayer said:**
> Maybe  wacky codec packs were used to produce that file.  Fortunately that's a Windoze issue.  Linux is better behaved.  Opening it with mediainfo would give better info.

I can tell you one thing though.  Putting h.264 video in an avi container is a dead giveaway that whoever encoded it doesn't know what the frak he or she is doing.  That wouldn't in itself stop any decent software player from dealing with it, but it usually indicates other problems.

I did get it to play (audio and video) on the win7 virtual on my linux box using VLC. But, vlc continues to barf on linux. Here's the mediainfo stuff:

 bob$ mediainfo Cri*avi
General
Complete name                            : Crimea.avi
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 28.6 MiB
Duration                                 : 6mn 16s
Overall bit rate mode                    : Variable
Overall bit rate                         : 637 Kbps
Writing application                      : Lavf55.12.100

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Baseline@L2.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 1 frame
Codec ID                                 : H264
Duration                                 : 6mn 15s
Bit rate                                 : 528 Kbps
Width                                    : 480 pixels
Height                                   : 360 pixels
Display aspect ratio                     : 4:3
Frame rate mode                          : Variable
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.122
Stream size                              : 23.6 MiB (83%)

Audio
ID                                       : 0
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format version                           : Version 2
Format profile                           : LC
Muxing mode                              : ADTS
Codec ID                                 : FF
Duration                                 : 6mn 16s
Bit rate mode                            : Variable
Bit rate                                 : 96.0 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 4.30 MiB (15%)
Alignment                                : Aligned on interleaves
Interleave, duration                     : 40 ms (1.00 video frame)

An acquaintance gave my wife this disk with about 20 videos on it. No idea how they were made, etc. But I suspect he dl'd them from somewhere and stuck them on the disk. I've not bothered to ask ... he'll just tell me they work fine on his windows box :)

BTW, I copied one of the files to my android tablet. It told me the file was unrecognised.

---

### Post by FakeOutdoorsman on 2015-07-08
Please provide a sample file if possible.

---

### Post by BobvanderPoel on 2015-07-08
> **FakeOutdoorsman said:**
> Please provide a sample file if possible.

I copied one of the files to my web site. I'm not sure about the legal status of all this, but I'm pretty sure it's okay. I'll leave it up for a few days anyway and hopefully someone can figure out the problem.

    [http://mellowood.ca/Crimea.avi](http://mellowood.ca/Crimea.avi)

---

### Post by mc4man on 2015-07-08
terribly done vid - from ffprobe,
h264 @ 0x2d41260] illegal POC type 6
[h264 @ 0x2d41260] AVC: nal size 1119884762
[h264 @ 0x2d41260] missing picture in access unit with size 578
[h264 @ 0x2d41260] non-existing PPS 6 referenced
    Last message repeated 39 times
will play in mplayer or mpv or any frontend that uses mplayer or mpv
(- smplayer with mplayer cannot have time position saved to replay this vid..

---

### Post by FakeOutdoorsman on 2015-07-08
Plays for me with ffplay version N-73454-g9174866 and VLC 2.2.1, but I'm using Arch, not Ubuntu. Seeking is problematic. Lots of the PPS errors as mentioned by mc4man.

---

### Post by BobvanderPoel on 2015-07-08
> **mc4man said:**
> terribly done vid - from ffprobe,
h264 @ 0x2d41260] illegal POC type 6
[h264 @ 0x2d41260] AVC: nal size 1119884762
[h264 @ 0x2d41260] missing picture in access unit with size 578
[h264 @ 0x2d41260] non-existing PPS 6 referenced
    Last message repeated 39 times
will play in mplayer or mpv or any frontend that uses mplayer or mpv
(- smplayer with mplayer cannot have time position saved to replay this vid..

Yeah well ... no questions about the issue that it's badly done ... but not my issue :)

I tried mplayer and mpv and got the same "no video" result. Just a gray window. I'm wondering if I'm missing some kind of library. 

I'm running Mint 7.2 and now wondering if I have the latest mplayer: MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Mind you, it didn't work on ubuntu running 14.04 either.

---

### Post by BobvanderPoel on 2015-07-08
The odd thing is that VLC won't run it either. In my past experience VLC plays just about anything I have thrown at it.

---

### Post by mc4man on 2015-07-08
> **FakeOutdoorsman said:**
> Plays for me with ffplay version N-73454-g9174866 and VLC 2.2.1, but I'm using Arch, not Ubuntu. Seeking is problematic. Lots of the PPS errors as mentioned by mc4man.
Vlc works here if I use the one I have built off of FFmpeg. (vlc-3.x). If I use vlc 2.2.1 off of libav it either crashes or just green screen depending on which video out I set in vlc (normal here is opengl on Intel Haswell gpu

---

### Post by mc4man on 2015-07-08
> **BobvanderPoel said:**
> Yeah well ... no questions about the issue that it's badly done ... but not my issue :)

I tried mplayer and mpv and got the same "no video" result. Just a gray window. I'm wondering if I'm missing some kind of library. 

I'm running Mint 7.2 and now wondering if I have the latest mplayer: MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Mind you, it didn't work on ubuntu running 14.04 either.
Don't know mint, assume you mean Mint 17.2. If  it's based on 14.04 then the default mplayer is old. You could use mplayer from here if desired, I update it only once & a while now as mplayer dev is slow...

[https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test](https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test)

Which mpv are you using?, as mentioned  it works fine here (using -vo=opengl-hq on Intel gpu

---

### Post by BobvanderPoel on 2015-07-08
> **mc4man said:**
> Vlc works here if I use the one I have built off of FFmpeg. (vlc-3.x). If I use vlc 2.2.1 off of libav it either crashes or just green screen depending on which video out I set in vlc (normal here is opengl on Intel Haswell gpu

Okay, I just grabbed 2.2.1 from a PPA. No joy with that. 

3.x ? Are you sure? Can't find that anywhere. Assuming you mean 2.2? So, do I need to compile it here or can I download one with ffmpeg?

---

### Post by BobvanderPoel on 2015-07-08
I just checked an my windows vlc is 2.2.1 (same as the PPA). Must be the lib linking that's different.

So, if this is going to be a complete pain ... any ideas about just converting the vid to something that will play?

---

### Post by mc4man on 2015-07-08
> **BobvanderPoel said:**
> Okay, I just grabbed 2.2.1 from a PPA. No joy with that. 

3.x ? Are you sure? Can't find that anywhere. Assuming you mean 2.2? So, do I need to compile it here or can I download one with ffmpeg?
3.x is the current vlc dev version. As far as vlc 2.2 I'm not aware of any ppa's that offer one that uses ffmpeg over libav.

(- I used to use ffmpeg in one ppa's vlc build  but switched back to libav because of an issue with dvd menus created with devede or dvdstyler if vlc was built off of ffmpeg. Atm vlc seems to base on libav but I believe the libav 'dominos' are going to start falling soon which may or may not be a good thing. Likely more good than bad.

You could build your own vlc using ffmpeg, there is a guide in this forum that should work for either current dev or can be used on the vlc 2.2 source.
(or just use mplayer or mpv..

---

### Post by BobvanderPoel on 2015-07-08
Got it to work!

  MPlayer SVN-r37401 (C) 2000-2012 MPlayer Team

is just fine.

Thanks all!

---

