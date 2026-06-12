---
title: "Help Converting MKV to WMV"
date: 2008-11-15
forum: Multimedia Software
---

### Post by ThaAllGood1 on 2008-11-15
New to converting video files and fairly new to Ubuntu so please bare with me.  Also I am currently using 8.10

What I am trying to do is to convert MKV files (most of which or 70op) to a WMV file, also keeping the 5.1 sound as well.  I have found away to do this in XP so I know it is possible but I am trying to free myself of MS, sure most of you can understand that.

TIA

---

### Post by lovinglinux on 2008-11-15
If you are trying to free yourself of MS then you shouldn't convert your videos to **WMV**, which means "**W**indows **M**edia **V**ideo".


> **http://en.wikipedia.org/wiki/WMV]

Windows Media Video (WMV) is a compressed video file format for several proprietary codecs developed by Microsoft. The original codec, known as WMV, was originally designed for Internet streaming applications, as a competitor to RealVideo. The other codecs, such as WMV Screen and WMV Image, cater for specialized content. Through standardization from the Society of Motion Picture and Television Engineers (SMPTE),[1][2] WMV has gained adoption for physical-delivery formats such as HD DVD and Blu-ray Disc[3][4].[/QUOTE]

WMV is not a good format/container/codec in my opinion, while MKV is a feature-rich container, with support for multiple audio tracks and subtitles.

[QUOTE=http://en.wikipedia.org/wiki/WMV]

Microsoft claims that WMV 9 provides a compression ratio that is two times better than MPEG-4 , and three times better than MPEG-2 said:**
>  Microsoft also claims that WMV 9 is 15-50% better than WMV 8 in terms of compression efficiency.[18] One test report published in January 2005, however, showed that WMV 9 had worse compression efficiency than WMV 8.[19] Many 3rd party WMV compilers have had worse performance than Windows Movie Maker.

[QUOTE=URL="http://en.wikipedia.org/wiki/MKV]

The Matroska Multimedia Container is an open standard free Container format, a file format that can hold an unlimited number of video, audio, picture or subtitle tracks inside a single file.[1] It is intended to serve as a universal format for storing common multimedia content, like movies or TV shows. Matroska is similar in conception to other containers like AVI, MP4 or ASF, but is entirely open in specification, with implementations consisting mostly of open source software. Matroska file types are .MKV for video (with subtitles and audio), .MKA for audio-only files and .MKS for subtitles only.

Initially the uptake of the format was low. It was initially used almost exclusively for DVD rips of anime, as the container allowed the viewer to choose between the original language track and a dub. In recent years, however, Matroska has seen wider use due to the scene adopting it as a format of choice for high definition content ripped from HDTV and next generation video discs (HD DVD and Blu-ray). It usually carries H.264 video, one or more AC3/AAC/DTS audio tracks and sometimes one or more subtitle tracks (sometimes coupled with one or more embedded TrueType or OpenType font). Before H.264, most MKV files from the above mentioned scene contained RealVideo (RV9, RV10) encoded video tracks, which at that time was slightly superior to MPEG-4 Part 2[citation needed] (used e.g. by the DivX, Xvid and FFmpeg MPEG-4 codecs), especially for anime material, in combination with MP3 or Vorbis encoded audio streams and soft-subtitles.[/QUOTE]

Is there a particular reason why you don't want MKV files?

You can convert them using Avidemux. There are several options of containers (file format) and encoders. If you really want to convert to WMV, then you can use [[COLOR="DarkRed"]**WinFF**[/COLOR]]("http://code.google.com/p/winff/").

---

### Post by ThaAllGood1 on 2008-11-17
LOL Figured some one would call me on the WMV, well i want my computer to at least be MS free.  As of now the Xbox will play MKV files but only with 2 channel audio.  It will support WMV files though with the 5.1 sound.  Open to other suggestions, my goal is to convert MKV files to a file format that the 360 will play while keeping sound and image quality

---

### Post by lovinglinux on 2008-11-17
> **ThaAllGood1 said:**
> LOL Figured some one would call me on the WMV, well i want my computer to at least be MS free.  As of now the Xbox will play MKV files but only with 2 channel audio.  It will support WMV files though with the 5.1 sound.  Open to other suggestions, my goal is to convert MKV files to a file format that the 360 will play while keeping sound and image quality

LOL. I guess you can also be free of MS on your Xbox with [[COLOR="Red"]**XBMC**[/COLOR]]("http://xbmc.org/"). I don't have an Xbox, so I really don't know how it works, how to install or if it could compromise other functionalities or warranty. But it seems that XBMC would allow you to [[COLOR="Red"]**play other formats**[/COLOR]]("http://xbmc.org/about/") not supported by Microsoft.

I have XBMC on my PC and it is a pretty nice application, although I prefer to use my special setup of Firefox to manage media files.

BTW, if I didn't mentioned the WMV proprietary aspect, I would never know you were trying to convert the video to play on the Xbox and would never recommend XBMC. So it's a good idea to mention why you need a specific format, otherwise people will only give you converter options while they could know about other solutions that you are not aware of.

---

### Post by ThaAllGood1 on 2008-11-18
I used XBMC on my old Xbox but would like to keep the 360 legit, we all know how well they are built and how they never need repaired.  The 360 does support up to 1080p on MKV and WMV but only supports 2 channel audio for MKV.  And there is the problem

---

### Post by lovinglinux on 2008-11-19
> **ThaAllGood1 said:**
> I used XBMC on my old Xbox but would like to keep the 360 legit, we all know how well they are built and how they never need repaired.  The 360 does support up to 1080p on MKV and WMV but only supports 2 channel audio for MKV.  And there is the problem

I see. Have you tried WinFF?

Why don't you convert it to AVI? It seems that Xbox 360 supports 5.1 sound for this format.

[http://ubuntuforums.org/showthread.php?t=641491](http://ubuntuforums.org/showthread.php?t=641491)

---

### Post by ThaAllGood1 on 2008-11-19
Won't I lose the video quality if its in a XVID format?

---

### Post by lovinglinux on 2008-11-19
> **ThaAllGood1 said:**
> Won't I lose the video quality if its in a XVID format?

I guess you lose quality on every conversion, no matter if the format is AVI, WMV or MP4, unless the output is encoded with a lossless codec like Huffyuv. 

AVI does not necessarily uses XVID for encoding, although as you can see in the quote below from [[COLOR="Red"]**Xbox FAQ**[/COLOR]]("http://blogs.msdn.com/xboxteam/archive/2007/11/30/december-2007-video-playback-faq.aspx"), Xbox only supports the [[COLOR="Red"]**MPEG-4 ASP**[/COLOR]]("http://en.wikipedia.org/wiki/MPEG-4_ASP") video profile, which means you can encode the video with Xvid4 or lavc ([[COLOR="Red"]**libavcodec**[/COLOR]]("http://en.wikipedia.org/wiki/Libavcodec")) using Avidemux.

[QUOTE=http://blogs.msdn.com/xboxteam/archive/2007/11/30/december-2007-video-playback-faq.aspx]

**1.    What exactly does the Xbox 360 support for AVI?**

Xbox 360 supports the following for AVI:

·         File Extensions: .avi, .divx

·         Containers: AVI

·         Video Profiles: [[COLOR="Red"]**MPEG-4 Part 2**[/COLOR]]("http://en.wikipedia.org/wiki/MPEG-4_ASP"), Simple & Advanced Simple Profile

·         Video Bitrate: 5 Mbps with resolutions of 1280 x 720 at 30fps. See question number 11 for more information.

·         Audio Profiles: [COLOR="Red"]**[Dolby® Digital 2 channel and 5.1 channel]("http://en.wikipedia.org/wiki/AC3")**[/COLOR], MP3

·         Audio Max Bitrate: No restrictions. See question number 11 for more information.


**5.    Can I mix and match the video and audio codecs outside of those defined in questions 1 through 4 above?**

No you cannot.  We only support each audio and video codec in the explicit containers defined in questions 1 through 4.


**14. Do you support 5.1 channel AAC?**

No. Only 2-channel AAC is supported. If you want to play a 5.1-channel video on your console, you will need to encode it to WMV with WMAPro 5.1 audio or use the AVI container with [[COLOR="Red"]**Dolby® Digital 5.1 audio**[/COLOR]]("http://en.wikipedia.org/wiki/AC3").[/QUOTE]

Based on the information above, to get what you want you have to encode the video using WMV or using AVI with [[COLOR="Red"]**MPEG-4 ASP**[/COLOR]]("http://en.wikipedia.org/wiki/MPEG-4_ASP") video and [[COLOR="Red"]**AC3**[/COLOR]]("http://en.wikipedia.org/wiki/AC3") audio.

Doing this with Avidemux is pretty simple. Select **MPEG-4 ASP (lavc)** or **MPEG-4 ASP (Xvideo4)** in the video option and **AC3 (lavc)** in the audio option.

I have good results with **MPEG-4 ASP (lavc)** profile when converting using Avidemux. It is fast and has good quality. You might have to tweak the codec options with the "Configure" button to get better results and less video quality loss.

---

### Post by ThaAllGood1 on 2008-11-19
When trying to install Avidemux 2.4.3.1 I received the error 
Error: Dependency is not satisfiable: liblame0

Did some googling and haven't found much on it

THX for helping me out with this process

---

### Post by lovinglinux on 2008-11-20
> **ThaAllGood1 said:**
> When trying to install Avidemux 2.4.3.1 I received the error 
Error: Dependency is not satisfiable: liblame0

Did some googling and haven't found much on it

THX for helping me out with this process

Where did you get Avidemux?

To install it all you have to do is run the following command:

```
sudo apt-get install avidemux
```

You can also select it using using the Add/Remove manager. Nevertheless, I don't remember exactly, but I guess you need universe, multiverse or medibuntu software sources enabled. 

To enable them go to System >>> Administration >>> Software Sources, then select the second an the fourth checkboxes in the "Ubuntu Software" tab. Then open the "Third-Party Software" tab and add the following lines:

```
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free
```

Finally, install the Medibuntu key by copying and pasting the following command into the terminal:

```
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

After completing this process you can install Avidemux as explained. The software manager will install the necessary dependencies.

---

### Post by FakeOutdoorsman on 2008-11-20
You could try ffmpeg, but you'll need the "unstripped" version to encode to mpeg4:
```
sudo apt-get purge ffmpeg
sudo apt-get update
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0 ffmpeg
```
Here's a most basic command (I'm not sure if it will work in the Xbox):
```
ffmpeg -i inputvideo.mkv -vcodec mpeg4 -vtag xvid -sameq -acodec ac3 -ab 512k output.avi
```
It can be improved though. Show the output of:
```
ffmpeg -i inputvideo.mkv
```
This will show the specs of the input video.  It's good to know what is being worked with before transcoding.

---

### Post by ThaAllGood1 on 2008-11-20
Fake...With the code that you had shown it would convert it to a XVID file.  Will that keep the same 720p resolution or will it alter that?

Trying Avidemux now and will let you know how that works.

---

### Post by ThaAllGood1 on 2008-11-20
OK tried Avidemux and I do not see any option to convert to WMV am I missing it?

---

### Post by lovinglinux on 2008-11-21
> **ThaAllGood1 said:**
> OK tried Avidemux and I do not see any option to convert to WMV am I missing it?

No. Avidemux does not convert to WMV, but you can convert to AVI with 5.1 sound using the specifications that are supported by Xbox.

Select MPEG-4 ASP (lavc) or MPEG-4 ASP (Xvideo4) in the video option, AC3 (lavc) in the audio option and AVI in the format option.

---

### Post by FakeOutdoorsman on 2008-11-21
> **ThaAllGood1 said:**
> Fake...With the code that you had shown it would convert it to a XVID file.  Will that keep the same 720p resolution or will it alter that?
It will use whatever resolution the input file is unless you change it with the "-s" option.  If you have a long movie and don't want to encode the whole thing then try the "-vframes foo" option, where *foo* is the number of frames to encode: -vframes 300.

---

### Post by ThaAllGood1 on 2008-11-23
@Fake

OK so I did the conversion on a couple files and tried both over the network and burned to a disk.  The video runs at really fast, maybe like 16x speed and the audio as normal, this goes for about 30 sec before the audio stops completely.  Any ideas?

---

### Post by LinuxPS2 on 2008-11-24
couldn't you always just set up a UPnP server like fuppes and stream it with the full audio?... or possibly use mencoder - it should be able to do it, also what is the audio?... AAC?

---

### Post by LinuxPS2 on 2008-11-24
or you could check here... [http://ubuntuforums.org/showthread.php?t=548547&page=3](http://ubuntuforums.org/showthread.php?t=548547&page=3)

the first post has a mencoder script that seems to work... ripbot264 for windows is nice though - seems like it uses ffmpeg for its grunt work and will show the code - see what it does

---

### Post by ThaAllGood1 on 2008-11-24
@LinuxPS2  

The Xbox does not support MKV with 5.1 audio only with 2.0.  When I am on the Xbox it does not recognize any MKV files.  If you are not familiar with it, it will only show compatible files

---

### Post by FakeOutdoorsman on 2008-11-24
> **ThaAllGood1 said:**
> @Fake

OK so I did the conversion on a couple files and tried both over the network and burned to a disk.  The video runs at really fast, maybe like 16x speed and the audio as normal, this goes for about 30 sec before the audio stops completely.  Any ideas?
Show the command you used and the full ffmpeg output.

---

