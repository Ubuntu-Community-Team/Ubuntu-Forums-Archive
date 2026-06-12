---
title: "convert FLAC to ALAC"
date: 2008-08-14
forum: Multimedia Software
---

### Post by CNLiberal on 2008-08-14
I have some FLAC files that I'd like to play on my iPod but I don't want to change the firmware on my iPod.  My iPod currently connects to the stereo in my SUV through a specialzed iPod connector that Alpine made.  Is there a way to convert FLAC files to ALAC (Apple Lossless Audio Codec) so I can transfer the songs to my iPod via gtkpod or Songbird?  Thanks!

Jim

---

### Post by cozmicharlie on 2008-08-15
There is a lot of confusion concerning Apple Lossless (ALAC).  Many think .m4a is the same but it is not.  Part of the confusion lies in the fact that ALAC has a .m4a extension like AAC but it is not AAC.  In reality though what you get from the Apple store is really aac.  The codec has been reversed engineered and you can get an ALAC decoder through Synaptic.  But, I don't know of any transcoders for ALAC.  I would recommend aac of which there are a number of good transcoder.  aacplusenc is one of the best transcoders for aac ([http://ubuntuforums.org/showthread.php?t=631835&highlight=aacplusenc](http://ubuntuforums.org/showthread.php?t=631835&highlight=aacplusenc)).  It is available in Synaptic or via a deb file.  PACPL ([http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl)) is also excellent and uses the aacplusenc transcoder - the advantage of PACPL is you can integrate it in to Amarok.  If you want a gui then SoundKonverter (with a k not a c) is the best IMHO - you can install it from Synaptic.  These will all transcode your flac files to high quality aac that can be played on your ipod.  You will also want to install gtkpod-aac.

Enjoy

---

### Post by CNLiberal on 2008-08-15
Thanks for your reply cozmicharlie!

It's sounding like nobody cares about lossless audio on their iPod using Linux?  I'd really like to start using lossless.  Anyone else know of an answer?  Thanks!

---

### Post by cozmicharlie on 2008-08-15
Actually, I think most do care about lossless.  That's why you read a lot of posts in the forums recommending Rockbox (I run Rockbox on my ipod). I would recommend Rockbox also, but you mentioned that do not want to change the native firmware so your options are limited. 

Someone else may have a some suggestions though.

Enjoy

---

### Post by CNLiberal on 2008-08-17
Yeah, I only wish that Rockbox worked with my Alpine KCA-420i.  I've read the Rockbox forums and they say they can't get it working, mostly because no one has one and is willing to put in the time.  I know nothing about programming so I'm relatively worthless.  :-D

---

### Post by cozmicharlie on 2008-08-17
Thats too bad.  I think the best you can do is use aac (that is really what you get when you buy Apple Lossless from itunes).  Use the aacplusenc transcoder (it is better than faac).  The quality should be just as good as Apple Lossless.

---

### Post by jimav on 2009-11-14
ALAC is *not* a variant of AAC.  They use the same MP4 container (probably why both types of files use the .m4a extension), which causes confusion.

ALAC is a completely different (and lossless) compression algorithm.  In contrast, AAC is a lossy compression scheme conceptually similar to MP3.  

See [http://en.wikipedia.org/wiki/Apple_Lossless](http://en.wikipedia.org/wiki/Apple_Lossless)

So encoding our FLAC files as AAC will result in loss of quality.  

What is needed is a true ALAC encoder for linux.  Does anyone have info on such a thing?

---

### Post by andrew.46 on 2009-11-14
Hi jimav,

> **jimav said:**
> What is needed is a true ALAC encoder for linux.  Does anyone have info on such a thing?

Looks like FFmpeg can decode/encode alac:

```

andrew@skamandros~$**[COLOR="Red"] ffmpeg -formats | grep alac[/COLOR]**
FFmpeg version SVN-r20529, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 13 2009 10:20:28 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter
 --enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab
 --enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libopencore-amrnb 
--enable-libopencore-amrwb --enable-version3 --enable-libspeex --enable-zlib 
--enable-nonfree --enable-gpl
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1. 8. 0 /  1. 8. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
**[COLOR="Red"] DEA    alac            ALAC (Apple Lossless Audio Codec)[/COLOR]**

```

But I will admit I have never had the need to experiment with this codec so I cannot suggest specific syntax.

Andrew

---

### Post by mc4man on 2009-11-14
Was actually tring this the other day in response to something, basically just 
ffmpeg -i <input> -acodec alac <output>.m4a

Did a number of compares, re-encodes, re-re-encodes, ect. seemed just fine 

Otherwise install  dBpoweramp in wine (to some extent free for 30 days)

---

### Post by jimav on 2009-12-29
Thanks for the pointer to ffmpeg!

I tried a round-trip encode/decode using ffmpeg + alac-decoder and got back a .wav file of exactly the same length as the original one, but different contents.  The diffs start at byte 5, so I suspect the headers differ, maybe because I need some decode options to make the same kind of .wav file (?).  However the 'file' command says they are the same format.

Does anyone see why this test fails?  

```
+ ffmpeg -i original.wav -acodec alac new.m4a
+ alac-decoder -f recreated.wav new.m4a
+ file original.wav recreated.wav new.m4a
original.wav:  RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 44100 Hz
recreated.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 44100 Hz
new.m4a:       ISO Media, MPEG v4 system, iTunes AAC-LC

+ ls -l original.wav recreated.wav new.m4a
-rw-r--r-- 1 jima jima 91673948 2009-11-06 17:49 original.wav
-rw-r--r-- 1 jima jima 91673948 2009-12-29 00:25 recreated.wav
-rw-r--r-- 1 jima jima 60855313 2009-12-29 00:25 new.m4a
+ cmp original.wav recreated.wav
**original.wav recreated.wav differ: byte 5, line 1**
```

---

### Post by Nighto on 2010-03-08
FFmpeg can convert from FLAC to ALAC. I used it to convert my FLAC files in order to play them on iPod Touch.

I created a script to easily convert them:

```
#!/bin/sh

echo ""
echo "flac2alac - script de conversão de áudio FLAC para ALAC"
echo "Este script usa o ffmpeg para conversão de áudio do tipo"
echo "FLAC (Free Lossless Audio Codec) para ALAC (Apple Lossless Audio Codec)."
echo "Por Arlindo \"Nighto\" Pereira"
echo ""

if [ "$1" ]
then
	ffmpeg  -i "$1" -acodec alac "`basename "$1" .flac`.m4a" \
		-metadata title=\""$(metaflac --show-tag=TITLE "$1" | sed 's/TITLE=//g')"\" \
		-metadata author=\""$(metaflac --show-tag=ARTIST "$1" | sed 's/ARTIST=//g')"\" \
		-metadata album=\""$(metaflac --show-tag=ALBUM "$1" | sed 's/ALBUM=//g')"\" \
		-metadata year=\""$(metaflac --show-tag=DATE "$1" | sed 's/DATE=//g')"\" \
		-metadata track=\""$(metaflac --show-tag=TRACKNUMBER "$1" | sed 's/TRACKNUMBER=/$
		-metadata genre=\""$(metaflac --show-tag=GENRE "$1" | sed 's/GENRE=//g')"\"
else
	echo "Entre com o nome do arquivo para converter:"
	echo "flac2alac arquivo.flac"
	echo ""
exit 1
fi
```

[http://nighto.net/convertendo-flac-para-alac/](http://nighto.net/convertendo-flac-para-alac/)

It's comments are in portuguese but the important bits remain the same.

With this script saved on /usr/local/bin (don't forget to make it executable!) you can convert your files in batch like this:

```
for i in *.flac; do flac2alac "$i"; done
```

Cheers,
Arlindo "Nighto" Pereira

---

### Post by shantiq on 2010-06-03
> **mc4man said:**
> Was actually tring this the other day in response to something, basically just 
ffmpeg -i <input> -acodec alac <output>.m4a

Did a number of compares, re-encodes, re-re-encodes, ect. seemed just fine 

Otherwise install  dBpoweramp in wine (to some extent free for 30 days)

[B][COLOR="Blue"]Thanx for that
and to convert from alac (m4a) to wav or flac 


```
ffmpeg  -i <input>.m4a  <output>.wav

```
```
ffmpeg  -i <input>.m4a  <output>.flac
```[/COLOR][/B]

---

### Post by conway.federico on 2010-06-06
Ok, so I am new to linux... however I love my .flac´s just the same.  I put in...

```
ffmpeg  -i </home/conway/Downloads/_FLAC/>.flac  </home/conway/Downloads/_M4A/>.m4a
```  gives me the response...

```
conway@conway-laptop:~$ ffmpeg  -i </home/conway/Downloads/_FLAC/>.flac  </home/conway/Downloads/_M4A/>.m4a
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
ffmpeg: missing argument for option '-i'
```

how do I define my missing argument?

---

### Post by shantiq on 2010-06-06
[B][COLOR="Blue"]hi federico your line is a bit wrong


you need to go into your folder where the music file is or [ut it in your home folder Places/home folder   then make sure the name of the file has no gaps


for example change it to   ```
1.m4a
```


then write you ffmpeg line as follows

 ```
ffmpeg  -i 1.m4a 1.flac
```
or    ```
ffmpeg  -i 1.m4a 1.wav
```   if you want wave


hope this is clearer  


there is also another route



FIRST INSTALL alac-decoder from synaptic then run


```
alac-decoder -f output.wav input.m4a

```

where input and output are the name of your music file obviously


[COLOR="DarkRed"]ALSO   alac files play straight off  in the player called xine which is in synaptic


also this player called [deadbeef]("http://deadbeef.sourceforge.net/") plays alac[/COLOR]



[/COLOR][/B]

---

### Post by conway.federico on 2010-06-07
What if I wanted to preserve my file names and tag information?  Not to mention do all my FLAC´s in one batch.

---

### Post by shantiq on 2010-06-08
```

```> **conway.federico said:**
> What if I wanted to preserve my file names and tag information?  Not to mention do all my FLAC´s in one batch.

[B][COLOR="Blue"]hi federico.  this you can do.  


THROUGH WINE
============


install wine from your synaptic.  it is a programme which allows you to install windows programms on a linux system

or from terminal    applications/accessories/terminal

enter

```
sudo apt-get install wine
```



then go to [dBpoweramp]("http://dw.com.com/redir?edId=3&siteId=4&oId=3000-2140_4-10042534&ontId=2140_4&spi=4c7b756007a967c210d72d19ebfac894&lop=link&tag=tdw_dltext&ltype=dl_dlnow&pid=11386222&mfgId=83769&merId=83769&pguid=@2bhiwoPjF8AACY7bOoAAAEo&destUrl=http%3A%2F%2Fdownload.cnet.com%2F3001-2140_4-10042534.html%3Fspi%3D4c7b756007a967c210d72d19ebfac894")   once it is downloaded right-click and open with wine


then   applications/wine/programs/  pick dbpoweramp batch converter   and there you are    all your tags will be kept



it is not a linux only solution but there is one [cascade9 indicated]("http://ubuntuforums.org/showthread.php?t=1500430")


LINUX ONLY SOLUTION
------------------

first in terminal

```
sudo apt-get install gstreamer0.10-plugins-bad
```

then   ```
sudo apt-get install soundconverter
```

open through applications/sound and video

it will also keep your tags and you can batch-convert



[/COLOR][/B]

---

### Post by ppvanzella on 2010-06-14
Metadata is NOT being transfered from my FLACs to the ALACs. Why is that?

---

### Post by giggaflop on 2010-07-03
> **Nighto said:**
> FFmpeg can convert from FLAC to ALAC. I used it to convert my FLAC files in order to play them on iPod Touch.

I created a script to easily convert them:

```
#!/bin/sh

echo ""
echo "flac2alac - script de conversão de áudio FLAC para ALAC"
echo "Este script usa o ffmpeg para conversão de áudio do tipo"
echo "FLAC (Free Lossless Audio Codec) para ALAC (Apple Lossless Audio Codec)."
echo "Por Arlindo \"Nighto\" Pereira"
echo ""

if [ "$1" ]
then
	ffmpeg  -i "$1" -acodec alac "`basename "$1" .flac`.m4a" \
		-metadata title=\""$(metaflac --show-tag=TITLE "$1" | sed 's/TITLE=//g')"\" \
		-metadata author=\""$(metaflac --show-tag=ARTIST "$1" | sed 's/ARTIST=//g')"\" \
		-metadata album=\""$(metaflac --show-tag=ALBUM "$1" | sed 's/ALBUM=//g')"\" \
		-metadata year=\""$(metaflac --show-tag=DATE "$1" | sed 's/DATE=//g')"\" \
		-metadata track=\""$(metaflac --show-tag=TRACKNUMBER "$1" | sed 's/TRACKNUMBER=/$
		-metadata genre=\""$(metaflac --show-tag=GENRE "$1" | sed 's/GENRE=//g')"\"
else
	echo "Entre com o nome do arquivo para converter:"
	echo "flac2alac arquivo.flac"
	echo ""
exit 1
fi
```

[http://nighto.net/convertendo-flac-para-alac/](http://nighto.net/convertendo-flac-para-alac/)

It's comments are in portuguese but the important bits remain the same.

With this script saved on /usr/local/bin (don't forget to make it executable!) you can convert your files in batch like this:

```
for i in *.flac; do flac2alac "$i"; done
```

Cheers,
Arlindo "Nighto" Pereira

lol i then created a extending script so i didn't have to remember the command to do a directory called "dir2alac" which was basically your "for i in *.flac; do flac2alac "$i"; done" but in an executable shell script in the same dir as flac2alac, also your script is incorectly pasted from nano if i guess right it should be

```
#!/bin/sh

echo ""
echo "flac2alac - script de conversão de áudio FLAC para ALAC"
echo "Este script usa o ffmpeg para conversão de áudio do tipo"
echo "FLAC (Free Lossless Audio Codec) para ALAC (Apple Lossless Audio Codec)."
echo "Por Arlindo \"Nighto\" Pereira"
echo ""

if [ "$1" ]
then
        ffmpeg  -i "$1" -acodec alac "`basename "$1" .flac`.m4a" \
                -metadata title=\""$(metaflac --show-tag=TITLE "$1" | sed 's/TITLE=//g')"\" \
                -metadata author=\""$(metaflac --show-tag=ARTIST "$1" | sed 's/ARTIST=//g')"\" \
                -metadata album=\""$(metaflac --show-tag=ALBUM "$1" | sed 's/ALBUM=//g')"\" \
                -metadata year=\""$(metaflac --show-tag=DATE "$1" | sed 's/DATE=//g')"\" \
                -metadata track=\""$(metaflac --show-tag=TRACKNUMBER "$1" | sed 's/TRACKNUMBER=//g')"\" \
                -metadata genre=\""$(metaflac --show-tag=GENRE "$1" | sed 's/GENRE=//g')"\"
else
        echo "Entre com o nome do arquivo para converter:"
        echo "flac2alac arquivo.flac"
        echo ""
exit 1
fi

```

---

### Post by brazilectro on 2010-07-12
Hi, I found the script posted in this topic very useful, however sometimes it doesn't work for me. So I've made 2 modifications:

1. The order of arguments for ffmpeg was changed.
2. Search for metadata now is case insensitive (I flag), since some flac files can have data as: TITLE=... or title=... (note that I flag will not work for some versions of sed)

```

#!/bin/sh

echo ""
echo "Script for converting FLAC audio files to ALAC. Uses ffmpeg."
echo "FLAC (Free Lossless Audio Codec) para ALAC (Apple Lossless Audio Codec)."
echo "By Arlindo \"Nighto\" Pereira"
echo ""

if [ "$1" ]
then
        ffmpeg  -i "$1" \
        -metadata title="$(metaflac --show-tag=TITLE "$1" | sed 's/title=//gI')" \
        -metadata author="$(metaflac --show-tag=ARTIST "$1" | sed 's/artist=//gI')" \
        -metadata album="$(metaflac --show-tag=ALBUM "$1" | sed 's/album=//gI')" \
        -metadata year="$(metaflac --show-tag=DATE "$1" | sed 's/date=//gI')" \
        -metadata track="$(metaflac --show-tag=TRACKNUMBER "$1" | sed 's/tracknumber=//gI')" \
        -metadata genre="$(metaflac --show-tag=GENRE "$1" | sed 's/genre=//gI')" \
        -acodec alac "`basename "$1" .flac`.m4a"
else
        echo "Please enter the name of flac file to convert:"
        echo ""
exit 1
fi

```

---

### Post by MetalMusicAddict on 2010-07-13
Here's mine I've had for a while:

[SIZE="1"]```
#!/bin/bash
#This script depends on the: flac, ffmpeg and mpeg4ip-utils packages.

   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.m4a"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | ffmpeg -i - -acodec alac "$OUTF"
         mp4tags -s "$TITLE" -t "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" -y "$DATE" "$ARTIST - $ALBUM - $TRACKNUMBER - $TITLE".m4a
      done
fi
```[/SIZE]

My full script:
```
[SIZE="1"]#!/bin/bash
#This script depends on the: id3v2, lame, flac, faac, wavpack, mppenc, aacplusenc, gpac, mpeg4ip-utils and vorbis-tools packages.

format=$1
if [ "$format" = "vorbis" ]; then
   for a in *.flac
      do

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         oggenc -q 5 "$a"
      done
fi

if [ "$format" = "mp3" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.mp3"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | lame -V 3 --vbr-new - "$OUTF"
         id3v2 -t "$TITLE" -T "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" -y "$DATE" "$OUTF"
      done
fi

if [ "$format" = "wavpack" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.wv"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | wavpack -w "Artist=$ARTIST" -w "Title=$TITLE" -w "Album=$ALBUM" -w "Year=$DATE" -w "Track=$TRACK$" -w "Genre=$GENRE" -o "$OUTF" -
      done
fi

if [ "$format" = "musepack" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.mpc"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | mppenc --standard --ape2 --artist "$ARTIST" --title "$TITLE" --album "$ALBUM" --year "$DATE" --track "$TRACKNUMBER" --genre "$GENRE" - "$OUTF"
      done
fi

if [ "$format" = "faac" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.m4a"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | faac -w -q 192 --artist "$ARTIST" --track "$TRACKNUMBER" --title "$TITLE" --album "$ALBUM" --year "$DATE" -o "$OUTF" -
      done
fi

if [ "$format" = "aac+" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.aac"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | aacplusenc - "$OUTF" 32
         MP4Box -sbr -new -no-sys -add "$OUTF" "$ARTIST - $ALBUM - $TRACKNUMBER - $TITLE".mp4 
         mp4tags -s "$TITLE" -t "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" -y "$DATE" "$ARTIST - $ALBUM - $TRACKNUMBER - $TITLE".mp4 
         rm *.aac
      done
fi

if [ "$format" = "alac" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.m4a"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -c -d "$a" | ffmpeg -i - -acodec alac "$OUTF"
         mp4tags -s "$TITLE" -t "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" -y "$DATE" "$ARTIST - $ALBUM - $TRACKNUMBER - $TITLE".m4a
      done
fi

if [ "$format" = "mp3hd" ]; then
   for a in *.flac
      do
         OUTF=`echo "$a" | sed s/"\.flac$"/"\.mp3"/g`

         ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
         TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
         ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
         GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
         TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
         DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

         flac -d -o "$TITLE".wav "$a"
         mp3hdEncoder -if "$TITLE".wav -of "$OUTF" -br 0 -mode 1 -Title "$TITLE" -Track "$TRACKNUMBER" -Artist "$ARTIST" -Album "$ALBUM" -Genre "$GENRE" -Year "$DATE"
         rm "$TITLE".wav
      done
fi[/SIZE]
```

Here's the link for the [Mp3HD]("www.all4mp3.com/SoftwareHD.aspx") encoder.

---

### Post by sneak on 2010-09-13
If I'm reading that correctly, that script will not properly convert tags that contain an equals sign ("=") due to the way your regular expression pulls out the tag data.

---

### Post by atca on 2011-11-05
To add to this in case any one else is interested 
I've pulled together a script which converts a CD to FLAC and ALAC transcribing the meta data between FLAC and ALAC since they ue slightly different formats. It also performs conversion frmo FLAC to ALAC as part of this process and could be easily modified to go the other way. It takes the whole process from rip to FLAC/ALAC rip with 2 clicks and in under 15 minutes, it can also be used to batch CD rips.

See [here]("http://confoundedtech.blogspot.com/2011/11/ubuntu-automatically-rip-cd-to-flac-and.html")

---

### Post by ruupie on 2012-03-03
Simple python script to convert single file or recursed directory from flac to alac (m4a)

```

#!/usr/bin/env python 
'''
Created on Mar 3, 2012

@author: ruben
'''
#======================
# Settings
#======================
DELETE_ORGINAL = False
VERBOSE = True

#======================
# Code
#======================
import sys
import subprocess as sp
import os

def convert_dir(dirname):
    """ Recursively walk to dir and subdirs to find flacfiles and convert them
    """
    
    def process_directory(arg, curdir, filenames):
        if os.path.basename(curdir).startswith('.'):
            return
        print 'Processing directory: %s'%curdir
        flacfiles = sorted(filter(lambda x: os.path.splitext(x)[1] == '.flac', filenames))
        
        if not flacfiles:
            print 'No flac files found!'
            return
        
        for f in flacfiles:
            try:
                file_ = os.path.join(curdir, f)
                convert_file(file_)
                if DELETE_ORGINAL:
                    os.remove(file_)
            except:
                pass
            
    
    os.path.walk(dirname, process_directory, None)
    


def convert_file(flacfile):
    """ Convert single flac file
    """
    filename, ext = os.path.splitext(flacfile)
    if not ext == '.flac':
        exit('%s is not a flac file'%flacfile)
        
    flacbasename = os.path.basename(flacfile)
    m4afile = '%s%s'%(filename, '.m4a')
    
    if os.path.exists(m4afile):
        msg = 'SKIPPED %s because m4a already exists!'%flacbasename
        print msg
        raise Exception(msg)
        
    
    print 'Converting file: %s'%(flacbasename) ,
    
    tags = FlacHelper(flacfile).tags
    
    
    m4a_fields = {
         'author':tags['artist'],         'title':tags['title'],
         'album':tags['album'],           'year':tags['year'],
         'track':tags['track'],           'genre':tags['genre'],
         'comment':tags['comment'],       'disc':tags['disc'],
         'totaltracks':tags['totaltracks'],
      }

    meta = ' '.join(['-metadata %s="%s"'%(field, value) for field, value in m4a_fields.items() if value]) 
    
    cmd = 'ffmpeg -i "%s" %s -acodec alac "%s"'%(flacfile, meta, m4afile)
     
    stderr = sp.STDOUT if VERBOSE else file('/dev/null')
 
    err = sp.call(cmd, shell=True, stderr=stderr)
    
    success = err == 0
    print '[SUCCES]' if success else '[FAILED]'
    
    if not success: 
        raise Exception('Error during flac convertion')



#======================
# Helpers
#======================
class FlacHelper( object ):
    FLAC_TAGS = {
      'album':'album',
      'artist':'artist',
      'comment':'comment',
      'composer':'composer',
      'copyright':'copyright',
      'description':'description',
      'disc':'discnumber',
      'genre':'genre',
      'license':'license',
      'performer':'performer',
      'title':'title',
      'track':'tracknumber',
      'totaltracks':'tracktotal',
      'year':'date',
      }

    def __init__(self, name):
        self.name = name
        
    @property
    def tags(self):
        return dict((k,self._read_tag(v)) for k,v in self.FLAC_TAGS.items())

    def _read_tag(self,field):
        val = sp.Popen( 'metaflac --show-tag=%s "%s"' % (field,self.name),
            shell=True, stdout=sp.PIPE).communicate()[0]
    
        return val.split('=')[1].strip() if val else None


#======================
# Main
#======================

if __name__ == '__main__':
    if len(sys.argv) <= 1:
        exit('Please enter file or directory to convert')
        
    param = sys.argv[1]
    
    if not os.path.exists(param):
        exit('File or path not found! (%s)'%param)
    
    if os.path.isdir(param):
        convert_dir(param)
        exit(0)
        
    if os.path.isfile(param):
        convert_file(param)
        exit(0)

    print 'ehh?'

```

---

### Post by shantiq on 2012-03-04
guys these days you can also simply use ffmpeg  thus   [it keeps all tags]


**for a single file**


> ffmpeg -i filename.flac  -acodec alac   filename.m4a


**and bulk convert**



```
for f in *.flac; do ffmpeg -i "$f" -acodec alac "${f%.flac}.m4a"; done 
```



**to enter multiple folders and do same**

> for i in */
do
  cd "$i"
  for f in *.flac; do ffmpeg -i "$f" -acodec alac "${f%.flac}.m4a"; done
  cd ..
done

---

### Post by evilsoup on 2012-03-04
For most formats, ffmpeg does indeed preserve tags.
However, this thread prompted me to test that out, and unfortunately it doesn't preserve tags between FLAC and ALAC (I also tested .mp3 to ALAC, not that there would be any point in converting from mp3 to ALAC, and that also didn't keep metadata). I assume this oversight is because the ffmpeg devs just don't use ALAC. Someone should file it as a bug on ffmpeg's launchpad.

Oh well. In the meantime, the scripts here should work fine.

---

### Post by shantiq on 2012-03-04
sorry but not my experience here [IMG]http://img839.imageshack.us/img839/5577/smilie39.png[/IMG]

see from test today  ALL TAGS KEPT

[ATTACH]213694[/ATTACH]



ffmpeg version used is ```
ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1
```  ONEIRIC


YOU may be using an earlier version of program which did not as yet do this

---

### Post by rekh127 on 2012-04-02
Shantiq is correct 

ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1   keeps all the tags with the simple command of ffmpeg -i input.flac -acodec alac output.m4a

---

### Post by evilsoup on 2012-04-03
> **rekh127 said:**
> Shantiq is correct

Yes. At the time of writing I was using the FFmpeg from the 11.04 repositories, but the version from the PPA (and later versions) does indeed preserve tags by itself.

---

