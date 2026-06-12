---
title: "What is the format of the stream??"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by lambono on 2008-02-26
Hi All,
I have a script which dumps a stream output....

```
mplayer -dumpstream -playlist $STREAMADDRESS -dumpfile "$USERDIR$SHOWNAME".dump -vc dummy -vo null &

```

The stream is then converted to .mp3 format 

```

mkfifo $USERDIR$RECORDINGNAME.pipe

lame -h -v -b 64 --tt $SHOWNAME --tl "${STATIONNAME}" --ty "2008" "$USERDIR$RECORDINGNAME.pipe" "$USERDIR$RECORDINGNAME".mp3 & mplayer -vc dummy -vo null -ao pcm:file="$USERDIR$RECORDINGNAME.pipe" "$USERDIR$RECORDINGNAME".dump


```

However this 2nd step might not be necessary for some streams as they are already in MP3 format. How can I test for this before I start trying to convert it?

Thanks for your help!

---

### Post by andrew.46 on 2008-02-26
Hi,

 Can you pull the information from :

```
$ mplayer -identify
```

and use a conditional statement?

          Andrew

Edit: I am stupid!!! Of course this will not work on a *stream*.

---

### Post by ron999 on 2008-02-26
Hi
If you play the stream with mplayer from the command line it gives information about the stream.
In the example below it shows that it's 48Kbps AAC file format detected.
Here:-
```
Playing http://sc1.abacast.com:8105/.
Resolving sc1.abacast.com for AF_INET6...
Couldn't resolve name for AF_INET6: sc1.abacast.com
Resolving sc1.abacast.com for AF_INET...
Connecting to server sc1.abacast.com[216.218.147.60]: 8105...
Name   : Radio Caroline
Genre  : Various
Website: http://www.radiocaroline.co.uk
Public : no
Bitrate: 48kbit/s
Cache size set to 128 KBytes
Cache fill:  6.25% (8192 bytes)   
ICY Info: StreamTitle='Radio Caroline rocking around the world... www.radiocaroline.co.uk ...powered by Abacast courtesy of freeclix.com (12:01 GMT)';StreamUrl='';
Cache fill: 18.75% (24576 bytes)   
AAC file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==================
```

---

### Post by lambono on 2008-02-26
Thanks for the responses.
To use the mplayer -identify syntax it seems I have to use the following to stop the file from playing 

```
mplayer -identify -frames 0 -vc null -vo null -ao null stream.dump
```

This will give me an output like this 

```
mplayer -identify -frames 0 -vc null -vo null -ao null stream.dump
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing stream.dump.
ID_AUDIO_ID=0
Audio file file format detected.
ID_FILENAME=stream.dump
ID_DEMUXER=audio
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=96000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=0
ID_LENGTH=378.00
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 96.0 kbit/6.80% (ratio: 12000->176400)
ID_AUDIO_BITRATE=96000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mad
Video: no video
Starting playback...


Exiting... (End of file)

```

It seems that this line "Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)" shows that it is an mp3 file. 

So how can I test for this in my script? 

Thanks!
Lambono

---

### Post by ron999 on 2008-02-26
Hmmm..
You inspected the file after you had downloaded it.
My suggestion was to inspect the stream before you download it.
:):)

But either way, I don't know how to use that information to instruct the script whether it needs to be  encoded to mp3 or not.
:confused:

Maybe someone else has an idea.:KS
:guitar::guitar:

---

### Post by lambono on 2008-02-29
Any Ideas?

---

