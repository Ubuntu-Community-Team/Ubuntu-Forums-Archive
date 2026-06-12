---
title: "useful tips to batch convert more unusual audio formats"
date: 2010-10-30
forum: Multimedia Software
---

### Post by shantiq on 2010-10-30
for reasons which i do not fully understand i am fascinated by all the different **lossless** formats available


so here a small collection of batch conversions scripts which can be used in Ubuntu and all Linux systems

the prerequisite is to have ffmpeg installed and of course the codecs of the different formats   [mp3HD]("http://www.all4mp3.com/Download.aspx?eula=mp3hd_eula.html&file=mp3HD_Toolkit_for_Linux_2010-02-02.zip&name=Linux%20mp3HD%20Toolkit%20for%20v1.5")  [OptimFROG]("http://www.losslessaudio.org/")[ ape]("http://ubuntuforums.org/showpost.php?p=9562445&postcount=3") [mp4als]("http://www.nue.tu-berlin.de/menue/forschung/projekte/beendete_projekte/mpeg-4_audio_lossless_coding_als/parameter/en/#253204")  shorten bonk are attached


Here are "from and to" conversions scripts for shorten alac mp3hd mp4als flac ape ofr bonk 




i hope this is of use to others too   or maybe i am just mad :KS:KS



feel free to add more to this little bank



[COLOR="DarkRed"]ALL YOU NEED to do is cd to a folder of files and enter the line of code[/COLOR]   as in for example the first one go to a folder of wav files which will be turned into shn files   THE LATEST VERSION of qmmp plays shorten now as does [deadbeef]("http://ubuntuforums.org/showpost.php?p=9731471&postcount=21")and xmms



[U]wav to shorten
[/U]


```
for f in *.wav; do shorten "$f" "${f%.wav}.shn"; done

```


if you want to delete the original file   add ```
&& rm "$f"
```


so wav to shorten becomes

```
for f in *.wav; do shorten "$f" "${f%.wav}.shn" && rm "$f"  ; done

```




[U]shorten to wav
[/U]
```
for f in *.shn; do ffmpeg -i "$f" "${f%.shn}.wav"; done

```

[U]wav to mp3HD
[/U]
```
for f in *.wav; do mp3hdEncoder -br 320000   -if "$f" -of "${f%.wav}.mp3"; done

```


**When using mp3hdEncoder or mp3hdEncoder.exe under wine make sure you have accepted the terms and conditions first   IT WILL SIMPLY not work otherwise**For mp3hdEncoder enter mp3hdEncoder in the command line and follow instructions  for .exe right click and do same


[U]mp3HD to wav
[/U]
```
for f in *.mp3; do mp3hdDecoder   -if "$f" -of "${f%.mp3}.wav"; done

```

[U]wav to alac    apple lossless
[/U]
```
for f in *.wav; do ffmpeg -i  "$f" -acodec alac "${f%.wav}.m4a"; done

```

[U]alac to wav
[/U]

```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.wav"; done

```

[U]alac to flac
[/U]
```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.flac"; done

```


[U]flac to alac
[/U]
```
for f in *.flac; do ffmpeg -i "$f" -acodec alac "${f%.flac}.m4a"; done

```


[U]wav to mp4als
[/U]
```
for f in *.wav; do mp4alsRM22rev2  "$f"  "${f%.wav}.mp4"; done

```

and to decompress 

```
   for f in *.mp4; do mp4alsRM22rev2 -x -v "$f"  "${f%.mp4}.wav"; done

```



[U]wav to bonk
[/U]
```
for f in *.wav; do bonk encode -l "$f"  "${f%.wav}.bonk"; done

```


[U]wav to ofr  OptimFROG
[/U]
```
for f in *.wav; do ofr --encode  "$f"  "${f%.wav}.ofr"; done

```

[U]wav to ape
[/U]

```
for f in *.wav; do mac "$f" "${f%.wav}.ape" -c5000 ; done
```

[U]ape to flac
[/U]
```
for f in *.ape; do ffmpeg -i "$f" "${f%.ape}.flac"; done

```

[U]ape to alac
[/U]
```
for f in *.ape; do ffmpeg -i "$f" -acodec alac "${f%.ape}.m4a"; done

```

[U]ape to shorten
[/U]

```
for f in *.ape; do mac  "$f" "${f%.ape}.wav" -d ; done && for f in *.wav; do shorten "$f" "${f%.wav}.shn" && rm "$f"  ; done && rm *.ape
```


[U]shorten to alac
[/U]
```
for f in *.shn; do ffmpeg -i "$f" -acodec alac "${f%.shorten}.m4a"; done
```




[U]wavpack to flac
[/U]
```
for f in *.wv; do ffmpeg -i "$f"  "${f%.wv}.flac"; done
```


_**To mp3 320kbps (lossy)** _(here from flac but simply replace word flac by name of codec you start from)


```
for f in *.flac; do ffmpeg -i "$f" -ab 320k "${f%.flac}.mp3"; done
```




**ALSO** if you want to rip a disc to any of those formats You may want to use [Rubyripper]("http://ubuntuforums.org/showpost.php?p=9630448&postcount=26") since it allows for external encoding

---

### Post by shantiq on 2010-10-31
for some of the more usual formats


shntool is also very handy

```
format    ext     input    output  description
 ------    ---     -----    ------  -----------
    wav   .wav   shntool   shntool  RIFF WAVE file format
   aiff  .aiff       sox       sox  Audio Interchange File Format
    shn   .shn   shorten   shorten  Shorten low complexity waveform coder
   flac  .flac      flac      flac  Free Lossless Audio Codec
    ape   .ape       mac       mac  Monkey's Audio Compressor
    ofr   .ofr       ofr       ofr  OptimFROG Lossless WAVE Audio Coder
   lpac      -      lpac         -  Lossless Predictive Audio Compression
     wv    .wv  wvunpack   wavpack  WavPack Hybrid Lossless Audio Compression
   alac      -      alac         -  Apple Lossless Audio Codec
     la      -        la         -  Lossless Audio Compresser
    tta   .tta    ttaenc    ttaenc  TTA Lossless Audio Codec
    als   .als    mp4als    mp4als  MPEG-4 Audio Lossless Coding
    tak   .tak      takc      takc  (T)om's lossless (A)udio (K)ompressor
   bonk  .bonk      bonk      bonk  Bonk lossy/lossless audio compressor
    kxs      -     kexis         -  Kexis lossless WAV file compressor
    mkw   .mkw    mkwcon    mkwcon  MKW Audio Compression format
   cust      -         -   shntool  Custom output format module
   term      -         -   shntool  Sends output to the terminal
   null      -         -   shntool  Sends output to /dev/null


```
for batch convert use this

```
shnconv -o shn * flac
```    would convert all your files in a folder from flac to shn  -o is for output      change formats to your needs  (in my experience they do not all work but the main ones do)

---

### Post by shantiq on 2010-12-12
ok and if you wanted to batch convert to [**Tak**]("http://thbeck.de/Tak/Tak.html")

[**more    info**]("http://wiki.hydrogenaudio.org/index.php?title=TAK")





you can do that too by **placing Takc.exe (attached) in the folder where the wav files are** and making it executable


then enter (omit red code if you want to keep wavs)

```
for f in *.wav; do wine takc -e -p4  "$f" "${f%.wav}.tak" [COLOR="Red"]&& rm "$f"[/COLOR];  done
```

[U]**And** to convert to tak from flac (and remove flacs)
[/U]

```
flac -d *.flac && rm *.flac && for f in *.wav; do wine takc -e -p4  "$f" "${f%.wav}.tak" [COLOR="Red"]&& rm "$f"[/COLOR];  done
```


will play in foobar or winamp under wine

---

### Post by shantiq on 2010-12-29
**also useful if you download tracks in 24-bit and 32-bit** in sample rate of say 96000Hz and want to be able to turn into burnable wavs


you can use sox in this way



from flac

```
for f in *.flac; do sox  "$f" -b 16 -r 44100  "${f%.flac}.wav"; done
```


from wavpack

```
for f in *.wv; do sox  "$f"  -b 16 -r 44100 "${f%.wv}.wav"; done

```


all info on this page attached as a Pdf

---

### Post by omatoots on 2011-02-11
Perfect. Just what I needed. Thank you for posting.

---

### Post by l-x-l on 2011-02-11
Outstanding post. Thanks.

---

### Post by Repabil on 2011-03-01
Agreed, great post!

Another options for many formats is to use the GNOME application [SoundConverter](apt://soundconverter).

---

### Post by shantiq on 2011-03-05
> **Repabil said:**
> Agreed, great post!

Another options for many formats is to use the GNOME application [SoundConverter](apt://soundconverter).



yes repabil soundconverter best of the GUI converters but one might love to see see those numbers spin:KS:KS:KS when at the command-line


[B]
one more conversion is from flac to aac/m4a[/B]   but keeping the tags     this one was givem me by mc4man



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

flac -c -d "$f" - | neroAacEnc -if -  -cbr 320000 -of  "$OUTF"
neroAacTag "$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" -meta:album="$ALBUM" -meta:genre="$GENRE" -meta:year="$DATE" -meta:track="$TRACKNUMBER" -meta:totaltracks="$TRACKTOTAL"
done
mkdir "$ALBUM" && mv *.m4a "$ALBUM"
```


[B]
ps :   you can bump up[/B] kbps to 516 with  neroAacEnc   change 320000 to 516000

---

### Post by shantiq on 2011-03-14
there is yet another codec which can be obtained through ffmpeg
it is used as the sound file in high quality DOLBY videos


**[ac3]("http://www.digitalpreservation.gov/formats/fdd/fdd000209.shtml")** is lossy but goes up to 640kbps giving you a small file with high kbps




maybe try it on some flac files or wav


```
for f in *.flac; do ffmpeg -i "$f" -ab 640k "${f%.flac}.ac3"; done
```


```
for f in *.wav; do ffmpeg -i "$f" -ab 640k "${f%.flac}.ac3"; done
```

it has to be certain settings for kbps   which are

640,576,512,448,384,320,256,224,192,160,128,112,96,80,64,56,48,32



ac3 plays in all recent players

---

### Post by shantiq on 2011-06-04
and if the command line is not really your thing


soundKonverter   in your synaptic    or   ```
sudo apt-get install soundkonverter
```


now will convert any lossless format to any other provided you have them installed


see image/   set output to source directory to know where to find your files / set quality to lossless


[CENTER][IMG]http://img8.imageshack.us/img8/1993/finishedsoundkonverter0.png[/IMG][/CENTER]

---

### Post by Conf.linux on 2012-10-02
Additional commands:

To convert to Lame V0 MP3 preset:

```
for f in *.flac; do ffmpeg -i "$f" -aq 0 "${f%.flac}.mp3"; done
```

To convert to Lame V2 MP3 preset:

```
for f in *.flac; do ffmpeg -i "$f" -aq 2 "${f%.flac}.mp3"; done
```

---

### Post by overdrank on 2012-10-02
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

