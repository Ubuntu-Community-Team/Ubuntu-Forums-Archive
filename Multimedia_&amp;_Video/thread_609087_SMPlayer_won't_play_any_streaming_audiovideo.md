---
title: "SMPlayer won't play any streaming audio/video"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by tghe-retford on 2007-11-10
I've been having quite a few problems with a number of media player apps. Tonight, I tried SMPlayer 0.5.61 in Kubuntu 7.10 x86_64 and it won't play any streaming file, even though KMPlayer (still won't play AAC files!) and MPlayer will. This is a log of me trying to play [http://smoothjazz.com/streams/smoothjazz_128.pls](http://smoothjazz.com/streams/smoothjazz_128.pls) (which is a Shoutcast playlist for Smoothjazz.com)

```
/usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -zoom -nokeepaspect -nodouble -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 41943054 -colorkey 131586 -monitoraspect 1.25 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -osdlevel 0 -vf-add expand=osd=1 -noslices -vf-add screenshot -channels 6 -playlist http://smoothjazz.com/streams/smoothjazz_128.pls

MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving smoothjazz.com for AF_INET...
Connecting to server smoothjazz.com[38.99.110.66]: 80...
Cache size set to 8192 KBytes
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing [playlist]
numberofentries=17
File1=http://scfire-chi-aa04.stream.aol.com:80/stream/1005
Title1=(#1 - 81/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length1=-1
File2=http://scfire-ntc-aa01.stream.aol.com:80/stream/1005
Title2=(#2 - 83/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length2=-1
File3=http://scfire-dll-aa04.stream.aol.com:80/stream/1005
Title3=(#3 - 84/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length3=-1
File4=http://scfire-nyk-aa02.stream.aol.com:80/stream/1005
Title4=(#4 - 84/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length4=-1
File5=http://scfire-chi-aa01.stream.aol.com:80/stream/1005
Title5=(#5 - 85/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length5=-1
File6=http://scfire-ntc-aa04.stream.aol.com:80/stream/1005
Title6=(#6 - 85/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length6=-1
File7=http://scfire-chi-aa02.stream.aol.com:80/stream/1005
Title7=(#7 - 88/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length7=-1
File8=http://scfire-dll-aa01.stream.aol.com:80/stream/1005
Title8=(#8 - 91/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length8=-1
File9=http://scfire-nyk-aa04.stream.aol.com:80/stream/1005
Title9=(#9 - 91/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length9=-1
File10=http://scfire-nyk-aa03.stream.aol.com:80/stream/1005
Title10=(#10 - 92/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length10=-1
File11=http://scfire-dll-aa03.stream.aol.com:80/stream/1005
Title11=(#11 - 94/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length11=-1
File12=http://scfire-ntc-aa03.stream.aol.com:80/stream/1005
Title12=(#12 - 94/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length12=-1
File13=http://scfire-dll-aa02.stream.aol.com:80/stream/1005
Title13=(#13 - 99/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length13=-1
File14=http://scfire-chi-aa03.stream.aol.com:80/stream/1005
Title14=(#14 - 104/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length14=-1
File15=http://scfire-nyk-aa01.stream.aol.com:80/stream/1005
Title15=(#15 - 106/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length15=-1
File16=http://scfire-ntc-aa02.stream.aol.com:80/stream/1005
Title16=(#16 - 116/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length16=-1
File17=http://207.200.96.226:8052
Title17=(#17 - 100/100) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length17=-1
Version=2.
File not found: 'scfire-chi-aa04.stream.aol.com:80/stream/1005
Title1=(#1 - 81/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length1=-1
File2=http://scfire-ntc-aa01.stream.aol.com:80/stream/1005
Title2=(#2 - 83/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length2=-1
File3=http://scfire-dll-aa04.stream.aol.com:80/stream/1005
Title3=(#3 - 84/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length3=-1
File4=http://scfire-nyk-aa02.stream.aol.com:80/stream/1005
Title4=(#4 - 84/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length4=-1
File5=http://scfire-chi-aa01.stream.aol.com:80/stream/1005
Title5=(#5 - 85/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length5=-1
File6=http://scfire-ntc-aa04.stream.aol.com:80/stream/1005
Title6=(#6 - 85/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length6=-1
File7=http://scfire-chi-aa02.stream.aol.com:80/stream/1005
Title7=(#7 - 88/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length7=-1
File8=http://scfire-dll-aa01.stream.aol.com:80/stream/1005
Title8=(#8 - 91/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length8=-1
File9=http://scfire-nyk-aa04.stream.aol.com:80/stream/1005
Title9=(#9 - 91/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length9=-1
File10=http://scfire-nyk-aa03.stream.aol.com:80/stream/1005
Title10=(#10 - 92/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length10=-1
File11=http://scfire-dll-aa03.stream.aol.com:80/stream/1005
Title11=(#11 - 94/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length11=-1
File12=http://scfire-ntc-aa03.stream.aol.com:80/stream/1005
Title12=(#12 - 94/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length12=-1
File13=http://scfire-dll-aa02.stream.aol.com:80/stream/1005
Title13=(#13 - 99/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length13=-1
File14=http://scfire-chi-aa03.stream.aol.com:80/stream/1005
Title14=(#14 - 104/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length14=-1
File15=http://scfire-nyk-aa01.stream.aol.com:80/stream/1005
Title15=(#15 - 106/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length15=-1
File16=http://scfire-ntc-aa02.stream.aol.com:80/stream/1005
Title16=(#16 - 116/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length16=-1
File17=http://207.200.96.226:8052
Title17=(#17 - 100/100) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length17=-1
Version=2'
Failed to open [playlist]
numberofentries=17
File1=http://scfire-chi-aa04.stream.aol.com:80/stream/1005
Title1=(#1 - 81/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length1=-1
File2=http://scfire-ntc-aa01.stream.aol.com:80/stream/1005
Title2=(#2 - 83/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length2=-1
File3=http://scfire-dll-aa04.stream.aol.com:80/stream/1005
Title3=(#3 - 84/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length3=-1
File4=http://scfire-nyk-aa02.stream.aol.com:80/stream/1005
Title4=(#4 - 84/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length4=-1
File5=http://scfire-chi-aa01.stream.aol.com:80/stream/1005
Title5=(#5 - 85/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length5=-1
File6=http://scfire-ntc-aa04.stream.aol.com:80/stream/1005
Title6=(#6 - 85/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length6=-1
File7=http://scfire-chi-aa02.stream.aol.com:80/stream/1005
Title7=(#7 - 88/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length7=-1
File8=http://scfire-dll-aa01.stream.aol.com:80/stream/1005
Title8=(#8 - 91/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length8=-1
File9=http://scfire-nyk-aa04.stream.aol.com:80/stream/1005
Title9=(#9 - 91/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length9=-1
File10=http://scfire-nyk-aa03.stream.aol.com:80/stream/1005
Title10=(#10 - 92/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length10=-1
File11=http://scfire-dll-aa03.stream.aol.com:80/stream/1005
Title11=(#11 - 94/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length11=-1
File12=http://scfire-ntc-aa03.stream.aol.com:80/stream/1005
Title12=(#12 - 94/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length12=-1
File13=http://scfire-dll-aa02.stream.aol.com:80/stream/1005
Title13=(#13 - 99/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length13=-1
File14=http://scfire-chi-aa03.stream.aol.com:80/stream/1005
Title14=(#14 - 104/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length14=-1
File15=http://scfire-nyk-aa01.stream.aol.com:80/stream/1005
Title15=(#15 - 106/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length15=-1
File16=http://scfire-ntc-aa02.stream.aol.com:80/stream/1005
Title16=(#16 - 116/500) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length16=-1
File17=http://207.200.96.226:8052
Title17=(#17 - 100/100) SmoothJazz.com - The Global Home for the Smoothest Jazz - Live from Monterey Bay
Length17=-1
Version=2.


Exiting... (End of file)

```

Local media plays fine but streaming media does not. I don't want to be switching between a number of media players to play different kinds of media files. Is there anything I could do to get SMPlayer to work with streams, like KMPlayer (except for AAC) and MPlayer does?

Thanks in advance.

---

### Post by rvm4000 on 2007-11-10
Does mplayer play that stream? It doesn't play for me.

It seems the playlist doesn't have proper line breaks and mplayer can't parse it.

---

### Post by tghe-retford on 2007-11-10
> **rvm4000 said:**
> Does mplayer play that stream? It doesn't play for me.

It seems the playlist doesn't have proper line breaks and mplayer can't parse it.
It wouldn't play in MPlayer for me either:
```
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://smoothjazz.com/streams/smoothjazz_128.pls.
Resolving smoothjazz.com for AF_INET...
Connecting to server smoothjazz.com[38.99.110.66]: 80...
Cache size set to 8192 KBytes


Exiting... (End of file)

```

But does in KMPlayer (its playing the first entry in the playlist):

```
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Resolving scfire-chi-aa04.stream.aol.com for AF_INET...
Connecting to server scfire-chi-aa04.stream.aol.com[149.174.133.204]: 80...
Name   : SMOOTHJAZZ.COM - The Internet's Original Smooth Jazz Radio Station - Live from the Monterey Bay
Genre  : Smooth Jazz
Website: http://www.smoothjazz.com
Public : yes
Bitrate: 128kbit/s
Cache size set to 8096 KBytes
Cache fill:  0.00% (0 bytes)   
Cache fill:  3.95% (327680 bytes)   
ID_AUDIO_ID=0
Audio file file format detected.
ID_FILENAME=http://scfire-chi-aa04.stream.aol.com:80/stream/1005
ID_DEMUXER=audio
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=0
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mad
Video: no video
Starting playback...
```

Adding individual URL's from the stream does work in SMPlayer, but it seems strange as to how it does work in KMPlayer and not in SMPlayer (even selecting the It's a Playlist option in the URL dialog).

The BBC News 24 stream also has a habit of not working either in SMPlayer/MPlayer but does in KMPlayer...

Very odd... it must be how the frontends interact with MPlayer.

I'd stick with KMPlayer for everything but it wouldn't play an AAC stream I wanted for another jazz station that MPlayer could play. (see thread: [http://ubuntuforums.org/showthread.php?t=602969](http://ubuntuforums.org/showthread.php?t=602969))

---

### Post by rvm4000 on 2007-11-11
Maybe kmplayer downloads and parses the pls file on its own.

---

### Post by rvm4000 on 2007-11-15
Here is a work-around that will let you play those pls files in mplayer or smplayer.
Create a bash script (for instance named "play_broken_pls_stream.sh") with this content:

```

#!/bin/sh
wget $1 -O /tmp/temp.pls
sed -e "s/\r/\r\n/g" /tmp/temp.pls > /tmp/temp2.pls
mplayer -playlist /tmp/temp2.pls

```

It downloads the pls file and saves in a temporary file,  then fixes the line breaks, and finally plays it with mplayer (you can replace it with smplayer).

```

./play_broken_pls_stream.sh http://smoothjazz.com/streams/smoothjazz_128.pls  

```

I'm not good with bash scripts, so this could probably be written much better...

---

