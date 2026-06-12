---
title: "Merge separate audio and video streams"
date: 2007-10-26
forum: Multimedia Production
---

### Post by moeFinley on 2007-10-26
With Mencoder, FFMpeg or something similar is it possible to merge audio and video from separate files?

I can't seem to find a way to specify multiple input files in the command.  I'm trying to take audio from one Flash video file and put it in another without re-encoding.

Thanks for any help.

---

### Post by VvWolverinevV on 2008-01-28
*bump*

I have exactly this same question.

---

### Post by Creative2 on 2008-01-28
well i have made fuoco tools[ here]("http://ubuntuforums.org/showthread.php?t=652843")  
 you can find avimerge in video filter, if you want do with command line without interfaces: 

THIS WORKS ONLY FOR AVI FILES remember to every files must have the SAME RESOLUTION THE SAME BITRATE VIDEO AND AUDIO THE SAME RESAMPLING 

1 install transcode (avimerge is a part of transocde)
2 avimerge -o TEMP.avi -i you avi file here in a line  

where TEMP is the output

---

### Post by eye208 on 2008-01-28
> **moeFinley said:**
> With Mencoder, FFMpeg or something similar is it possible to merge audio and video from separate files?
With MEncoder you can specify a separate audio input file using the -audiofile option:

mencoder yourvideo -audiofile youraudio -ovc copy -oac copy -o result.avi

If your video is in MP4 format, you can use MP4Box to add audio streams:

MP4Box yourvideo.mp4 -add youraudio.aac

Mkvmerge does the same thing for Matroska files. Check out the manual page.

You can also use Avidemux to do these things.

---

### Post by VvWolverinevV on 2008-01-28
Nice!  MP4Box did the trick for my .mpg video and .m4a audio files.

One more quesiton:
The audio file is longer than the video file.  How do I truncate the resulting video file to a specified length?

---

### Post by eye208 on 2008-01-28
> **VvWolverinevV said:**
> The audio file is longer than the video file.  How do I truncate the resulting video file to a specified length?
First find out the length of the video stream in the MP4 file:

MP4Box yourfile.mp4 -info

The output will look like this:
```
* Movie Info *
        Timescale 600 - Duration 00:01:45.371
        Fragmented File no - 2 track(s)
        File Brand isom - version 1
        Created: GMT Mon Jan 28 18:34:02 2008

File has root IOD
Scene PL 0xff - Graphics PL 0xff - OD PL 0xff
Visual PL: AVC/H264 Profile (0x15)
Audio PL: AAC Profile @ Level 2 (0x29)
No streams included in root OD

Track # 1 Info - TrackID 1 - TimeScale 12000 - Duration 00:00:08.000
Media Info: Language "Undetermined" - Type "vide" - Sub Type "avc1" - 96 samples
MPEG-4 Config: Visual Stream - ObjectTypeIndication 0x21
AVC/H264 Video - Visual Size 320 x 240 - Profile Main @ Level 5.1
Pixel Aspect Ratio 1:1 - Indicated track size 320 x 240
Self-synchronized

Track # 2 Info - TrackID 2 - TimeScale 44100 - Duration 00:01:45.372
Media Info: Language "Undetermined" - Type "soun" - Sub Type "mp4a" - 4538 samples
MPEG-4 Config: Audio Stream - ObjectTypeIndication 0x67
MPEG-2 Audio AAC LC - 2 Channel(s) - SampleRate 44100
Synchronized on stream 1
```
In this example the video stream duration is only 8 seconds. Now you can trim the file to 8 sec overall duration:

MP4Box yourfile.mp4 -splitx 0:8

This will create a new file yourfile_0_8.mp4 with audio truncated to 8 seconds.

---

### Post by VvWolverinevV on 2008-01-29
Perfect!  Thank you.

---

