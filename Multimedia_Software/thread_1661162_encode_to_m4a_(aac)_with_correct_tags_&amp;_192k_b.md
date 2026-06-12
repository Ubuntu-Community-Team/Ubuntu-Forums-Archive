---
title: "encode to m4a (aac) with correct tags &amp; 192k bitrate"
date: 2011-01-06
forum: Multimedia Software
---

### Post by piedro on 2011-01-06
Hello! 

I tried all kinds of different programs to convert flac files to m4a oe aac files. I tried to get a bitrate of 192k. It won't work correctly! 

- sound-converter converts the files and tags but the resulting files show no bitrate at all! 
- using ffmpeg on hte commandline with -ab 192k results in files also not showing any bitrate in any musicplayer. (same with nautilus file information!). Using media info on any resulting file shows no bitrate at all. 

The files will play still but I need to compare some files so I need the bitrate. I used ffmpeg -i on the files and voila: they show a bitrate but with 152k instead of 192k!!! 

How to encode these files correctly transfering the metatags and getting a correct bitrate of 192k which is also shown when looking at the audio file info? 

plz help, 
thx for reading, 
piedro

---

### Post by ron999 on 2011-01-06
Hi
I think that the faac encoder is _**variable bitrate**_. That's why you don't see accurate readings.
From faac --long-help it says:-
> -b <bitrate>	Set average bitrate (ABR) to approximately <bitrate> kbps.

This is the command that I'd use with ffmpeg
```
ffmpeg -i filename.flac -acodec libfaac -b 192k -map_meta_data 0:0 output.m4a

```
It transfers the meta-data OK.
But mediainfo and ffmpeg -i both show the result as 64kbps, so I think it's the VBR thing that's confusing them.

[SIZE="2"]> Complete name                    : output.m4a
Format                           : MPEG-4
Format profile                   : Apple AAC audio with iTunes info
Codec ID                         : M4A 
File size                        : 3.02 MiB
Duration                         : 6mn 18s
Overall bit rate                 : 66.8 Kbps
Album                            : Live Rust
Track name                       : Cortez the Killer
Track name/Position              : 12
Track name/Total                 : 0
Performer                        : Neil Young and Crazy Horse
Genre                            : Rock
Encoded date                     : 1979
Writing application              : Lavf52.84.0

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 6mn 18s
Bit rate mode                    : Variable
Bit rate                         : 64.0 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 2.89 MiB (96%)
[/SIZE]

---

### Post by ron999 on 2011-01-06
EDIT
There's an error in my command above.
It should be [SIZE="5"]**-ab**[/SIZE] instead of -b.

Like this:-
```
ffmpeg -i filename.flac -acodec libfaac -ab 192k -map_meta_data 0:0 output.m4a
```

mediainfo then shows 152Kbps.
So I still think that the VBR confuses it.

> Complete name                    : /home/ron/output.m4a
Format                           : MPEG-4
Format profile                   : Apple AAC audio with iTunes info
Codec ID                         : M4A 
File size                        : 6.99 MiB
Duration                         : 6mn 18s
Overall bit rate                 : 155 Kbps
Album                            : Live Rust
Track name                       : Cortez the Killer
Track name/Position              : 12
Track name/Total                 : 0
Performer                        : Neil Young and Crazy Horse
Genre                            : Rock
Encoded date                     : 1979
Writing application              : Lavf52.84.0

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 6mn 18s
Bit rate mode                    : Variable
Bit rate                         : [COLOR="Red"]152 Kbps[/COLOR]
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Stream size                      : 6.87 MiB (98%)



---

### Post by shantiq on 2011-01-06
well using neroAacEnc (enclosed) will give a constant bitrate

```
flac * -d &&
for f in *.wav; do neroAacEnc -cbr 192000  -if "$f"  -of "${f%.wav}.m4a"; done
```


but one had to encode from wav so no tags:KS:KS    not sure this is better


[B]to install neroAacEnc
[/B]

place in home folder

then  ```
sudo cp neroAacEnc /usr/bin
```


and then    ```
cd /usr/bin
```

then   ```
 sudo chmod +x neroAacEnc
```




there has to be a way to do it all 192 constant +tags  let us think

---

### Post by FakeOutdoorsman on 2011-01-06
You can verify the bitrate of the output file: bitrate = filesize / duration. For example, a [color=green]7[/color] MB file that is [color=blue]378[/color] seconds long: ([color=green]7[/color]*1024)8 / [color=blue]378[/color] = ~152 kilobits per second.

This doesn't mean that the file was encoded at a constant bitrate of 152 Kbps.

---

### Post by piedro on 2011-01-06
Wow, that's alot of great advice. 

And yes: this is exactly the same phenomena I experienced: got the tags, but bitrate showing 152k (which I also figured probalbly to be a variable one ...).  
So by applying -ab 192k I get an average vbr of 152k - that's at least unexpected, isn't it? 

Most of my music collection was encoded by apples itunes on an old apple machine. All those files are constant bitrate 192k. So for good measure it would be nice to get some consistency by encoding my flacs ripped by my new linux box to the same format. 

I like your nero encoder solution also but retagging is a bit of a nuisance. BTW: I never realized that you can't get the tags from wav ... 

I also tried "Mobile Media Converter" but I gave up at creating a profile for that one to do the job.

---

### Post by shantiq on 2011-01-07
piedro    192k is really quite a "thin" pared down version of a piece of music       why do you not rip to flac/alac/wavpack/ape/alac  etc from now on on your linux machine     the sound quality of your music files becomes much higher    192 m4a is really like fatfree slimline audio

but of course it is your choice   if you want to rip directly to aac  192k you can use [rubyripper]("http://linuxappfinder.com/package/rubyripper") for that with tags and constant bitrate

you will need to do with neroAacTag the same install process you have to do with neroAacEnc




**once rubyripper is installed** settings are
preferences/codecs/other
the other  command line is

```
neroAacEnc -cbr 192000 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t
```


There you have aac 192 tagged :KS    and you can tick flac at the same time and compare the quality of both files

**ps ** rubyripper  often handles better starting with the command line
```
rrip_gui 
```   for the settings   and ```
rrip_cli
```    for the rip

 
Anyway thought i would add this

---

### Post by cascade9 on 2011-01-07
> **shantiq said:**
> piedro    192k is really quite a "thin" pared down version of a piece of music       why do you not rip to flac/alac/wavpack/ape/alac  etc from now on on your linux machine     the sound quality of your music files becomes much higher    192 m4a is really like fatfree slimline audio

+1....well, +1 on flac, +0.5 on wavapck and -losts and lots on ALAC (why go to a closed source codec with crap support?) and .ape (ape is a joke.....read the licence if you dont believe me) 

In these days of super cheap 1TB+ sized drives, lossless makes great sense.

---

### Post by shantiq on 2011-01-07
> **cascade9 said:**
> +1....well, +1 on flac, +0.5 on wavapck and -losts and lots on ALAC (why go to a closed source codec with crap support?) and .ape (ape is a joke.....read the licence if you dont believe me) 

In these days of super cheap 1TB+ sized drives, lossless makes great sense.


well Cascade we from time to time have these chats about:KS:KS:KS codecs   i  personally do not care for ape and agree with you there


only mentioned as it is popular with many and people have heard about it   

you know my favourite ... :KS

as regards alac i love it   i know it is mac's baby but i adore it and it is very well handled on linux    all players play it 

Players which handle alac 

VLC plays them 
QMMP (right-click on player/settings/plugins/FFmpeg plugin/highlight/Preferences/Tick alac )
deadbeef 
aqualung
audacious
xine

  and rubyripper will rip it for you in style with help from ffmpeg

```
ffmpeg  -i %i -acodec alac  "%o".m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track="%n" -meta:title="%t"

```

wavpack is really cool    no beef there


again rubyripper

```
wavpack -w "Artist=%a" -w "Title=%t" -w "Album=%b" -w "Year=%y" -w "Track=%n" -w "Genre=%g" -hhm %i -o "%o.wv"

```

---

### Post by cascade9 on 2011-01-07
> **shantiq said:**
> as regards alac i love it   i know it is mac's baby but i adore it and it is very well handled on linux    all players play it 

wavpack is really cool    no beef there


You know what I've said before.......if its lossless, there should be no difference in output quality (depending on decoder). 

ALAC is playable under linux, but the decoders were all written from scratch (by reverse engineering of quicktime .dlls), since apple didnt release ANY specifications on the format. Sod apple. 

wavpack isnt bad, but hybrid ripping (one of the main points of wavpack) is pretty much useless, it takes more CPU time to decode compared to flac, and flac has far more support in portable media players, etc.  (mainly thanks to the extra CPU time needed by wavpack). So IMO flac is better. 

IMO there are too many open source lossless codecs. Division will just make things easier for microsoft (with WMA lossless) and apple (with ALAC) to tie up the market.

---

### Post by FakeOutdoorsman on 2011-01-07
Here's an interesting article from a FFmpeg developer: [Why Lossless Audio Codecs generally suck](http://codecs.multimedia.cx/?p=313).

---

### Post by mc4man on 2011-01-07
One way w/ neroAacEnc and tags (at least some
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

flac -c -d "$f" - | neroAacEnc -if -  -q 0.[COLOR="Blue"]65[/COLOR] -of  "$OUTF"
neroAacTag "$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" -meta:album="$ALBUM" -meta:genre="$GENRE" -meta:year="$DATE" -meta:track="$TRACKNUMBER" -meta:totaltracks="$TRACKTOTAL"
done
[COLOR="Blue"]mkdir "$ALBUM" && mv *.m4a "$ALBUM"[/COLOR]
```

Blue is adjustable, for a br then adjust as such

```
neroAacEnc -if -  -br 192000
```

see neroAacEnc -help

Assumes neroAacEnc and neroAacTag in path and executable

---

### Post by shantiq on 2011-01-07
> **FakeOutdoorsman said:**
> Here's an interesting article from a FFmpeg developer: [Why Lossless Audio Codecs generally suck](http://codecs.multimedia.cx/?p=313).


thanx for that bloody hilarious :D

==============================================

mc4man that is astounding :-k

---

### Post by mc4man on 2011-01-08
shantiq - 
because i know you like such things, a couple of varitions of above for alac
The ffmpeg tagging one won't do tracktotal correct, ffmpeg seems to have an issue, varied the save location method in both so you can see ...

Also am attaching an interesting one I came across, forget if it workedright or needed some adjustment.

(have a couple of mp3hd ones lying about (wmal2mp3hd and flac2mp3hd..

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

mkdir "$ALBUM" 

flac -c -d "$f" - | ffmpeg -i -  -acodec alac  ./"$ALBUM/$OUTF"
neroAacTag ./"$ALBUM/$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" -meta:album="$ALBUM" -meta:genre="$GENRE" -meta:year="$DATE" -meta:track="$TRACKNUMBER" -meta:totaltracks="$TRACKTOTAL"
done
```

```
#!/bin/bash
for f in *.flac
do
   ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
   ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
mkdir "$ARTIST-$ALBUM"

 ffmpeg  -i "$f" -acodec alac \
	-metadata title="$(metaflac --show-tag=TITLE "$f" | sed 's/TITLE=//g')" \
	-metadata artist="$(metaflac --show-tag=ARTIST "$f" | sed 's/ARTIST=//g')" \
	-metadata album="$(metaflac --show-tag=ALBUM "$f" | sed 's/ALBUM=//g')" \
	-metadata date="$(metaflac --show-tag=DATE "$f" | sed 's/DATE=//g')" \
	-metadata genre="$(metaflac --show-tag=GENRE "$f" | sed 's/GENRE=//g')" \
	-metadata track="$(metaflac --show-tag=TRACKNUMBER "$f" | sed 's/TRACKNUMBER=//g')" \
	"./$ARTIST-$ALBUM/${f%.flac}.m4a"
done
```

---

### Post by shantiq on 2011-01-08
:KS:KS thank you

---

### Post by piedro on 2011-01-16
Wow! Ok ...

Shantiq@ 
First of all about fatfree slimline audio: 
What's wrong about that. Please trust me in asking  question with some thought on it beforehand. I see your point in lossless formats, 
I prefer wavpack & FLAC btw, but I have about 45 000 tracks on a server fed by 7 persons in a living association. While everyone should have access (without necessarily owning the lossless original) using linux, MAC & Windows boxes (plus three laptops) and a variety of mobile devices, 4 of them being iPods, I had to find a compromise in a format and in choosing a bitrate. Filesize does matter in our scenario and bandwidth of the WLAN does also! (Forgot to mention 2 wireless PS3s ...)

So fatfree slimline is a good thing. Most of the music ripped by itunes does enter the server in 192k m4a, a lot of music seems to be in 128k mp3 which doesn't make too much sense to me. But: I can't re-rip all the albums neither can I use wavpack on some files (everyone has to recode for mobiles by him/herself) while leaving the majority in other formats. I have my music in FLAC but I re-rip the tracks with an apple laptop via itunes to 192k m4a which seems to be a good way to go for most of our uses ... 

I like to avoid this because my ubuntu desktop box is much faster in encoding. But I want to assure I get it right. Correct bitrate,  correct tags. I won't accept files messing up the server due to formating and tagging by the other guys, so I have to get it right myself. 

BTW: 192k quality seems to be alright to listen to. I can't hear any significant difference in quality to FLACs. Maybe it's my sound hardware is too bad ...

Long answer? Yes. But it's a bit like posing a problem as "How to walk from here to the university?" to get answers like "Don't walk - take a cab!" or "Why would you want to study?" ... 

But still: Thanks a lot for your efforts and discussing. 

@mc4man: Thanks so much for your solutions! I will thoroughly test the Neroenc script alternatives asap. They sound like a good solution. Though I probably still have to use musicbrainz afterwards to fill the missing tags. I really appreciate. 

thx for reading and discussing the topic everyone, 
piedro

---

### Post by shantiq on 2011-01-17
Piedro if you have to share so many tracks and load ipods then aac might be cool for your needs here

but it is very little info 192kbps and PERSONALLY i feel i am listening to the skeleton of a track with all the flesh and muscle removed


wav/cda is 1411kbps     lossless typically in the 500-1000 range    so we can see what is left with 192       a fraction of the original



by the way fine for mp3players    i have tried 320mp3 and wav on a player and no difference i could hear

on a laptop speakers some difference is heard but not huge



or if you plug your computer into a stereo system ( my most likely setup ) then it really matters    i then favour 24-bit flac or wavpack  or any of the lossless formats 



so it depends what you want your music for  not everybody needs audiophile quality and in your case you have so many trax your choice might be right for you

matter of of taste in the end

---

