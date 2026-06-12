---
title: "Merge 2 MP4 files"
date: 2012-09-18
forum: Multimedia Software
---

### Post by alfirdaous on 2012-09-18
Hello everybody,

I tried to merge 3 MP4 files using MP4Box / Mencoder, but it does NOT work:

```

$ sudo MP4Box -add 001.mp4 -add 002.mp4 -add 003.mp4 out.mp4 Unknown input file type Unknown input file type Unknown input file type Unknown input file type Unknown input file type Unknown input file type Converting to ISMA Audio-Video MP4 file... Saving to out.mp4: 0.500 secs Interleaving   $ sudo mencoder 001.mp4 002.mp4 003.mp4 -ovc copy -oac copy -of lavf format=mp4 -o output.mp4 mencoder: relocation error: mencoder: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

```Any idea about this issue.

Thx in advance

---

### Post by dargaud on 2012-09-18
mp4 music or mp4 video ? And merge as in play them at the same time (overlap) or play one after the other. In both former cases, use the audacity sound editor to do what you want. In both latter cases, use a video editor.

---

### Post by alfirdaous on 2012-09-18
MP4 video files, I need it in a command line

---

### Post by ron999 on 2012-09-18
> **alfirdaous said:**
> Any idea about this issue.
[SIZE="3"]**Unknown input file type**[/SIZE]

Hi
You need to find out what's in those mp4 files.

```
mediainfo 001.mp4 
```
```
mediainfo 002.mp4 
```
```
mediainfo 003.mp4
```

---

### Post by shantiq on 2012-09-18
hi alfi here is syntax which works



> MP4Box -add 1.mp4 [COLOR="DarkRed"]-cat[/COLOR] 2.mp4 [COLOR="DarkRed"]-cat[/COLOR] 3.mp4 -cat 4.mp4 -cat 5.mp4 -cat 6.mp4   NameofNewCombinedFile.mp4


add only used on the first one   [ and what Ron said...]

---

### Post by ShadowVegan on 2012-09-18
Couldn't you just use a video editing program and put one immediately after the other then save as a new file?

---

### Post by alfirdaous on 2012-09-18
001.mp4
```

$ mediainfo 001.mp4
General
Complete name                    : 001.mp4
Format                           : Flash Video
File size                        : 81.9 MiB
Duration                         : 17mn 2s
Overall bit rate                 : 672 Kbps
httphostheader                   : o-o---preferred---ams03s19---v17---lscache6.c.youtube.com

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Muxing mode                      : Container profile=Unknown@3.0
Duration                         : 17mn 2s
Bit rate                         : 535 Kbps
Width                            : 640 pixels
Height                           : 480 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Variable
Frame rate                       : 25.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.070
Stream size                      : 65.2 MiB (80%)

Audio
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Duration                         : 17mn 2s
Bit rate                         : 129 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 15.7 MiB (19%)


```

002.mp4:
```

$ mediainfo 002.mp4
General
Complete name                    : 002.mp4
Format                           : Flash Video
File size                        : 81.9 MiB
Duration                         : 17mn 2s
Overall bit rate                 : 672 Kbps
httphostheader                   : o-o---preferred---ams03s19---v17---lscache6.c.youtube.com

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Muxing mode                      : Container profile=Unknown@3.0
Duration                         : 17mn 2s
Bit rate                         : 535 Kbps
Width                            : 640 pixels
Height                           : 480 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Variable
Frame rate                       : 25.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.070
Stream size                      : 65.2 MiB (80%)

Audio
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Duration                         : 17mn 2s
Bit rate                         : 129 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 15.7 MiB (19%)


desktop@ks3002276:/home/alfirdaouscom/www/Downloads/Medias/Mariyat/Dorousse/MohammadAlShanakeety/MountaqaAlMoltaqa$ mediainfo 002-2.mp4
General
Complete name                    : 002-2.mp4
Format                           : Flash Video
File size                        : 81.7 MiB
Duration                         : 17mn 3s
Overall bit rate                 : 670 Kbps
httphostheader                   : o-o---preferred---ams03s20---v20---lscache8.c.youtube.com

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Muxing mode                      : Container profile=Unknown@3.0
Duration                         : 17mn 3s
Bit rate                         : 533 Kbps
Width                            : 640 pixels
Height                           : 480 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Variable
Frame rate                       : 25.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.069
Stream size                      : 65.0 MiB (80%)

Audio
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Duration                         : 17mn 3s
Bit rate                         : 129 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 15.7 MiB (19%)

```

003.mp4:
```

$ mediainfo 003.mp4
General
Complete name                    : 003.mp4
Format                           : Flash Video
File size                        : 36.3 MiB
Duration                         : 7mn 28s
Overall bit rate                 : 609 Kbps
httphostheader                   : o-o---preferred---ams03s08---v18---lscache3.c.youtube.com

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Muxing mode                      : Container profile=Unknown@3.0
Duration                         : 7mn 28s
Bit rate                         : 527 Kbps
Width                            : 640 pixels
Height                           : 480 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Variable
Frame rate                       : 25.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.069
Stream size                      : 28.2 MiB (78%)

Audio
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Duration                         : 7mn 28s
Bit rate                         : 129 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 6.87 MiB (19%)


desktop@ks3002276:/home/alfirdaouscom/www/Downloads/Medias/Mariyat/Dorousse/MohammadAlShanakeety/MountaqaAlMoltaqa$ mediainfo 002-3.mp4
General
Complete name                    : 002-3.mp4
Format                           : Flash Video
File size                        : 36.3 MiB
Duration                         : 7mn 28s
Overall bit rate                 : 609 Kbps
httphostheader                   : o-o---preferred---ams03s08---v18---lscache3.c.youtube.com

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Muxing mode                      : Container profile=Unknown@3.0
Duration                         : 7mn 28s
Bit rate                         : 527 Kbps
Width                            : 640 pixels
Height                           : 480 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Variable
Frame rate                       : 25.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.069
Stream size                      : 28.2 MiB (78%)

Audio
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Duration                         : 7mn 28s
Bit rate                         : 129 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 6.87 MiB (19%)

```


I already tried:

```

$ sudo MP4Box -add 001.mp4 -add 002.mp4 -add 003.mp4 out.mp4
Unknown input file type Unknown input file type Unknown input file type Unknown input file type Unknown input file type Unknown input file type Converting to ISMA Audio-Video MP4 file... Saving to out.mp4: 0.500 secs Interleaving

```

and:

```

$ sudo MP4Box -cat 001.mp4 -cat 002.mp4 -cat 003.mp4 output.mp4
[sudo] password for desktop: 
Unknown input file type
Unknown input file type
No suitable media tracks to cat in 001.mp4 - skipping
Unknown input file type
Unknown input file type
No suitable media tracks to cat in 002.mp4 - skipping
Unknown input file type
Unknown input file type
No suitable media tracks to cat in 003.mp4 - skipping
Saving to output.mp4: 0.500 secs Interleaving

```
eventhough:

```

$ sudo mencoder 001.mp4 002.mp4 003.mp4 -ovc copy -oac copy -of lavf format=mp4 -o output.mp4 mencoder: relocation error: mencoder: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

```

as well as:

```

sudo cat 001.mp4 002.mp4 003.mp4 >video.mp4 bash: video.mp4: Permission denied

```

PS: I am under Ubuntu Server, NOT Ubuntu Desktop

---

### Post by ron999 on 2012-09-18
Hi
mediainfo shows:-"**Format : Flash Video**".
They're not pukka mp4 files.
That's probably why MP4Box rejects them.

Try processing them with FFmpeg.
Like this:-
```
ffmpeg -i 001.mp4 -vcodec copy -acodec copy 001a.mp4
```
```
ffmpeg -i 002.mp4 -vcodec copy -acodec copy 002a.mp4
```
```
ffmpeg -i 003.mp4 -vcodec copy -acodec copy 003a.mp4
```

When done, mediainfo will show:- "**Format : MPEG-4**".
Then add/cat the new files with MP4Box.

---

### Post by afulldeck on 2012-09-18
> **shantiq said:**
> hi alfi here is syntax which works






add only used on the first one   [ and what Ron said...]
I new to Ubuntu, but not new to unix. Although I am very much out of date. That said, I tried to do a man pages on MP4Box and I got nothing. Where does this command come from? I seem to be looking in all the wrong places....

MP4Box -add 1.mp4 [COLOR=DarkRed]-cat[/COLOR] 2.mp4 [COLOR=DarkRed]-cat[/COLOR] 3.mp4 -cat 4.mp4 -cat 5.mp4 -cat 6.mp4   NameofNewCombinedFile.mp4

---

### Post by alfirdaous on 2012-09-18
thx ron999, it works, BUT, while combining files using this command line:

```

sudo MP4Box -cat 001a.mp4 -cat 002a.mp4 -cat 003a.mp4 -new combinedfile.mp4

```

It is combining like this:

> 
001a.mp4 then 001a.mp4 then 002a.mp4 then 003a.mp4


so 001a.mp4 is duplicated

---

### Post by shantiq on 2012-09-19
yes wrong syntax    first one is add then cat for all the next ones


>  MP4Box -add 1.mp4 -cat 2.mp4 -cat 3.mp4 -cat 4.mp4 -cat 5.mp4 -cat 6.mp4 NameofNewCombinedFile.mp4   unless i am sorely mistaken

---

### Post by alfirdaous on 2012-09-19
Thx shantiq, BUT, there is an image of the first video and sound of the second video at the beginning of the file

---

### Post by shantiq on 2012-09-19
ok if MP4Box id not playing ball may i suggest 2 other routes


**mencoder**


```
mencoder -oac pcm -ovc copy -o final.mp4    1.mp4 2.mp4 3.mp4 etc...
```


you can try it with -oac copy  but i find it oftens refuses that and asks for pcm which makes the size much bigger but usually is fine


when all command line fails i use **Kdenlive** [in synaptic] always reliable but reencodes

---

### Post by alfirdaous on 2012-09-19
I already tried the same, output:

```

mencoder: relocation error: mencoder: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

```

another method:

```

$ sudo MP4Box -cat 002a.mp4 -cat 002b.mp4 -cat 002c.mp4 outme2.mp4
Appending file 002a.mp4
No suitable destination track found - creating new one (type vide)
No suitable destination track found - creating new one (type soun)
Appending file 002b.mp4                          
Appending file 002c.mp4                          
Saving to outme2.mp4: 0.500 secs Interleaving    

```

another way:

```

$ sudo MP4Box -add 002a.mp4 -add 002b.mp4 -add 002c.mp4 -new outmeadd.mp4
IsoMedia import - track ID 1 - Video (size 640 x 480)
IsoMedia import - track ID 2 - Audio (SR 44100 - 2 channels)
IsoMedia import - track ID 1 - Video (size 640 x 480)     
IsoMedia import - track ID 2 - Audio (SR 44100 - 2 channels)
IsoMedia import - track ID 1 - Video (size 640 x 480)     
IsoMedia import - track ID 2 - Audio (SR 44100 - 2 channels)
Saving outmeadd.mp4: 0.500 secs Interleaving              

```

so in the above cases:

1st one: the only video1 is given as an output format.

2nd one: the 3 files are merged, BUT, the first video is duplicated

---

### Post by shantiq on 2012-09-19
ok funk it    go to Kdenlive never seen that fail  :KS:KS  gives you perfect copies [ i usually pick mkv]    and it does not care how disparate input files might be

it is slow but REALLY effective

---

### Post by alfirdaous on 2012-09-19
thx shantiq, but I am using Ubuntu Server, so command line will be highly appreciated

---

### Post by ron999 on 2012-09-19
> **alfirdaous said:**
> thx ron999, it works, BUT, while combining files using this command line:

```

sudo MP4Box -cat 001a.mp4 -cat 002a.mp4 -cat 003a.mp4 -new combinedfile.mp4

```

It is combining like this:



so 001a.mp4 is duplicated
Try with this syntax:-
```
MP4Box 001a.mp4 -cat 002a.mp4 -cat 003a.mp4 -out combinedfile.mp4
```

---

### Post by alfirdaous on 2012-09-19
ron999: I think it works, I should watch the full movie 42 min 26 sec, I'll get back to you

---

### Post by alfirdaous on 2012-09-19
It works perfect, thanks

---

