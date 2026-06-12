---
title: "How to Rip .m4a"
date: 2011-03-16
forum: Multimedia Software
---

### Post by ukbeast on 2011-03-16
I am trying to use Gstreamer with Sound Juicer to Rip to .m4a CBR 192 (constant bit rate).

However I keep getting variable bitrate, what am I doing wrong?

audio/x-raw-int,rate=44100,channels=2 ! bitrate=320000 faac profile=2 ! ffmux_mp4

Also 128000 has the same memory usage as 320000?

---

### Post by Yellow Pasque on 2011-03-17
Why wouldn't you be using bitrate=192000?

---

### Post by ukbeast on 2011-03-17
Bitrate=192000 always comes out the sames as bitrate=320000.

Is there a CD ripper with CDDB support? and constant bitrate for MPEG-4 audio?

---

### Post by ron999 on 2011-03-17
> **ukbeast said:**
> Bitrate=192000 always comes out the sames as bitrate=320000.

Is there a CD ripper with CDDB support? and constant bitrate for MPEG-4 audio?

Hi
SoundJuicer uses **faac** encoder which is a **VBR** encoder. It won't encode CBR.:(
That's probably why SoundJuicer won't give you a CBR MPEG-4 audio rip.

faac has an **ABR** option which uses VBR but aims for a target.

Even if I use faac as a stand-alone converter using a 192Kbps ABR option MediaInfo shows _152Kbps_ VBR.:confused:
```
faac -b 192 -w santana.wav 
```

> General
Complete name                    : santana.m4a
Format                           : MPEG-4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 3.90 MiB
Duration                         : 3mn 35s
Overall bit rate                 : [COLOR="Red"]152 Kbps[/COLOR]
Writing application              : FAAC 1.26.1

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format profile                   : LC
Codec ID                         : 40
Duration                         : 3mn 35s
Bit rate mode                    : [COLOR="Red"]Variable[/COLOR]
Bit rate                         : 151 Kbps
Maximum bit rate                 : 179 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 3.86 MiB (99%)


I use **RubyRipper** with **neroAacEnc** encoder.
(RubyRipper uses freedb - not CDDB).
neroAacEnc has a CBR option, though (imo) I think that it's probably ABR too.
If I rip the track with RubyRipper using [FONT="Courier New"]**neroAacEnc -br 192000**[/FONT] MediaInfo shows a more accurate _192Kbps_ (VBR) result:-

> Complete name                    : santana.m4a
Format                           : MPEG-4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 4.93 MiB
Duration                         : 3mn 35s
Overall bit rate                 : [COLOR="Red"]192 Kbps[/COLOR]

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format profile                   : LC
Codec ID                         : 40
Duration                         : 3mn 35s
Bit rate mode                    : [COLOR="Red"]Variable[/COLOR]
Bit rate                         : 192 Kbps
Maximum bit rate                 : 219 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 4.89 MiB (99%)
Writing library                  : Nero AAC codec 1.5.4.0
Encoding settings                : -br 192000

So maybe that's the way to go - **RubyRipper** with **neroAacEnc**.:D

---

### Post by ukbeast on 2011-03-17
Thank you ron999 I tried this before but it seems to take along time to rip due to it's using accurate rip.

I'll try again with it thanks again.

---

### Post by ron999 on 2011-03-17
> **ukbeast said:**
> ...but it seems to take along time to rip due to it's using accurate rip.

In RubyRipper > Preferences > Secure Ripping
set 
'Match all Chunks' and 'Match Erroneous Chunks' to **2**.
Then it will only take twice as long as SoundJuicer.:D

---

### Post by ukbeast on 2011-03-17
> **ron999 said:**
> In RubyRipper > Preferences > Secure Ripping
set 
'Match all Chunks' and 'Match Erroneous Chunks' to **2**.
Then it will only take twice as long as SoundJuicer.:D

is this line correct?

neroAacEnc -br 192000  -if %i -of "%o.m4a"  -w --artist "%a" --title "%t" --genre "%g" --album "%b" --track %n --year "%y" %i -o "%o".m4a

thanks again.

I spent way to much time using WMP XD

---

### Post by ron999 on 2011-03-17
> **ukbeast said:**
> is this line correct?

neroAacEnc -br 192000  -if %i -of "%o.m4a"  -w --artist "%a" --title "%t" --genre "%g" --album "%b" --track %n --year "%y" %i -o "%o".m4a


That line will work - but you won't get any tags.:-(

With neroAacEnc it's probably best to install **neroAacTag** if you want tags.
It comes in the package that you downloaded from nero.

When neroAacTag is installed paste in this line:-
```
neroAacEnc -br 192000 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track="%n" -meta:title="%t"

```

---

### Post by Yellow Pasque on 2011-03-17
Is there a reason you need CBR?

---

### Post by mc4man on 2011-03-18
> **ukbeast said:**
> Thank you ron999 I tried this before but it seems to take along time to rip due to it's using accurate rip.

I'll try again with it thanks again.
Starting with lucid the ruby libs used by RR will cause ripping from the gui to take quite a long time. (hangs between tracks

So the simple solution is to set up RR in the gui but run the rip and encode from the cli with rrip_cli

If you wish to not do interactivly then add either a -a or -d depending on RR version (the current is -d
Ex
rrip_cli -a
or
rrip_cli -d

Otherwise to use the gui in a timely fashion you'd need to switch some libs to the 1.9.X ruby and provide a newer ruby-gtk

one method for that shown here, post 174
[http://ubuntuforums.org/showthread.php?t=799621&page=11](http://ubuntuforums.org/showthread.php?t=799621&page=11)

---

### Post by shantiq on 2011-03-18
there is one player that will give you constant bitrate by default called pacpl

```
sudo apt-get install pacpl
```


then   (first create a folder called aactrax on desktop)

```
pacpl  --outdir ~/Desktop/aactrax --rip all  -t  aac  --aacqual 122

```

and that gave me constant bitrate in each track but not quite the same for all trax   was between 180 and 200 kbps   but **each one** constant








found [this]("http://wiki.multimedia.cx/index.php?title=Understanding_AAC") tho about aac

> AAC is a variable bitrate (VBR) block-based codec where each block decodes to 1024 time-domain samples. Allegedly, each frame stands alone and does not depend on previous frames (whereas many perceptual audio codecs overlap data with the previous frame).


could explain why it is not cbr easily

---

### Post by shantiq on 2011-03-18
> **ukbeast said:**
> is this line correct?

neroAacEnc -br 192000  -if %i -of "%o.m4a"  -w --artist "%a" --title "%t" --genre "%g" --album "%b" --track %n --year "%y" %i -o "%o".m4a

thanks again.

I spent way to much time using WMP XD



no Beast it is not if you want cbr   this will do it

```
neroAacEnc -[COLOR="Red"]cbr[/COLOR] 192000  -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t
```


cbr makes it constant   br is not constant:KS


you will need to have neroAacTag installed to do this    explained [URL="http://ubuntuforums.org/showpost.php?p=10324294&postcount=4"]here   also codec attached
[/URL]

probably the only way to get really constant aac on linux ??    If Anyone needs guidelines on how to install neroAacEnc maybe [read]("http://ubuntuforums.org/showpost.php?p=10324294&postcount=4")



ACTually just did a disc to check   and yes all constant at 191kbps  :KS:KS:KS:KS:KS   but i hope one kilobite out is cool    not sure why tho?

---

### Post by ukbeast on 2011-03-20
Thanks for the help guys:D
Problem solved and I can enjoy high quality music for my PSP;)

Bye))):P

---

### Post by t2kburl on 2011-04-06
> **shantiq said:**
> no Beast it is not if you want cbr   this will do it

```
neroAacEnc -[COLOR="Red"]cbr[/COLOR] 192000  -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t
```


cbr makes it constant   br is not constant:KS


you will need to have neroAacTag installed to do this    explained [URL="http://ubuntuforums.org/showpost.php?p=10324294&postcount=4"]here   also codec attached
[/URL]

probably the only way to get really constant aac on linux ??    If Anyone needs guidelines on how to install neroAacEnc maybe [read]("http://ubuntuforums.org/showpost.php?p=10324294&postcount=4")



ACTually just did a disc to check   and yes all constant at 191kbps  :KS:KS:KS:KS:KS   but i hope one kilobite out is cool    not sure why tho?

maybe a dumb question here, but what do the %i and %o etc do? I'm trying to make a bash script for this using files ripped to *.wav and when I used the code from here it cant find the files. This worked for encoding, but made all the metadata %whatever. Am I missing something?

```
neroAacEnc -q 1 -br 192000 -2pass -if "${file%.*}".wav -of "${file%.*}".m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t
```

---

### Post by shantiq on 2011-04-06
well t2 i is input o is output


also  i am under the impression that wave files do not carry tagging so that will explain why they will not appear in you final m4a


you can use this here but no tags


```
for f in *.wav; do neroAacEnc  -cbr 192000    -if  "$f"  -of  "${f%.wav}.m4a"; done 
```



                 ================================



on the other end if you start from flac    see below     the tags are there to start so they end up in the final files




here is a bash from flac to m4a(courtesy of Mc4man)

```
#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.m4a/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKTOTAL=`metaflac "$f" --show-tag=TRACKTOTAL | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$f" - | neroAacEnc -if -  -cbr 516000 -of  "$OUTF"
neroAacTag "$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" -meta:album="$ALBUM" -meta:genre="$GENRE" -meta:year="$DATE" -meta:track="$TRACKNUMBER" -meta:totaltracks="$TRACKTOTAL"
done
mkdir "$ALBUM" && mv *.m4a "$ALBUM"
```

---

### Post by andrew.46 on 2011-04-06
> **ron999 said:**
> Even if I use faac as a stand-alone converter using a 192Kbps ABR option MediaInfo shows _152Kbps_ VBR.:confused:

```
faac -b 192 -w santana.wav
[...]
General
Complete name : santana.m4a
Format : MPEG-4
Format profile : Base Media / Version 2
Codec ID : mp42
File size : 3.90 MiB
Duration : 3mn 35s
Overall bit rate : 152 Kbps
Writing application : FAAC 1.26.1

Audio
ID : 1
Format : AAC
Format/Info : Advanced Audio Codec
Format profile : LC
Codec ID : 40
Duration : 3mn 35s
Bit rate mode : Variable
Bit rate : 151 Kbps
Maximum bit rate : 179 Kbps
Channel(s) : 2 channels
Channel positions : Front: L R
Sampling rate : 44.1 KHz
Compression mode : Lossy
Stream size : 3.86 MiB (99%) 

```


Seems odd, my own copy of faac is a little more accurate:

```

andrew@skamandros~/music/YouTube$ **[COLOR="Red"]faac -b 192 -w test.wav [/COLOR]**
Freeware Advanced Audio Coder
FAAC 1.28

Average bitrate: 192 kbps
Quantization quality: 100
Bandwidth: 20872 Hz
Object type: Low Complexity(MPEG-4) + M/S
Container format: MPEG-4 File Format (MP4)
Encoding test.wav to test.m4a
   frame          | bitrate | elapsed/estim | play/CPU | ETA
 5224/5224  (100%)|  191.6  |    8.1/8.1    |   15.05x | 0.0 

andrew@skamandros~/music/YouTube$ **[COLOR="Red"]mediainfo test.m4a [/COLOR]**
General
Complete name                    : test.m4a
Format                           : MPEG-4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 2.79 MiB
Duration                         : 2mn 1s
**[COLOR="Red"]Overall bit rate                 : 193 Kbps[/COLOR]**
Encoded date                     : UTC 2011-04-06 08:38:54
Tagged date                      : UTC 2011-04-06 08:39:02
Writing application              : FAAC 1.28

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format profile                   : LC
Codec ID                         : 40
Duration                         : 2mn 1s
[B][COLOR="Red"]Bit rate mode                    : Variable
Bit rate                         : 192 Kbps
Maximum bit rate                 : 220 Kbps[/COLOR][/B]
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 2.77 MiB (99%)
Encoded date                     : UTC 2011-04-06 08:38:54
Tagged date                      : UTC 2011-04-06 08:39:02


```

Slightly different version of faac but I am not sure that that would make such a big difference....

---

### Post by t2kburl on 2011-04-06
I got it, thanks :)

Figured out that the %x part listed above for all the tags was from the metadata acquired by rubyrip.

I'm doing flac to m4a

This needs to be run in the directory with the flac files in it, so there is room for improvement.

```
#!/bin/bash

for f in *.flac
do
pacpl -t wav "${f%.*}".flac
done

for file in *wav
do
neroAacEnc -q 1 -br 192000 -2pass -if "${file%.*}".wav -of "${file%.*}".m4a
done

for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.m4a/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKTOTAL=`metaflac "$f" --show-tag=TRACKTOTAL | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$f" -| neroAacTag "$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" -meta:album="$ALBUM" -meta:genre="$GENRE" -meta:year="$DATE" -meta:track="$TRACKNUMBER" -meta:totaltracks="$TRACKTOTAL"-add-cover:front:folder.jpg
done
mkdir "$ALBUM" && mv *.m4a "$ALBUM" 
```

edit: oops! It appears I need to adjust my settings a bit. No 2pass and either drop the -br or the -q setting, since they are somewhat redundant (and not set to give similar results!).

[http://www.hydrogenaudio.org/forums/index.php?showtopic=44310]("http://www.hydrogenaudio.org/forums/index.php?showtopic=44310")

---

