---
title: "Kino exporting no nothing"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by defrex on 2007-08-10
Hello, and thanks in advance for the help.

I'm using kino with my dv cam, and everything seems to be working fine, until I export. I've tried ffmpeg, mencode, and the mpeg encoder built in. After spending the time it would take to encode, either the exported file is completely empty or non-existent. No error messages. I'm really not sure what could be going on.

I'm using feisty, and kino 0.9.2. Any help would be great.

defrex

---

### Post by defrex on 2007-08-10
shameless bump

---

### Post by defrex on 2007-08-11
Please tell me I'm not going to have to borrow my roommates mac... I'll never live it down.

---

### Post by zhkent on 2007-08-11
Maybe gstreamer codecs?

---

### Post by defrex on 2007-08-11
I have 'em all.

---

### Post by dabl on 2007-08-11
I was trying to use Kino for editing big .mpg (mpeg2) files from VHS tape that I captured through a PVR-150 card.  You are correct, it gets flaky on the "export" thing -- it crashes, and it doesn't seem to created the correct file format.

I'm back to Avidemux, warts and all.  At least I've figured out how to come up with a viable .mpg export file.  :rolleyes:

---

### Post by defrex on 2007-08-11
Another app... I feel dumb for not trying it already. Thanks, I'll give it a shot when I get home from work.

---

### Post by defrex on 2007-08-12
Avidemux won't open the .dv files kino made. Is there a way to import them?

---

### Post by zhkent on 2007-08-12
Kino would not export for me either until I got everything it needed. 

from kino's website:

Here's the list of required components. You can usually install them from your Linux distribution's repository.

    * libglade2
    * gtk 2.6 (and related dependencies)
    * libxml2
    * libdv
    * libsamplerate
    * libasound
    * libXv
    * libpthread
    * ffmpeg, libavformat, and libavcodec
    * libraw1394
    * libiec61883
    * libavc1394

Some optional, but recommended runtime utilities include:

    * ffmpeg2theora
    * sox
    * vorbis-tools
    * lame
    * mjpegtools
    * dvdauthor
    * 'Q' dvdauthor
    * growisofs
    * mencoder

---

### Post by defrex on 2007-08-12
:confused:

I installed all the packages, but still no luck...

---

### Post by Amazona aestiva on 2007-08-15
Kino 1.0.0:
[http://www.getdeb.net/download.php?release=871&fpos=0]("http://www.getdeb.net/download.php?release=871&fpos=0")
It is better than 0.9.2;)

---

### Post by mega on 2007-08-22
> **Amazona aestiva said:**
> Kino 1.0.0:
[http://www.getdeb.net/download.php?release=871&fpos=0]("http://www.getdeb.net/download.php?release=871&fpos=0")
It is better than 0.9.2;)

does not fix it

I get the exact same message, invalid codec

where do you get the codec's to export to something windows users can understand?

---

### Post by Amazona aestiva on 2007-08-22
See my signature! Read it carefully!
I ment use the first code.

---

### Post by mega on 2007-08-22
> **Amazona aestiva said:**
> See my signature! Read it carefully!
I ment use the first code.

I may be missing one or two of these packages, I'll try them tonight


when I run kino from the shell I can see the error when I try to go to another format about missing codec, I can export to divx, but windows users cannot play the video


what is the best format for windows users?

---

### Post by Amazona aestiva on 2007-08-22
I use mencoder for external encoder, and its xvid is perfect under windows.
And if you want to play something under Windows, You should use:
[http://ftp.freenet.de/pub/filepilot/windows/multimedia/video/k-lite_codec_pack/klcodec330f.exe]("http://ftp.freenet.de/pub/filepilot/windows/multimedia/video/k-lite_codec_pack/klcodec330f.exe")

---

### Post by mega on 2007-08-22
> **Amazona aestiva said:**
> I use mencoder for external encoder, and its xvid is perfect under windows.
And if you want to play something under Windows, You should use:
[http://ftp.freenet.de/pub/filepilot/windows/multimedia/video/k-lite_codec_pack/klcodec330f.exe]("http://ftp.freenet.de/pub/filepilot/windows/multimedia/video/k-lite_codec_pack/klcodec330f.exe")

exactly how do I get this exe file to work with kino?

I just tried playing the xvid, I get sound but no video

---

### Post by Amazona aestiva on 2007-08-22
NO! the exe is for Windows users!
This is that you need:
```
sudo apt-get install gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-audiofile gstreamer0.8-cdio gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-misc gstreamer0.10-alsa gstreamer0.10-doc gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-gnonlin gstreamer0.10-gnonlin-dev gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-doc gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-base-doc gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-sdl gstreamer0.10-tools gstreamer0.10-x gstreamer-tools irb1.8 liba52-0.7.4 libbreakpoint-ruby1.8 libcdaudio1 libcmdparse2-ruby1.8 libdaemonize-ruby1.8 libdvdnav4 libdvdread3 libfaac0 libfaad2-0 libfreebob0 libgems-ruby1.8 libglib2-ruby libgsm1 libgstreamer0.8-0 libgstreamer0.8-ruby libgstreamer0.10-0 libgstreamer0.10-0-dbg libgstreamer0.10-ruby1.8 libgstreamer-gconf0.8-0 libgstreamer-perl libgstreamer-plugins0.8-0 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-pulse0.10-0 libid3tag0 libjack0.100.0-0 libjinglebase0.3-0 libjinglep2p0.3-0 libjinglexmllite0.3-0 libjinglexmpp0.3-0 liblame0 liblog4r-ruby1.8 libmad0 libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 libmpeg2-4 libncurses-ruby1.8 libopenssl-ruby1.8 libpulse0 libquicktime0 libreadline-ruby1.8 libruby1.8 libruby1.8-dbg libruby1.8-extras libsidplay1 libsoundtouch1c2 libswfdec0.3 libwavpack1 libxvidcore4 libxvidcore4-dev rdoc1.8 ruby1.8 ruby ffmpeg mencoder mplayer xvid4conf
```
This contains every GStreamer, the mencoder and the ffmpeg codec.

---

### Post by mega on 2007-08-22
> **Amazona aestiva said:**
> NO! the exe is for Windows users!
This is that you need:


[QUOTE=Amazona aestiva;3234250]NO! the exe is for Windows users!

ahh, I dont have permission to install software here at work, if it does not play on windows by default, I cant play it

what is the proper codec/format for a standard windows machine client?

---

### Post by Amazona aestiva on 2007-08-22
The exe is a codec pack. Windows need something like it to play files well. (Windows Media Player has never worked for me!)

---

### Post by mega on 2007-08-22
again, I can NOT load codec's on my windows machine, it is not allowed, we are locked out of installing software


I installed all the packages you referenced, I still get the exact same error from kino

I tried to export broadband quality h.264

Unsupported codec for output stream #0.0

>> Export::activate()
>>> output rate is 48000, adjusted rate is 48000
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, dv, from 'pipe:':
  Duration: N/A, start: 0.000000, bitrate: 28771 kb/s
  Stream #0.0: Video: dvvideo, yuv411p, 720x480, 28771 kb/s, 29.97 fps(r)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, mp4, to '/home/mega/vids/dogvscat.mp4':
  Stream #0.0: Video: 0x0000 (hq), yuv411p, 320x240, q=2-31, 500 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: 0x0000, 32000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0

---

### Post by Amazona aestiva on 2007-08-23
Perhaps Kino need a reinstall to use the new packs...
Have you installed Kino 1.1.1, or older?

And that's strange. I've never had a problem like this with Kino.

---

### Post by mega on 2007-08-23
> **Amazona aestiva said:**
> Perhaps Kino need a reinstall to use the new packs...
Have you installed Kino 1.1.1, or older?

And that's strange. I've never had a problem like this with Kino.

I uninstalled the .91 or whatever ubuntu ships with, installed 1.0, then installed 1.1.1 last night

all do the exact same thing

its' almost like my encoder is invalid or compiled without support for the other codecs


I've yet to make a video with linux that anyone at work can play, it's really starting to get frustrating

---

### Post by Amazona aestiva on 2007-08-23
Has export ever worked for you?

---

### Post by mega on 2007-08-23
> **Amazona aestiva said:**
> Has export ever worked for you?

yes, I can export divx and flash movies, neither of which anyone can play on a windows machine

---

### Post by Amazona aestiva on 2007-08-23
DivX means > XviD MPEG-4 AVI Single Pass (MEncoder)
This CAN be played in Windows if a good codec pack is installed.

---

### Post by mega on 2007-08-23
> **Amazona aestiva said:**
> DivX means 
This CAN be played in Windows if a good codec pack is installed.

we cannot install codec packs

in fact we cannot install ANY software, only the system administrators can, and they wont, per DIACAP rules for the government

---

### Post by Amazona aestiva on 2007-08-23
Understand but Windows Media Player is VERY stupid. Without codec packs it is almost impossible to play anything!

I found that there is a bug in the ffmeg or kino. Thats why it isn't working.

Don't give up! I'll look for a solution.(If there is any)

---

### Post by mega on 2007-08-23
> **Amazona aestiva said:**
> Understand but Windows Media Player is VERY stupid. Without codec packs it is almost impossible to play anything!

I found that there is a bug in the ffmeg or kino. Thats why it isn't working.

Don't give up! I'll look for a solution.(If there is any)

I'm thinking it's ffmpeg that's doing it

is there any way to add more codec options to kino?  wmv would be nice, windows can play that

---

### Post by mega on 2007-08-23
here's my ffmpeg version

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
configuration: --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
libavutil version: 0d.49.0.0
libavcodec version: 0d.51.11.0
libavformat version: 0d.50.5.0
built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)

---

### Post by Meurglys on 2007-08-23
Plain .mpg files should play on a Windows box without any additional codecs. Just make sure it's mgp 1, not mpg 2 which requires codecs to be installed. Good luck. :)

For more file formats, check this table:
[http://www.microsoft.com/windows/windowsmedia/player/9series/playererrors.aspx#80040255_0x00000000](http://www.microsoft.com/windows/windowsmedia/player/9series/playererrors.aspx#80040255_0x00000000)

---

### Post by Amazona aestiva on 2007-08-23
I solved it!
Try This:
```
sudo apt-get remove ffmpeg
```
Now download and install this:[http://ftp.kfki.hu/linux/ubuntu/pool/main/libr/libraw1394/libraw1394-5_0.10.1-1.1ubuntu1_i386.deb]("http://ftp.kfki.hu/linux/ubuntu/pool/main/libr/libraw1394/libraw1394-5_0.10.1-1.1ubuntu1_i386.deb")
After it This:[http://security.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/ffmpeg_0.cvs20050918-5ubuntu1.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/ffmpeg_0.cvs20050918-5ubuntu1.1_i386.deb")
Try Kino!
Is it working?????

After this I tested:
MPEG-4 AVI Single Pass_every profile -> Succeed:)
MPEG-4 AVI Dual Pass_every profile- > Succeed:)
DVD-video Single Pass_every profile -> Succeed:)
DVD-video Dual Pass_every profile -> Succeed:)

Note:Perhaps Windows Media Player won't play these files too.(I said that it is quite stupid, it needs codec packs!)

---

