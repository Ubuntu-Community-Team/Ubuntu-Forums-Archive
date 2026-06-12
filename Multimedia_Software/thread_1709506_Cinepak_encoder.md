---
title: "Cinepak encoder?"
date: 2011-03-18
forum: Multimedia Software
---

### Post by hellocatfood on 2011-03-18
Is there a way to encode video using the Cinepak codec on Linux? FFMPEG can only decode.

---

### Post by hellocatfood on 2011-03-18
I've since gotten a bit of help from the kind folk over at [videohelp](http://forum.videohelp.com/threads/333037-Cinepak-encoder?p=2065258) but I think I may be experiencing a program error. Can anyone test this to help me?

Just to clarify my issue I'll provide a sample video and my process. I'll be working with this short clip [http://ubuntuone.com/p/iJr/](http://ubuntuone.com/p/iJr/)

I converted this to an avi in the rgb24 colourspace
```
ffmpeg -i vid.mov -vcodec png -pix_fmt bgr24 outfile.avi
```I then tried to convert this to an avi that uses the cinepak codec
```
mencoder outfile.avi -vf format=bgr24 -ovc vfw -xvfwopts codec=iccvid.dll -oac mp3lame -o outfile_2.avi
```This is where I got my segmentation fault:
```
MP3 audio selected.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [flip]
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0xb6315fc0]using unscaled rgb24 -> bgr24 special converter
Opening video filter: [expand]
Expand: -1 x -1, -1 ; -1, osd: 0, aspect: 0.000000, round: 1
Starting compression:
 Input format:
  biSize 40
  biWidth 1280
  biHeight 720
  biPlanes 1
  biBitCount 24
  biCompression 0x0 ('')
  biSizeImage 2764800
 Output format:
  biSize 40
  biWidth 1280
  biHeight 720
  biPlanes 1
  biBitCount 24
  biCompression 0x64697663 ('cvid')
  biSizeImage 254100
 Output format after query/begin:
  biSize 40
  biWidth 1280
  biHeight 720
  biPlanes 1
  biBitCount 24
  biCompression 0x64697663 ('cvid')
  biSizeImage 254100
Segmentation fault
```Just to be sure I tried this code with both bgr24 and rgb24 arguments. Same results

I'm surprised that it still tries to convert to bgr24 when I've specifically told ffmpeg to use bgr24 in the first place.

As for the segfault, is this a problem with the software or the video that I'm using?

---

### Post by ron999 on 2011-03-18
Same result as you.:(
```
ron@ubuntu:~$ mencoder outfile.avi -vf format=bgr24 -ovc vfw -xvfwopts codec=iccvid.dll -oac mp3lame -o outfile_2.avi
MEncoder SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x58b6e9a
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MPNG]  1280x720  24bpp  23.976 fps  183849.6 kbps (22442.6 kbyte/s)
[V] filefmt:3  fourcc:0x474E504D  size:1280x720  fps:23.976  ftime:=0.0417
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Loading codec DLL: 'iccvid.dll'
Loaded DLL driver iccvid.dll at 6ea20000
HIC: a4a7ab8
568 - 568 - 568
Compressor type: 63646976
Compressor subtype: 64697663
Compressor flags: 47, version 65536, ICM version: 260
Flags: quality
ICCompressGetFormatSize ret: 40
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [format fmt=bgr24]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffpng] vfm: ffmpeg (FFmpeg PNG)
==========================================================================
MP3 audio selected.
VDec: vo config request - 1280 x 720 (preferred colorspace: RGB 24-bit)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using RGB 24-bit as output csp (no 6)
Opening video filter: [flip]
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0x8985f80]using unscaled rgb24 -> bgr24 special converter
Opening video filter: [expand]
Expand: -1 x -1, -1 ; -1, osd: 0, aspect: 0.000000, round: 1
Starting compression:
 Input format:
  biSize 40
  biWidth 1280
  biHeight 720
  biPlanes 1
  biBitCount 24
  biCompression 0x0 ('')
  biSizeImage 2764800
 Output format:
  biSize 40
  biWidth 1280
  biHeight 720
  biPlanes 1
  biBitCount 24
  biCompression 0x64697663 ('cvid')
  biSizeImage 254100
 Output format after query/begin:
  biSize 40
  biWidth 1280
  biHeight 720
  biPlanes 1
  biBitCount 24
  biCompression 0x64697663 ('cvid')
  biSizeImage 254100
Segmentation fault
ron@ubuntu:~$ 

```

---

### Post by hellocatfood on 2011-03-18
Drats!

Have you tried any other parameters and got it working? I think I'll just have to go and report an mencoder bug as well

---

### Post by andrew.46 on 2011-03-18
Your commandlines worked on my system using the latest git FFmpeg / svn MEncoder producing the following result:

```

Input #0, avi, from 'outfile_2.avi':
  Metadata:
    encoder         : MEncoder SVN-r33083-4.5.2
  Duration: 00:00:04.00, start: 0.000000, bitrate: 25335 kb/s
    Stream #0.0: Video: cinepak, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 288 kb/s

```

I have posted the resulting file here:

```
wget http://www.andrews-corner.org/tmp/outfile_2.avi
```

I suspect that the advice on MPlayer-users will be to upgrade to the latest development offering, there are guides for the latest MPlayer and FFmpeg on these forums. (The MPlayer guide needs a few additions to build the long neglected MEncoder as well).

Andrew

---

### Post by hellocatfood on 2011-03-18
Thanks for the help. I'm not able to upgrade at the moment (don't want to upgrade during project development), but at least I know it's a problem that has been fixed

---

### Post by andrew.46 on 2011-03-18
> **hellocatfood said:**
> Thanks for the help. I'm not able to upgrade at the moment (don't want to upgrade during project development), but at least I know it's a problem that has been fixed

Mind you if you are using the stock Natty Narwhal MEncoder it might be worth your while to file a bug report against the package. Reinhard Tartler is usually pretty good with such things.

---

### Post by hellocatfood on 2011-03-18
So the one in Natty isn't one with a fix for my problem?

I'm still using the Maverick version from medibuntu

---

### Post by andrew.46 on 2011-03-18
> **hellocatfood said:**
> So the one in Natty isn't one with a fix for my problem?

I'm still using the Maverick version from medibuntu

Looks like both Medibuntu Maverick and Natty are using MPlayer rc4 so I *suspect* there may be no difference. Unfortunately I do not have a Natty installation + repository MPlayer to test this on and in reality I am far happier building my own MPlayer packages anyway :). Hopefully some enterprising person with a copy of Natty Narwhal can test this....

BTW did the file I created work well enough on your system?

Andrew

---

### Post by hellocatfood on 2011-03-18
The file worked perfectly!

Could I ask one more favour of you? Would you be able to encode the video file using Cinepak again but at a really really low bit rate?

To put this all into context I like to explore glitches and compression artifacts and I've heard that there's really weird glitches when you encode video at low bit rates using Cinepak codec. My website (in my sig) probably explains it a lot better!

---

### Post by andrew.46 on 2011-03-18
> **hellocatfood said:**
> Could I ask one more favour of you? Would you be able to encode the video file using Cinepak again but at a really really low bit rate?

This could take a little longer as it looks like that to alter bitrates when encoding with the Video For Windows codec family you also need to build vfw2menc either using wine or mingw on Windows. Details at the bottom of this page:

7.6.  Encoding with the Video For Windows codec family 
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-video-for-windows.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-video-for-windows.html)

and the actual usage of this application and how to incorporate it into MEncoder syntax is not entirely clear to me from either the man pages or the html docs. Mind you this will probably be the hint in -xvfwopts:

> 
compdata=<file>
              The name of the codec settings file (like firstpass.mcf) created
              by vfw2menc.


I shall have a look at vfw2menc and see what happens :)

Andrew

**Edit:** You may be out of luck as there appear to be no options within the codec:

```

wine vfw2menc.exe.so -f cvid -d iccvid.dll -s onepass.mcf
[...]
Z:\home\andrew\Desktop\vfw2menc.exe.so: The driver doesn't provide a configure dialog

```

---

### Post by hellocatfood on 2011-03-19
> **andrew.46 said:**
> **Edit:** You may be out of luck as there appear to be no options within the codec

That's a real big shame :-( When I upgrade I'll also ask on the mailing list but it looks like you may be right about this one

Thanks for all of your help

---

### Post by andrew.46 on 2011-03-19
> **hellocatfood said:**
> Thanks for all of your help

It has been a pleasure and I have learned about Cinepak encoding with MEncoder which I had no idea about before :).

Andrew

---

