---
title: "How can I extract video properties to text file?"
date: 2011-04-30
forum: Multimedia Software
---

### Post by spielball on 2011-04-30
In VLC player I can display media information, but I cannot export this to a text file. Besides, the information displayed is poor. Things like overall bitrate or video bitrate aren't shown. I'd like to know how I can extract detailed video properties or which software to use for that purpose.

---

### Post by shantiq on 2011-04-30
[**mediainfo**]("http://mediainfo.sourceforge.net/en/Download/Ubuntu") is your best bet here

it gives you that kind of in depth info

```
mediainfo  ff2.mp4
General
Complete name                    : ff2.mp4
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 98.8 MiB
Duration                         : 3mn 20s
Overall bit rate                 : 4 144 Kbps
Writing application              : MEncoder 1.0rc4-4.5.2
Writing library                  : MPlayer

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.1
Format settings, CABAC           : Yes
Format settings, ReFrames        : 6 frames
Muxing mode                      : Container profile=Unknown@4.1
Codec ID                         : H264
Duration                         : 3mn 20s
Bit rate                         : 2 603 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16/9
Frame rate                       : 25.000 fps
Standard                         : PAL
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.113
Stream size                      : 62.1 MiB (63%)

Audio
Format                           : PCM
Format settings, Endianness      : Little
Format settings, Sign            : Unsigned
Codec ID                         : 1
Codec ID/Hint                    : Microsoft
Duration                         : 3mn 20s
Bit rate mode                    : Constant
Bit rate                         : 1 536 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 36.6 MiB (37%)
Interleave, duration             : 500 ms (12.50 video frames)
Interleave, preload duration     : 500 ms


```   if you add -f to the command you get even more info


```
mediainfo -f nameofthefile
```


=========================================

[B]And can also be installed thus
[/B]
1) Installing the command-line version from source

This is very straightforward:

ubuntu% ```
wget http://ovh.dl.sourceforge.net/sourceforge/mediainfo/MediaInfo_CLI_0.7.8_GNU_FromSource.tar.bz2
```
ubuntu% ```
bzip2 -d MediaInfo_CLI_0.7.8.tar.bz2
```
ubuntu% ```
tar xvf MediaInfo_CLI_0.7.8_GNU_FromSource.tar
```

ubuntu% ```
cd MediaInfo_CLI_0.7.8_GNU_FromSource
```
ubuntu% ```
sh CLI_Compile.sh 
```
ubuntu% ```
cd MediaInfo/Project/GNU/CLI
```
ubuntu% ```
sudo make install
```

 You can now invoke the 'mediainfo' command.   


ps a gui version also exists

---

### Post by andrew.46 on 2011-04-30
And of course to export to text file you can either use MediaInfo in the following manner:

```
mediainfo **[COLOR="Red"]my_file[/COLOR]** > video_info
```

or use the following syntax which also shows the info in the terminal:

```
mediainfo **[COLOR="Red"]my_file[/COLOR]** --LogFile=video_info
```

---

### Post by spielball on 2011-04-30
Thanks a lot! I'll give it a try.

Edit:
It works very well. Unfortunately, only the CLI is satisfying. The GUI version doesn't have any option to save the info to a text file. This is a bit inconvenient, because navigating in terminal isn't really exciting. In this case I'd prefer to drag & drop the file into the MediaInfo window and save the info to file. However, the CLI gives very detailed info. Hopefully, the GUI version will have an option to save a txt file in the future.

---

