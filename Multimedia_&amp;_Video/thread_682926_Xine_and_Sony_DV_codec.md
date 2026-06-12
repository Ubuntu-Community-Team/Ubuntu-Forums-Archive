---
title: "Xine and Sony DV codec"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by MrClearPore on 2008-01-30
I recently downloaded an **.avi** file that Xine could not open.  I received an error message that stated > There is no demuxer plugin available to handle <file name.avi> 
Usually this means that the file format was not recognized.
Judging from the name of the file, it was encoded with the XviD codec.  However, to verify whether this was true or not, I downloaded/installed a program called **mediainfo** that allowed me to view all pertinent information about the file (length, audio/video codecs used, etc).  To my surprise, I noticed that the **.avi** was encoded using the **Sony Digital Video (DV)** codec (for audio and video).

Here's the the complete output from **mediainfo:**

```
General #0
Count                : 185
Count of stream of t : 1
Kind of stream       : General
StreamKindID         : 0
Count of video strea : 1
Count of audio strea : 1
Count of text stream : 0
Count of chapter str : 0
Codecs Video         : Sony DV
Audio codecs         : Sony DV
Complete name        : video/Saw.IV.UNRATED.DVDRip.XviD-DiAMOND.avi
Folder name          : video
File name            : Saw.IV.UNRATED.DVDRip.XviD-DiAMOND
File extension       : avi
Format               : AVI
Format               : AVI
Format/Info          : Audio Video Interleave
Format/Family        : RIFF
Format/Extensions    : avi
Codec                : AVI
Codec                : AVI
Codec/Info           : Audio Video Interleave
Codec/Family         : RIFF
Codec/Extensions     : avi
File size            : 731241472
File size            : 697 MiB
File size            : 697 MiB
File size            : 697 MiB
File size            : 697 MiB
File size            : 697.4 MiB
PlayTime             : 214948
PlayTime             : 3mn 34s
PlayTime             : 3mn 34s 948ms
PlayTime             : 3mn 34s
PlayTime             : 00:03:34.948
Bit rate             : 27215567
Bit rate             : 27 Mbps

Video #0
Count                : 83
Count of stream of t : 1
Kind of stream       : Video
StreamKindID         : 0
Codec                : dvsd
Codec                : Sony DV
Codec/Family         : DV
Codec/Info           : Sony Digital Video (DV) 525 lines at 29.97 Hz or 625 lines at 25.00 Hz
Codec/CC             : dvsd
PlayTime             : 214948
PlayTime             : 3mn 34s
PlayTime             : 3mn 34s 948ms
PlayTime             : 3mn 34s
PlayTime             : 00:03:34.948
Width                : 720
Width                : 720 pixels
Display Aspect ratio : 1.333
Display Aspect ratio : 4/3
Frame rate           : 29.970
Frame rate           : 29.970 fps
FrameCount           : 6442

Audio #0
Count                : 67
Count of stream of t : 1
Kind of stream       : Audio
StreamKindID         : 0
Codec                : dvsd
Codec                : Sony DV
Codec/Family         : DV
Codec/Info           : Sony Digital Video (DV), audio part
Codec/CC             : dvsd

```

My question: is there a way for Xine to play this file?  And if so, how?

Any help is appreciated :)

---

