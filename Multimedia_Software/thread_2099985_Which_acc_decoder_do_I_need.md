---
title: "Which acc decoder do I need?"
date: 2012-12-31
forum: Multimedia Software
---

### Post by Azyx on 2012-12-31
Have an playst to Svedish streaming radio

```
#EXTM3U 
 
#EXTINF:-1,Sveriges Radio 
http://http-live.sr.se/p1-aac-96
```

It work with VLC, but for Gstreamer there are no decoder that work. I work with Gstreamer and Clementine on my 10.04, but I don't know which decoder I need.

Is there a way to see what kind of decoder I need either on my working player or via VLC or by checking the stream or something?

/Cheers

---

### Post by shantiq on 2012-12-31
> mediainfo p1-aac-96
General
Complete name                            : p1-aac-96
Format                                   : ADTS
Format/Info                              : Audio Data Transport Stream
File size                                : 4.76 MiB

Audio
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format version                           : Version 2
Format profile                           : HE-AAC / LC
Bit rate mode                            : Constant / Variable
Bit rate                                 : 94.2 Kbps
Minimum bit rate                         : 158 Kbps
Maximum bit rate                         : 249 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz / 24.0 KHz
Compression mode                         : Lossy
Stream size                              : 4.76 MiB (100%)


so HE-AAC ADTS is the audio file




see below for solution

---

### Post by shantiq on 2012-12-31
[URL="http://www.listenlive.eu/sweden.html"][B]Swedish radio
[/B][/URL]


right-click on 96k  [there is 192k too if you want better def]  and save pls file    now try in clementine and mplayer    should be fine:KS
or try the mp3 version[winamp logo] right at the top in the same way

============


if still a problem  open in text editor and extract the address
here is the address copy **without word mplayer** and open location in Mplayer gui or clementine

```
mplayer http://http-live.sr.se/p1-aac-96
```  or

```
mplayer http://http-live.sr.se/p1-aac-192
```


you had the right decoder the address just got messed up to something that cannot be read by all players

=================


you could simply copy third line in your original Code box in your post and add location to Mplayer Clementine / as you see same address

---

### Post by Azyx on 2013-01-06
> **shantiq said:**
> [URL="http://www.listenlive.eu/sweden.html"][B]Swedish radio
[/B][/URL]


right-click on 96k  [there is 192k too if you want better def]  and save pls file    now try in clementine and mplayer    should be fine:KS
or try the mp3 version[winamp logo] right at the top in the same way

============


if still a problem  open in text editor and extract the address
here is the address copy **without word mplayer** and open location in Mplayer gui or clementine

```
mplayer http://http-live.sr.se/p1-aac-96
```  or

```
mplayer http://http-live.sr.se/p1-aac-192
```
you had the right decoder the address just got messed up to something that cannot be read by all players

=================


you could simply copy third line in your original Code box in your post and add location to Mplayer Clementine / as you see same address

I'm not interested i either mplayer or xmms, it is a ploblem with gstreamer on my newly installed 12.04 Ubuntu. With my 'old' 12.04 or 10.04 there are no problem to play the m3u-lists. But as you says, the problem are maybe not codecs, but something else i gstreamer?

---

### Post by Azyx on 2013-01-06
If I add strem 
[http://http-live.sr.se/p1-aac-96](http://http-live.sr.se/p1-aac-96) in Clementine I get the message:

'Could not decode stream'
'Could not decode stream'
'Could not decode stream'
.....

Until I stop the player...

It now also affect my 'old' 12.04 Ubuntu, so it seems to be a problem according to an update? 

I have saved the radio streams m3u-file to not have to go out to internet and search after radio-channel everytime I get a new computer (Have used the m3u-files many years), just get the saved m3u-files on my local file-server. And I still work with VLC and on my 10.04LST machines Clementine and the default media player (Totem and Rhytmbox?) who user Gstreamer as media-engine.

---

### Post by Azyx on 2013-01-06
When i open Clementine in a terminal I get this message when I try to open the radio-stream:

```
12:42:58.881 DEBUG GnomeGlobalShortcutBackend:93    registered 
12:43:49.749 ERROR GstEnginePipeline:506            1 "gstffmpegdec.c(2215): gst_ffmpegdec_audio_frame (): /GstPipeline:pipeline/GstURIDecodeBin:uridecodebin-0/GstDecodeBin2:decodebin20/ffdec_aac:ffdec_aac0:
Decoding of AAC stream by FFMPEG failed." 
12:43:49.749 WARN  GstEngine:585                    Gstreamer error: "Could not decode stream." 
12:43:50.508 ERROR GstEnginePipeline:506            2 "gstffmpegdec.c(2215): gst_ffmpegdec_audio_frame (): /GstPipeline:pipeline/GstURIDecodeBin:uridecodebin-14/GstDecodeBin2:decodebin21/ffdec_aac:ffdec_aac1:
Decoding of AAC stream by FFMPEG failed." 
12:43:50.508 WARN  GstEngine:585                    Gstreamer error: "Could not decode stream." 
12:43:51.120 ERROR GstEnginePipeline:506            3 "gstffmpegdec.c(2215): gst_ffmpegdec_audio_frame (): /GstPipeline:pipeline/GstURIDecodeBin:uridecodebin-28/GstDecodeBin2:decodebin22/ffdec_aac:ffdec_aac2:
..............
```Until I stop the player

/Cheers

---

### Post by shantiq on 2013-01-07
Azyx   i do not understand what you wrote

read again carefully what i said about how to use the address; you are still doing what you did before clearly

copy and paste to location in clementine this address MINUS the word mplayer
[i have to write it LIKE THIS or it messes the link in this forum   TRUST ME ON THAT!]

1.   COPY  all of this line **minus **the word mplayer
```
mplayer http://http-live.sr.se/p1-aac-192
```

2.   OPEN CLEMENTINE  / PLAYLIST/add stream/paste the address above [without the word mplayer]





PEACE!   Shan

---

### Post by Azyx on 2013-01-07
> **shantiq said:**
> Azyx   i do not understand what you wrote

read again carefully what i said about how to use the address; you are still doing what you did before clearly

copy and paste to location in clementine this address MINUS the word mplayer
[i have to write it LIKE THIS or it messes the link in this forum   TRUST ME ON THAT!]

1.   COPY  all of this line **minus **the word mplayer
```
mplayer http://http-live.sr.se/p1-aac-192
```2.   OPEN CLEMENTINE  / PLAYLIST/add stream/paste the address above [without the word mplayer]

PEACE!   Shan

Offcourse I have done just that your described!  I doesen't matter if I add the m3u-file OR Playlist-->Add stream, the results are the same.

I have 2 shreen-shots as proof, but I don't know how or If I can upload theme here....

---

### Post by sudodus on 2013-01-07
> **shantiq said:**
> 
[i have to write it LIKE THIS or it messes the link in this forum   TRUST ME ON THAT!]

Try [noparse][noparse]...[/noparse][/noparse] :-)
```
[noparse]http://http-live.sr.se/p1-aac-192[/noparse]
```

---

### Post by Azyx on 2013-01-07
> **shantiq said:**
> Azyx   i do not understand what you wrote

PEACE!   Shan

I open clementine via terminal, to get error-message, when I add:

[http://http-live.sr.se/p1-aac-192](http://http-live.sr.se/p1-aac-192)
in the Playlist-->Add stream... popup-window. The error-message I show before appear inte the terminal.

Do you understand now?

/Cheers

---

### Post by shantiq on 2013-01-07
> **sudodus said:**
> Try [noparse][noparse]...[/noparse][/noparse] :-)
```
[noparse]http://http-live.sr.se/p1-aac-192[/noparse]
```


thanx for that...  never knew you could do this



so  Azyx   my last offer


1. open clementine 
2. go Playlist/Add stream and paste this [not the link you have used before/**that does not work**] just this link from this page please try it

> [noparse]http://http-live.sr.se/p1-aac-192[/noparse]


see if any good...

---

### Post by Azyx on 2013-01-07
> **shantiq said:**
> thanx for that...  never knew you could do this



so  Azyx   my last offer


1. open clementine 
2. go Playlist/Add stream and paste this [not the link you have used before/**that does not work**] just this link from this page please try it




see if any good...

No. same error with  	 	 		 			 				[http://http-live.sr.se/p1-aac-192](http://http-live.sr.se/p1-aac-192) as with 96..

```
Decoding of AAC stream by FFMPEG failed." 
15:22:10.376 WARN  GstEngine:585                    Gstreamer error: "Could not decode stream." 
15:22:10.787 ERROR GstEnginePipeline:506            21 "gstffmpegdec.c(2215): gst_ffmpegdec_audio_frame (): /GstPipeline:pipeline/GstURIDecodeBin:uridecodebin-280/GstDecodeBin2:decodebin220/ffdec_aac:ffdec_aac20:
Decoding of AAC stream by FFMPEG failed." 
15:22:10.789 WARN  GstEngine:585                    Gstreamer error: "Could not decode stream." 
15:22:11.377 ERROR GstEnginePipeline:506            22 "gstffmpegdec.c(2215): gst_ffmpegdec_audio_frame (): /GstPipeline:pipeline/GstURIDecodeBin:uridecodebin-294/GstDecodeBin2:decodebin221/ffdec_aac:ffdec_aac21:
Decoding of AAC stream by FFMPEG failed." 
15:22:11.382 ERROR GstEnginePipeline:506            22 "gstbasesrc.c(2625): gst_base_src_loop (): /GstPipeline:pipeline/GstURIDecodeBin:uridecodebin-294/GstSoupHTTPSrc:source:
streaming task paused, reason error (-5)" 

```

---

### Post by BicyclerBoy on 2013-01-07
Both those streams work okay here with Clementine..
1.) 10.04.3 LTS 64 bit clememtine 1.1 gstreamer-0.10-ffmpeg 0.10.11.1~ppa1~lucid1 universe.
2.) 12.04 LTS 32bit clementine 1.1.1 gstreamer-0.10-ffmpeg 0.10.13-4

Do you have multiverse & universe repositories enabled (in synaptic) ?
Have you installed "ubuntu-restricted-extras" ?

It's a bit silly using 192KHz sample rate for an internet talk show..

---

### Post by Azyx on 2013-01-07
> **BicyclerBoy said:**
> Both those streams work okay here with Clementine..
1.) 10.04.3 LTS 64 bit clememtine 1.1 gstreamer-0.10-ffmpeg 0.10.11.1~ppa1~lucid1 universe.
2.) 12.04 LTS 32bit clementine 1.1.1 gstreamer-0.10-ffmpeg 0.10.13-4

Do you have multiverse & universe repositories enabled (in synaptic) ?
Have you installed "ubuntu-restricted-extras" ?

It's a bit silly using 192KHz sample rate for an internet talk show..

Thanx. I did not have that, only ubuntu-restricted-addons, but it did not help :( Will test more tomorrow.

Yes 96kHz work fine for talk :) I also have slow adsl..

/Cheers

---

### Post by BicyclerBoy on 2013-01-07
You could try David Sansome's clementine ppa..

The gstreamer-ffmpeg dynamically loads other ffmpeg/libav system libraries.
(static build of it is 29MB.

So check you have the unstripped "extras" versions of the system avlibs..

---

### Post by shantiq on 2013-01-08
----------

---

### Post by BicyclerBoy on 2013-01-08
The errors that OP has are in gstreamer-ffmpeg..this is dynamically linked to system libav* libraries.
So it matters which versions they are.

It does not use ffmpeg directly & ffmpeg does not need to be installed.
And owing to the unfortunate choice by Ubuntu to use LibAV project over ffmpeg; the system libav*s are now derived from LibAV.

---

### Post by Azyx on 2013-01-09
I find the missing package :)
It was:

```
gstreamer0.10-plugins-bad  
```

:) Not the -good and the -ugly are enoght. I think, anyway it worked after installation of that :)

/Cheers and thank for all help

---

### Post by BicyclerBoy on 2013-01-10
Sorry. should have suggested good,bad & the ugly..
Not the same movie with just the two..

---

