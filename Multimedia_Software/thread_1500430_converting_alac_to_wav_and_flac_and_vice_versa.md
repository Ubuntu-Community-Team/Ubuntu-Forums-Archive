---
title: "converting alac to wav and flac and vice versa"
date: 2010-06-03
forum: Multimedia Software
---

### Post by shantiq on 2010-06-03
Got a few alac files off the net and looked around for converting solutions. Might be of use to some.



[B]_Players which handle alac_  

VLC plays them    
QMMP (right-click on player/settings/plugins/FFmpeg plugin/highlight/Preferences/Tick alac )
deadbeef    
aqualung[/B]
xine
audacious

Personally i love alac but if you need/want to convert them here goes...



to **[SIZE="3"]batch convert[/SIZE]** quickly to flac/wav

cd (change directory) to you alac files in your terminal then enter

```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.flac"; done

```


To decompress to wav use same as above just change word flac for wav

===============================================
and wav to alac 

```
for f in *.wav; do ffmpeg -i  "$f" -acodec alac "${f%.wav}.m4a"; done

```



**ALSO**   now ffmpeg handles **converting [to alac]("http://ubuntuforums.org/showpost.php?p=11737536&postcount=24") **




              ==========================================
              ==========================================




or for single file with FFMPEG
=============   ==============

wav to m4a  ==>


```
ffmpeg -i <input> -acodec alac <output>.m4a

```

and to convert from alac (m4a) to wav or flac 


```
ffmpeg  -i <input>.m4a  <output>.wav

```


```
ffmpeg  -i <input>.m4a  <output>.flac
```



there is also a way to do this with shntool   would anyone know how to?

---

### Post by shantiq on 2010-06-07
[B][COLOR="Blue"]

 alac files also play straight off in the player called xine which is in synaptic


also  [deadbeef]("http://deadbeef.sourceforge.net/download.html") plays alac
[/COLOR][/B]

---

### Post by cascade9 on 2010-06-07
Or, you can just forget the comandline stuff and use sounconverter. As long as you have the right gstreamer package installed (I cant remember if alac is under good, bad or ugly) soundconverter wil transcode them to whatever formaty you cwant. Also, and gstreamer media player should play them. List of teh gstreamer media players here- 

[http://www.gstreamer.net/apps/](http://www.gstreamer.net/apps/)

---

### Post by shantiq on 2010-06-07
> As long as you have the right gstreamer package installed (I cant remember if alac is under good, bad or ugly)


[B][COLOR="Blue"]hi there cascade not been able to get that going so far soundkonverter does not pick up the info from alac-decoder
probably not the one it picks it up from    truth is i do not see one can install alac onto ubuntu   


```
sudo apt-get install alac
``` goes nowhere


not sure what one has to do to get it going it would be handy since soundkonverter is so good   got shorten and tta going there but not as yet alac



oh sorry you said soundconverter not soundKonverter    well that one has AAC m4a  but i do not think that is lossless alac[/COLOR][/B]

---

### Post by cascade9 on 2010-06-07
Soundconverter does do alac- 

> SoundConverter is the leading sound conversion application for the GNOME Desktop. 	It reads anything the GStreamer library can read  	(Ogg Vorbis, AAC, MP3, FLAC, WAV, AVI, MPEG, MOV, M4A, AC3, DTS,** ALAC**, MPC, Shorten, APE, SID, MOD, XM, S3M, etc...),  	and writes WAV, FLAC, MP3, AAC, and Ogg Vorbis files. 	

[http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

Checked, it appears that alac support is in gstreamer-bad- 

> qtmux: add support for ALAC, SVQ3, IMA ADPCM; improve j2k handling

[http://gstreamer.freedesktop.org/releases/gst-plugins-bad/0.10.18.html](http://gstreamer.freedesktop.org/releases/gst-plugins-bad/0.10.18.html)

I *think* that all you would need to do to get gstreamer-bad witrh ubuntu is -

sudo apt-get install gstreamer0.10-plugins-bad

[http://packages.ubuntu.com/lucid/gstreamer0.10-plugins-bad](http://packages.ubuntu.com/lucid/gstreamer0.10-plugins-bad)

"sudo apt-get install alac" wont work because there is no "alac" package. Close though, there is "alac-decoder". 

[http://packages.ubuntu.com/lucid/alac-decoder](http://packages.ubuntu.com/lucid/alac-decoder)

---

### Post by shantiq on 2010-06-07
[B][COLOR="Blue"]well i did

```
sudo apt-get install gstreamer0.10-plugins-bad

```


and it says i am already up to date

and when i go to soundconverter no alac just AAC m4a up to 320kbps


BUT it will convert from alac to anything else    maybe that is what you meant  from alac to   but not the other way


no shorten either although it is picked up by soundKonverter


have i missed something?[/COLOR][/B]

---

### Post by cascade9 on 2010-06-07
Yes, I meant convert from ALAC to other formats. 

As far as shorten goes, it should be possible to transcode from one format into .shn. But I dont know any way to do it offhand, .shn is old and totally outclassed by newer lossless codecs so developers wouldnt be btoerhed adding .shn encoding support.

Yes, I did read on your other thread that you think shn is the best sounding lossless fomat, but I disagree, apart from lame 'maybe' lossless (like wma-lossless) and decoder issues, they should all sound the same ......

---

### Post by shantiq on 2010-06-07
> Yes, I did read on your other thread that you think shn is the best sounding lossless format, but I disagree, apart from lame 'maybe' lossless (like wma-lossless) and decoder issues, they should all sound the same ......[B][COLOR="Indigo"]i know they should but they really do not in my experience i once read a long article on shorten which explained how it had been designed for speech for conferences at cambridge university   hey here [i found it ]("ftp://svr-ftp.eng.cam.ac.uk/pub/reports/robinson_tr156.ps.Z") 

and it always has sounded clearer to me on windows or ubuntu   maybe i am mad but i think not   give a a whirl mayhaps?soundkonverter will happily oblige once you have installed it   

xmms is the only player i know which handles it on linux  also audacious does now   the best of all player to my mind   the KISS principle i read somewhere (keep it simple stupid)  i love solid systems


anyway[/COLOR][/B]

---

### Post by shantiq on 2010-07-20
and if you want to rip a disc to alac using rubyripper [here is howto]("http://ubuntuforums.org/showthread.php?t=1533534&page=2")   scroll to bottom of page


external encoding is    ```
ffmpeg -i %i -acodec alac  "%o".m4a
```

---

### Post by shantiq on 2010-08-02
also there is a program designed by david hammerton called alac-decoder which is really efficient but only works one way

still worth using

install


```
sudo apt-get install alac-decoder

```

```
alac-decoder -h
Usage: alac [options] [--] file
Decompresses the ALAC file specified

Options:
  -f output.wav     outputs the decompressed data to the
                    specified file, in WAV format. Default
                    is stdout.
  -r                write output as raw PCM data. Default
                    is in WAV format.
  -v                verbose output.
  -t                test that file is ALAC, also tests for
                    other m4a file types.

This software is Copyright (c) 2005 David Hammerton
All rights reserved
http://crazney.net/

```

if you file is named 24

```
alac-decoder -f 24.wav 24.m4a
```

---

### Post by shantiq on 2010-10-01
also just found out you can record your voice with a microphone directly to alac   using ffmpeg



```
ffmpeg -f alsa -ac 2 -i pulse -acodec alac  -y ./Desktop/RecordingMYvoice.m4a
```

---

### Post by jamesisin on 2010-10-05
You might be interested in this conversion script I recently finished:

[http://www.soundunreason.com/InkWell/?p=2485](http://www.soundunreason.com/InkWell/?p=2485)

---

### Post by shantiq on 2010-10-17
looking around finally [found a way]("http://ubuntuforums.org/showpost.php?p=5441422&postcount=3") to batch decompress a whole lot of alac to wave


 having saved the script 

```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.wav"; done

```



as m4a2wav-ffmpeg.sh in your home folder and made it executable  rightclick/properties/permissions/make executable


OR   ```
sudo chmod +x
```


go into your m4a file folder then enter  ```
 ~/./m4a2wav-ffmpeg.sh
```



brilliant   thank you guys


ps of course this works with all formats supported by ffmpeg simply substitute m4a for other format extension and do the same process

==============================================================================================


and to **batch convert from wav to alac **use this script instead and the same process


```
for f in *.wav; do ffmpeg -i  "$f" -acodec alac "${f%.wav}.m4a"; done
```



save as wav2m4a-ffmpeg.sh



then cd to you music files and do


```
~/./wav2m4a-ffmpeg.sh
```

---

### Post by shantiq on 2010-10-17
actually thinking about it a more likely scenario for a linux user encountering a bunch of **alac files would be to turn them into flacs**



so here


```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.flac"; done
```


save as   m4a2flac-ffmpeg.sh


make executable   as mentioned earlier


cd to your folder of alac files and run



```
~/./m4a2flac-ffmpeg.sh

```


**all conversion scripts zipped below**

---

### Post by jamesisin on 2010-10-20
Just a little heads-up to anyone who may be new to this kind of conversion: when you convert ALAC files into WAVE files **you will lose all of your tagging data**.  WAVE files have no mechanism for storing tag data in the way that other audio formats do.  (FLAC of course retains tag data.)

---

### Post by shantiq on 2010-10-20
fair point james


and i really wonder why that is?


does anyone know?    is there a built-in problem with wave or was it a choice that was made when it was designed?

---

### Post by jamesisin on 2010-10-21
Wave was designed long before id3 tagging existed.  There is some room in the header for a small amount of information (like artist and title) but it's really not a very good format for doing so.  Now that we have formats like FLAC which use id3 tagging there really seems no point in altering waves:

[http://en.wikipedia.org/wiki/WAV](http://en.wikipedia.org/wiki/WAV)

But, really, use FLAC.

---

### Post by atca on 2011-11-05
To add to this in case any one else is interested 
I've pulled together a script which converts a CD to FLAC and ALAC transcribing the meta data between FLAC and ALAC since they ue slightly different formats. Takes the whole process from rip to FLAC/ALAC rip with 2 clicks and in under 15 minutes, it can also be used to batch CD rips.

See [here]("http://confoundedtech.blogspot.com/2011/11/ubuntu-automatically-rip-cd-to-flac-and.html")

---

