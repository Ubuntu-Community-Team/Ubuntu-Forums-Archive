---
title: "Playing Video files from a Sony Camera"
date: 2013-03-13
forum: Multimedia Software
---

### Post by appalbarry on 2013-03-13
I can't believe that I've spent an hour trying to play these dumb things on both my Linux box and a Windows machine. Or even to find out what I need.

I have three files given to us by a client. They are video, and were recorded on a Sony camera of some kind. They are called:

AVIN0001.BNP               115.3 MB
AVIN0001.INP                115.3 MB
AVIN0001.INT                172.3 MB

What on earth do I need to play these things?

(For bonus points, what do I need in Windows?)

Thanks!!

---

### Post by SeijiSensei on 2013-03-13
Try installing **mplayer** and see if that works.  You can try running it from the command prompt and see what errors it throws if it cannot play the file by using "mplayer /path/to/AVIN0001.BNP".

Gee, what a surprise.  It looks like a proprietary Sony format.  [This link](http://www.fileinfo.com/extension/bnp) suggests using [this software from Sony](http://vaio-online.sony.com/prod_info/software/picture_motion_browser/).

I like Sony hardware; I own a PS3 and a Bravia television.  But I find anything from Sony having to do with computers to be way too proprietary for my tastes.

---

### Post by appalbarry on 2013-03-13
I'll try mplayer, but VNC couldn't do anything, or Windows Media Player on the Windows machine.  I actually already found the PMB page. Interesting to note that there's NO DOWNLOAD LINK on the page!!  Wound up downloading two Windows apps from the Sony site, neither of which will open these things.  Idiotic.  Stupid web site too.

---

### Post by Appalbarry2 on 2013-03-13
(Minor note - this site is refusing to let me log in in my original ID, even after changing passwords a couple of times. So here I am, v.2)

**mplayer AVIN0001.BNP** gives me:

Seek failed
Seek failed
Seek failed
Seek failed
Seek failed
Seek failed

Endlessly until I Break.

**mplayer AVIN0001.INP** Gives:

MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing AVIN0001.INP.
Detected file format: MPEG-PS
MPEG: FATAL: EOF while searching for sequence header.
Video: Cannot read properties.
Load subtitles in .
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[mp2float @ 0x7ff75a3c2540]Header missing
[mp2float @ 0x7ff75a3c2540]Header missing
[mp2float @ 0x7ff75a3c2540]Header missing
[mp2float @ 0x7ff75a3c2540]Header missing
[mp2float @ 0x7ff75a3c2540]Header missing
ad_ffmpeg: initial decode failed
ADecoder init failed :(
Could not open audio decoder ffmpeg.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[mp2 @ 0x7ff75a3c2540]Header missing
[mp2 @ 0x7ff75a3c2540]Header missing
[mp2 @ 0x7ff75a3c2540]Header missing
[mp2 @ 0x7ff75a3c2540]Header missing
[mp2 @ 0x7ff75a3c2540]Header missing
ad_ffmpeg: initial decode failed
ADecoder init failed :(
Could not open audio decoder ffmpeg.
Requested audio codec family [mad] (afm=libmad) not available.
Enable it at compilation.
Opening audio decoder: [hwmpa] MPEG audio pass-through (fake decoder)
AUDIO: 11025 Hz, 2 ch, mpeg2, 176.0 kbit/49.89% (ratio: 22000->44100)
Selected audio codec: [hwmpa] afm: hwmpa (MPEG audio pass-through for hardware MPEG decoders)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
[AO_ALSA] Format mpeg2 is not supported by hardware, trying default.
AO: [alsa] 11025Hz 2ch s16le (2 bytes per sample)
[format] Sample format big-endian MPEG-2 not yet supported 
[libaf] Reinitialization did not work, audio filter 'format' returned error code -2
[libaf] Unable to setup filter system can not meet sound-card demands, please send bugreport. 
Couldn't find matching filter/ao format!
Audio: no sound
Video: no video

[B]mplayer AVIN0001.INT gives me:

[/B]
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing AVIN0001.INT.
Failed to recognize file format.




Exiting... (End of file)

PMB is a proprietary Sony product that can't be downloaded and apparently even if you get a copy has to be activated with the applicable Sony camera plugged into the USB.

I also tried plugging the USB stick with the files into our Sony Blu-Ray player, and even it won't open them.

After two plus hours, I've concluded that there is no practical way to open these stupid files.

---

### Post by Appalbarry2 on 2013-03-13
One more update. Found a downloadable version of PMB for Windows here [http://esupport.sony.com/US/perl/swu-download.pl?upd_id=5134&SMB=YES](http://esupport.sony.com/US/perl/swu-download.pl?upd_id=5134&SMB=YES) **364 MB!!!!  **Refused to install under Vista because I'm not running a Vaio computer.

---

### Post by FakeOutdoorsman on 2013-03-13
I share your frustration. A client asked me to try to decode some videos that were evidence for a murder case. It was a proprietary format from a security camera and I only had a day or two to look at them. Unfortunately the camera company was out of business and any apparently related software I was able to scrounge was useless. As far as I could tell it was simply MPEG-1 video or MPEG-2 video that they took a dump on to make it proprietary but I didn't figure it out in time.

---

### Post by Appalbarry2 on 2013-03-14
Sony Replies:

[FONT=arial]Thank you for contacting Sony Support.[/FONT]

[FONT=arial]I understand that you're trying to playback the videos recorded by a Sony Camera. AVIN0001.BNP, AVIN0001.INP and [/FONT][AVIN0001.INT]("http://avin0001.int/")[FONT=arial] are Image Management files stored in the AVF_INFO folder of Camera. They're not meant for play back. The recorded videos will be stored in AVCHD or MP_ROOT folder in the Camera. They will have .MPG, .MP4, .MTS or .M2TS file extension.[/FONT]

[FONT=arial]The Software required to playback the videos are supplied with Sony Cameras and Camcorders and they're usually available for download from our support website using the model number of the Camera or Camcorder. You may contact the client to obtain the proper video files. You can also check the availability of the Software at our support website after obtaining the model number of the Camera/Camcorder.[/FONT]

[http://esupport.sony.com/US/p/select-system.pl?DIRECTOR=DRIVER](http://esupport.sony.com/US/p/select-system.pl?DIRECTOR=DRIVER)

[FONT=arial]Note: Software supplied with the Sony Camera/Camcorder are not compatible with Linux Operating System.[/FONT]

[FONT=arial]Thank you for understanding.[/FONT]

[FONT=arial]Sony of Canada, Ltd.[/FONT]
[FONT=arial]C6EH[/FONT]
[FONT=arial]William[/FONT]

---

### Post by evilsoup on 2013-03-14
You could maybe try wine with the Sony software.

---

### Post by sudodus on 2013-03-14
> **Appalbarry2 said:**
> Sony Replies:
...
[FONT=arial]I understand that you're trying to playback the videos recorded by a Sony Camera. AVIN0001.BNP, AVIN0001.INP and [/FONT][AVIN0001.INT]("http://avin0001.int/")[FONT=arial] are Image Management files stored in the AVF_INFO folder of Camera. They're not meant for play back. The recorded videos will be stored in AVCHD or MP_ROOT folder in the Camera. They will have .MPG, .MP4, .MTS or .M2TS file extension.[/FONT]
[FONT=arial]...[/FONT]
  We can play [FONT=arial]files with .MPG, .MP4, .MTS or .M2TS file extension in linux, so your problem is now 'only' to get the real video clip from your client ;-) Let's hope [s]he has not deleted them. [/FONT]

---

### Post by krishna.988 on 2013-03-15
You were asking what works on Windows...

Install Sony Picture motion browser software in Windows from SONY site to view these files.

---

### Post by Harolddurnez on 2014-01-20
Hi, 
I am in the same frustrating boat..
And as per thread below do not have any files in the AVCHD directory. 
Nor the option to ask 'client' for the video files.

Have you (or anyone else) since figured out a way to playback these formats? Either Windows or Mac?

Thanks.

---

### Post by sudodus on 2014-01-20
Welcome to the Ubuntu Forums Harolddurnez :-)

I think you have a better chance to get help if you start an old thread with a good title, and describe your problem as well as possible.

Anyway, please tell us what file type you have, and if you have been able to transfer the files from the camera to the computer!

There are several good video players available, the default one will vary between the different flavours of Ubuntu, and you can install many other video players as well as codecs if necessary.

Another problem is that old hardware might not be able to play high definition video without problems.

In order to give relevant help, we need to know more about your files, your computer and operating system (version/flavour of Ubuntu, Windows, MacOS).

---

### Post by berthold1 on 2014-08-31
I have a Sony hard disk camcorder and I have never had a problem. Downloading the files (from MP_ROOT) to Ubuntu and playing them has always worked.

---

