---
title: "VLC not showing embedded subtitles in a .MOV video"
date: 2012-05-28
forum: Multimedia Software
---

### Post by Fausto Arinos Barbuto on 2012-05-28
I have downloaded a big .MOV file with subtitles embedded on it.  But when I play it the subtitles aren't displayed.  I then found out that **_V_ideos/_S_ubtitle Track/caption - [English]** was not enabled, so I enabled it.  I was able to see the subtitles for a very brief while (say, half a second or less), but then they disappeared.  All other players I have installed on my computer show the subtitles perfectly, but VLC is my favourite player.  I wonder why it is not working and whatever plugin/codec is missing.  Thanks for any help.
PS: I have VLC 2.0.1 running on Ubuntu 12.04 64-bit.

---

### Post by shantiq on 2012-05-29
if    the subtitle is burnt into the movie file it plays automatically

so i am not sure what it could be



please install [**mediainfo** ]("http://mediainfo.sourceforge.net/en/Download")  it is in synaptic in precise if you are on precise    and run to see what is in your file       thanx


> mediainfo nameoffile

---

### Post by dodle on 2012-05-29
Try putting it in an .mkv container. You can use MKVMerge or MKVMerge GUI to do so. Install "mkvtoolnix" and "mkvtoolnix-gui".

---

### Post by andrew.46 on 2012-05-29
Can you give a link to this file?

---

### Post by Fausto Arinos Barbuto on 2012-06-03
> **andrew.46 said:**
> Can you give a link to this file?

Sure, you can find it here:

[http://openmedia.yale.edu/cgi-bin/open_yale/media_downloader.cgi?file=/courses/fall07/engl220/mov/chapters/engl220_02_091007.mov](http://openmedia.yale.edu/cgi-bin/open_yale/media_downloader.cgi?file=/courses/fall07/engl220/mov/chapters/engl220_02_091007.mov)

Sorry it took me so long to reply -- I've got the flu.  :-(

---

### Post by Fausto Arinos Barbuto on 2012-06-03
> **shantiq said:**
> if    the subtitle is burnt into the movie file it plays automatically

so i am not sure what it could be



please install [**mediainfo** ]("http://mediainfo.sourceforge.net/en/Download")  it is in synaptic in precise if you are on precise    and run to see what is in your file       thanx


Here it is the result of mediainfo:

General
Complete name                            : engl220_23_120307.mov
Format                                   : MPEG-4
Format profile                           : QuickTime
Codec ID                                 : qt  
File size                                : 370 MiB
Duration                                 : 44mn 4s
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 174 Kbps
Movie name                               : ENGL 220 - Lecture 23 - Professor John Rogers
Description                              : This introduction to Samson Agonistes focuses on a psycho-sexual reading of the poem, with particular emphasis placed on the poem's peculiar association of sexuality with violence.  The characterization of Dalila and her similarity to Samson is discussed.  The problems inherit in Miltonic heroism, especially self-sufficiency and the nature of heroic sacrifice, are expounded upon.
Encoded date                             : UTC 2008-10-01 14:44:27
Tagged date                              : UTC 2011-07-01 19:34:11
Copyright                                : Copyright: Yale University (2008). Some rights reserved. Unless otherwise indicated, content published by the Yale Open Educational Resources Video Lecture Project may be used under a Creative Commons License Attribution-Noncommercial-ShareAlike 3.0 Unported agreement. Use of certain materials contained in the project website is restricted by license agreements between Yale and other parties. You must seek permission directly from the licensor or copyright owner to reuse these materials.
Comment                                  : Samson Agonistes
com.apple.quicktime.album                : Yale University
com.apple.quicktime.artist               : John Rogers
com.apple.quicktime.keywords             : pronunciation, Edward Phillips, dating of the poem, Mary Powell, Act of Oblivion, identity, synecdoche, "the uncircumcised," heroic self-sufficiency
com.apple.quicktime.player.movie.audio.m : (Binary)

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Baseline@L3.0
Format settings, CABAC                   : No
Format settings, ReFrames                : 1 frame
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 44mn 3s
Bit rate mode                            : Variable
Bit rate                                 : 1 004 Kbps
Maximum bit rate                         : 4 006 Kbps
Width                                    : 640 pixels
Height                                   : 360 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.145
Stream size                              : 316 MiB (86%)
Language                                 : English
Encoded date                             : UTC 2008-10-01 14:44:06
Tagged date                              : UTC 2011-07-01 19:34:11
Color primaries                          : BT.601-6 525, BT.1358 525, BT.1700 NTSC, SMPTE 170M
Transfer characteristics                 : BT.709-5, BT.1361
Matrix coefficients                      : BT.601-6 525, BT.1358 525, BT.1700 NTSC, SMPTE 170M

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 44mn 3s
Bit rate mode                            : Constant
Bit rate                                 : 113 Kbps
Nominal bit rate                         : 128 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 35.5 MiB (10%)
Language                                 : English
Encoded date                             : UTC 2008-10-01 14:44:07
Tagged date                              : UTC 2011-07-01 19:34:11
Material_Duration                        : 2643986
Material_StreamSize                      : 37187165

Text #1
ID                                       : 5
Format                                   : Timed text
Codec ID                                 : tx3g
Duration                                 : 44mn 4s
Bit rate mode                            : Variable
Bit rate                                 : 114 bps
Stream size                              : 36.7 KiB (0%)
Language                                 : English
Encoded date                             : UTC 2008-10-01 14:44:07
Tagged date                              : UTC 2008-10-01 14:45:07

Text #2
ID                                       : 9
Format                                   : Apple text
Codec ID                                 : text
Duration                                 : 44mn 4s
Bit rate mode                            : Variable
Bit rate                                 : 1 bps
Stream size                              : 259 Bytes (0%)
Language                                 : English
Encoded date                             : UTC 2011-07-01 19:32:57
Tagged date                              : UTC 2011-07-01 19:34:11

Menu
ID                                       : 3
Language                                 : English
Encoded date                             : UTC 2008-10-01 14:44:07
Tagged date                              : UTC 2008-10-01 14:45:07

---

### Post by Fausto Arinos Barbuto on 2012-06-03
> **dodle said:**
> Try putting it in an .mkv container. You can use MKVMerge or MKVMerge GUI to do so. Install "mkvtoolnix" and "mkvtoolnix-gui".

Did that, but the resulting file does not show any subtitles either.
Thanks for the suggestion anyway.

---

### Post by andrew.46 on 2012-06-04
> **Fausto Arinos Barbuto said:**
> Sure, you can find it here:

[http://openmedia.yale.edu/cgi-bin/open_yale/media_downloader.cgi?file=/courses/fall07/engl220/mov/chapters/engl220_02_091007.mov](http://openmedia.yale.edu/cgi-bin/open_yale/media_downloader.cgi?file=/courses/fall07/engl220/mov/chapters/engl220_02_091007.mov)

Sorry it took me so long to reply -- I've got the flu.  :-(

Hmmmm.... cannot download from here. Sure about the link?

---

### Post by shantiq on 2012-06-04
hi again   so it shows you have an apple text in there   and a tx3g  sub  file.     i think that might be the problem   but i am not sure      maybe run file in a Mac if you know someone who has one.    Neither do i see a way of converting that to a format that is friendly to Ubuntu.....      someone else might know....   Sorry

> Text #1
ID : 5
Format : Timed text
[B]Codec ID : tx3g


[QUOTE]

tx3g is short for MPEG-4 Part 17, or MPEG-4 Timed Text, the text based subtitle format for MPEG-4. It is also streamable, which was one of the main aspects when creating the format.
It is mainly aimed for use in the .mp4 container, but can also be used in the .3gp container (as 3GPP Timed Text), which is technically almost identical with .mp4 but more used in cell phones. 3GPP Timed Text is exactly the same as MPEG-4 Timed Text when used in the .mp4 container.

open tx3g file on Windows:

QuickTime
MP4Box

open tx3g file on Mac:

Apple QuickTime





[/B]Duration : 44mn 4s
Bit rate mode : Variable
Bit rate : 114 bps
Stream size : 36.7 KiB (0%)
Language : English
Encoded date : UTC 2008-10-01 14:44:07
Tagged date : UTC 2008-10-01 14:45:07

Text #2
ID : 9
[B]Format : Apple text
[/B]Codec ID : text
Duration : 44mn 4s
Bit rate mode : Variable
Bit rate : 1 bps
Stream size : 259 Bytes (0%)
Language : English
Encoded date : UTC 2011-07-01 19:32:57
Tagged date : UTC 2011-07-01 19:34:11[/QUOTE]



see this is what you get with srt sub file in an mkv    **srt is the only format i see that works in Ubuntu ** [there is a format called idx that has never worked for me]

> Text #1
ID                                       : 3
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Default                                  : Yes
Forced                                   : No

Text #2
ID                                       : 4
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Default                                  : No
Forced                                   : No

---

### Post by shantiq on 2012-06-04
ok there might be a way


we have a program called MP4Box   in Ubuntu


which installs this way  


```
sudo apt-get install  gpac
```


then as you can see there is a way to convert existing sub to srt    [this might work]



> MP4Box  -h dump
Dumping Options
 -std                 dumps to stdout instead of file
 -info [trackID]      prints movie info / track info if trackID specified
                       * Note: for non IsoMedia files, gets import options
 -bt                  scene to bt format - removes unknown MPEG4 nodes
 -xmt                 scene to XMT-A format - removes unknown MPEG4 nodes
 -wrl                 scene VRML format - removes unknown VRML nodes
 -x3d                 scene to X3D/XML format - removes unknown X3D nodes
 -x3dv                scene to X3D/VRML format - removes unknown X3D nodes
 -lsr                 scene to LASeR format
 -diso                scene IsoMedia file boxes in XML output
 -drtp                rtp hint samples structure to XML output
 -dts                 prints sample timing to text output
 -sdp                 dumps SDP description of hinted file
 -dcr                 ISMACryp samples structure to XML output
 -dump-cover          Extracts cover art
 -dump-chap           Extracts chapter file

 -ttxt                Converts input subtitle to GPAC TTXT format
 -ttxt TrackID        Dumps Text track to GPAC TTXT format
 -srt                 Converts input subtitle to SRT format
 **[COLOR="Red"]-srt TrackID         Dumps Text track to SRT format[/COLOR]**

 -stat                generates node/field statistics for scene
 -stats               generates node/field statistics per MPEG-4 Access Unit
 -statx               generates node/field statistics for scene after each AU

 -hash                generates SHA-1 Hash of the input file



if it does then we can rebuild video file using   Mkvmerge    but first see if this conversion  works


for this use     ```
MP4Box -info nameoryourfile.mp4
```  to find sub track name


then to convert sub file

```
MP4Box  -srt TrackID nameoryourfile.mp4
```    see if a new srt file has been created  .....       fingers crossed.............


**-------------------------------------------------------------------------**


if   all this worked   then rebuild with mkvmerge



> mkvmerge    -o newfilewithsrt.mkv      youroriginalmp4.mp4     newsrt.srt

---

### Post by Fausto Arinos Barbuto on 2012-06-04
> **andrew.46 said:**
> Hmmmm.... cannot download from here. Sure about the link?

The link indeed doesn't work any more. I wonder why.

Try the following:

[http://oyc.yale.edu/english/engl-220/lecture-6](http://oyc.yale.edu/english/engl-220/lecture-6)

At the bottom, select the HIGH BANDWIDTH VIDEO mov [500MB].  The much smaller one, low bandwidth (100 MB file size) has no subtitles in it.

Thanks.

---

### Post by Fausto Arinos Barbuto on 2012-06-04
> **shantiq said:**
> ok there might be a way

I'm away from my computer, but I will try this tonight.

Thanks for all the hints and support.

Fausto

---

### Post by shantiq on 2012-06-04
ok fausto    my suggestion did not work

> MP4Box -info nameoryourfile.mp4


gave me  > /Desktop$ MP4Box -info ok.mov[iso file] Read Box "text" failed (Invalid IsoMedia File)
[iso file] Read Box "stsd" failed (Invalid IsoMedia File)
[iso file] Read Box "stbl" failed (Invalid IsoMedia File)
[iso file] Read Box "minf" failed (Invalid IsoMedia File)
[iso file] Read Box "mdia" failed (Invalid IsoMedia File)
[iso file] Read Box "trak" failed (Invalid IsoMedia File)
[iso file] Read Box "moov" failed (Invalid IsoMedia File)
Error opening file ok.mov: Invalid IsoMedia File



then i tried vlc   no go    then smplayer ans still no go for sub



but good ole movieplayer    played it straight off with sub    but i see you want VLC   ....

[ATTACH]219220[/ATTACH]

---

### Post by andrew.46 on 2012-06-05
Unfortunately I get patchy results also with MPlayer, SMPlayer and vlc :(.

---

