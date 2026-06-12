---
title: "Problems with streaming Real Audio files"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by oygle on 2007-11-27
I have read a number of "how to's" , and followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=542276") , but keep getting errors. I think the problem is a codec one ??

Here is what happens ..

> 
$ mplayer -playlist [http://lifestream.org/audio/TheProdigalSon.ram](http://lifestream.org/audio/TheProdigalSon.ram) \ -ao pcm:file=TheProdigalSon.wav -vc null -vo null
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron Covington/Pentium II Deschutes,Tonga/Pentium II Xeon (Family: 6, Model: 5, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
Resolving lifestream.org for AF_INET6...
Couldn't resolve name for AF_INET6: lifestream.org
Resolving lifestream.org for AF_INET...
Connecting to server lifestream.org[69.89.20.60]: 80...
Cache size set to 320 KBytes
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://www.lifestream.org/audio/TheProdigalSon.rm](http://www.lifestream.org/audio/TheProdigalSon.rm).
Resolving [www.lifestream.org](www.lifestream.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.lifestream.org](www.lifestream.org)
Resolving [www.lifestream.org](www.lifestream.org) for AF_INET...
Connecting to server [www.lifestream.org](www.lifestream.org)[69.89.20.60]: 80...
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
REAL file format detected.
Stream description: fileinfo
Stream mimetype: logical-fileinfo
Stream description: audio/x-pn-multirate-realaudio logical stream
Stream mimetype: logical-audio/x-pn-multirate-realaudio
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
Resolving [www.lifestream.org](www.lifestream.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.lifestream.org](www.lifestream.org)
Resolving [www.lifestream.org](www.lifestream.org) for AF_INET...
Connecting to server [www.lifestream.org](www.lifestream.org)[69.89.20.60]: 80...
Resolving [www.lifestream.org](www.lifestream.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.lifestream.org](www.lifestream.org)
Resolving [www.lifestream.org](www.lifestream.org) for AF_INET...
Connecting to server [www.lifestream.org](www.lifestream.org)[69.89.20.60]: 80...
Resolving [www.lifestream.org](www.lifestream.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.lifestream.org](www.lifestream.org)
Resolving [www.lifestream.org](www.lifestream.org) for AF_INET...
Connecting to server [www.lifestream.org](www.lifestream.org)[69.89.20.60]: 80...
Clip info:
 name: The Prodigal Son
 author: Wayne Jacobsen
 copyright: ï¿½1999
==========================================================================
Forced audio codec: mad
Opening audio decoder: [realaud] RealAudio decoder
Error: /usr/lib/win32/sipr.so.6.0: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: sipr.so.6.0, /usr/lib/win32/sipr.so.6.0, /usr/local/lib/win32/sipr.so.6.0
Error loading dll
ERROR: Could not open required DirectShow codec sipr.so.6.0.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Error: /usr/lib/win32/sipr.so: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: sipr.so, /usr/lib/win32/sipr.so, /usr/local/lib/win32/sipr.so
Error loading dll
ERROR: Could not open required DirectShow codec sipr.so.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Win32 LoadLibrary failed to load: sipr3260.dll, /usr/lib/win32/sipr3260.dll, /usr/local/lib/win32/sipr3260.dll
Error loading dll
ERROR: Could not open required DirectShow codec sipr3260.dll.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Error: /usr/lib/win32/sipr.bundle/Contents/MacOS/sipr: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: sipr.bundle/Contents/MacOS/sipr, /usr/lib/win32/sipr.bundle/Contents/MacOS/sipr, /usr/local/lib/win32/sipr.bundle/Contents/MacOS/sipr
Error loading dll
ERROR: Could not open required DirectShow codec sipr.bundle/Contents/MacOS/sipr.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x72706973.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Playing  -ao.
File not found: ' -ao'
Failed to open  -ao.

Playing pcm:file=TheProdigalSon.wav.
File not found: 'pcm:file=TheProdigalSon.wav'
Failed to open pcm:file=TheProdigalSon.wav.

Exiting... (End of file)
$ 


I used Firefox to grab the ram file, of course it was only a very small file. Then opened it in Totem Movie Player, and it said it needed to search for codecs, which it did, and found "GStreamer extra plugins". There is a message saying it is from the "ugly" set and might pose distribution problems.

If possible, I'd like to not have to install proprietary software or codecs to make this work.

I see some people recommend VLC, can that stream RAM files ?

Thanks !!

---

### Post by ron999 on 2007-11-27
Hi
If you right-click on that ram link then Save Link As...
and save it to your hard drive.
Then open up the downloaded file with text editor.
You'll see it says:-
[http://www.lifestream.org/audio/TheProdigalSon.rm](http://www.lifestream.org/audio/TheProdigalSon.rm)
You can play this with Totem by using Movie > Open Location
then paste it in.

******

I use these links with RealPlayer using File > Open Location
then paste it in. 

Alternatively I can use the monitor if I type:-
realplay [http://www.lifestream.org/audio/TheProdigalSon.rm](http://www.lifestream.org/audio/TheProdigalSon.rm)
Then RealPlayer opens up and plays the programme through the speakers.
So you need to have RealPlayer 10 installed to do this.

And then if you want to save the programme as an audio file you need to install an app named vsound.
sudo apt-get install vsound

This is how vsound works.
At the monitor type:-
vsound -t -d -f output.wav realplay [http://www.lifestream.org/audio/TheProdigalSon.rm](http://www.lifestream.org/audio/TheProdigalSon.rm)
Then RealPlayer plays the programme through the speakers as before, but this time a file will start to build up on your hard drive. The file will be named (similar to) vsound30470.au.
When the programme ends, or you've recorded enough, close RealPlayer and close the monitor.
Then the vsound30470.au file will disappear and in its place will appear a file named output.wav.
That's your programme in wav form.
If you want to convert it later to mp3 you can use command
lame output.wav output.mp3
This will give you 128Kbps 44kHz mp3.

I use this setup for recording programmes from BBC radio.
RealPlayer can be tricky to install. I bottled out and let Automatix install it for me.
Good Luck
:cool:

---

### Post by oygle on 2007-11-27
> **ron999 said:**
> 
If you right-click on that ram link then Save Link As...
and save it to your hard drive. Then open up the downloaded file with text editor.
You'll see it says:-
[http://www.lifestream.org/audio/TheProdigalSon.rm](http://www.lifestream.org/audio/TheProdigalSon.rm)
You can play this with Totem by using Movie > Open Location
then paste it in.


I _think_ that is what Totem was trying to do, but I will try what you have suggested, thanks.

> **ron999 said:**
> 
So you need to have RealPlayer 10 installed to do this.


I assume RealPlayer 10 is not open source, but proprietary ?

Thanks for the tips on vsound and RealPlay. It's a pity I can't just get the mplayer codec. What about the [Binary Codec packages]("http://www.mplayerhq.hu/design7/dload.html") for mplayer ?

Thanks for your help,

Oygle

---

### Post by andrew.46 on 2007-11-28
Hi Oygle,

 Thanks for the message, which in a moment of stupidity I deleted! My aplologies for not replying privately.

 Now I have the latest svn mplayer with the 2007 full codec pack and I could not play this file :-) I have downloaded it as follows:

```
# wget http://lifestream.org/audio/TheProdigalSon.rm
```

 and had a good go at it. It is a not insubstantial file at 6.7 megs but all I can get out of it is Direct Show errors. My apologies as I am no use to you :confused:

               Andrew

---

### Post by oygle on 2007-11-28
Hi Andrew,

No worries about the PM.  :)

Thanks for trying with the file,

Oygle

---

### Post by wisam on 2007-11-28
Weeks ago mplayer had no problem playing streaming Real Audio from BBC. Not even binary codecs were needed. But yesterday, I was trying to watch a video on BBC and got that same error that you got. I installed w32codecs and was able to play the video file. Maybe BBC upgraded to a new version of Real Audio/Video that is not supported by native mplayer codecs.

---

### Post by oygle on 2007-11-28
Okay thanks for advising on that. I'd prefer not to have to install w32codecs, but if there is no other way around the problem ?

Maybe the mplayer mailing list has some info on this, like [this post]("http://article.gmane.org/gmane.comp.video.mplayer.user/53887/match=real")

---

### Post by andrew.46 on 2008-02-25
Hi,

 Oddly enough on coming back to this post I can play the file quite successfully:

```

andrew@ilium~/Desktop$ mplayer TheProdigalSon.rm 
MPlayer dev-SVN-r26096-4.1.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing TheProdigalSon.rm.
REAL file format detected.
Stream description: fileinfo
Stream mimetype: logical-fileinfo
Stream description: audio/x-pn-multirate-realaudio logical stream
Stream mimetype: logical-audio/x-pn-multirate-realaudio
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
[real] Audio stream found, -aid 0
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
[real] Audio stream found, -aid 1
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
[real] Audio stream found, -aid 2
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 3
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
[real] Audio stream found, -aid 4
Clip info:
 name: The Prodigal Son
 author: Wayne Jacobsen
 copyright: &#65533;1999
==========================================================================
Opening audio decoder: [realaud] RealAudio decoder
AUDIO: 16000 Hz, 1 ch, s16le, 16.0 kbit/6.25% (ratio: 2000->32000)
Selected audio codec: [rasipr] afm: realaud (RealAudio Sipro)
==========================================================================
AO: [oss] 16000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   9.4 (09.4) of 1129.0 (18:49.0)  0.3% 

```

      Andrew

---

### Post by oygle on 2008-02-26
Andrew,

I'll give it a try then, thanks. Maybe there has been an update of mplayer since ??

---

### Post by andrew.46 on 2008-02-26
Hi,

> **oygle said:**
> Andrew,

I'll give it a try then, thanks. Maybe there has been an update of mplayer since ??

A lot of movement on the mplayer front as always.. I did not try the streaming angle just:

```
$ wget http://lifestream.org/audio/TheProdigalSon.rm
$ mplayer  TheProdigalSon.rm
```

And it all played well.

      Andrew

---

### Post by oygle on 2008-03-01
No, still no go. I tried the same command as the first post .

> 
$ mplayer -playlist [http://lifestream.org/audio/TheProdigalSon.ram](http://lifestream.org/audio/TheProdigalSon.ram) \ -ao pcm:file=TheProdigalSon.wav -vc null -vo null


and got those same errors. Then I tried this ..

> 
mplayer -dumpstream [http://lifestream.org/audio/TheProdigalSon.ram](http://lifestream.org/audio/TheProdigalSon.ram) -dumpfile TheProdigalSon.ram


and checked the contents of the file, then ran this ..

> 
mplayer -dumpstream [http://lifestream.org/audio/TheProdigalSon.rm](http://lifestream.org/audio/TheProdigalSon.rm) -dumpfile TheProdigalSon.rm


and then tried this one ..

> 
mplayer TheProdigalSon.rm -ao pcm:file=TheProdigalSon.wav


and mplayer failed with all those 'win32' error messages.  There must be some way to stream a real audio file and convert it to WAV in one hit, **without** having to install proprietary software or codecs to make this work.

---

### Post by ron999 on 2008-03-01
Hi
I haven't been able to do the job in one hit.
But this will do it in two hits.

Use the command:-

```
mplayer -dumpstream http://www.lifestream.org/audio/TheProdigalSon.rm -vo null -vc null -ao null
```

This will download a file named 'stream.dump'. It's 6.7MB.

Now convert it to wav using command:-

```
mplayer stream.dump -vo null -vc null -ao pcm:file=TheProdigalSon.wav
```

:)

---

### Post by andrew.46 on 2008-03-01
Hi:

> **oygle said:**
> and mplayer failed with all those 'win32' error messages.  There must be some way to stream a real audio file and convert it to WAV in one hit, **without** having to install proprietary software or codecs to make this work.

The first command worked for me:

```
$ mplayer -playlist http://lifestream.org/audio/TheProdigalSon.ram  -ao pcm:file=TheProdigalSon.wav -vc null -vo null

```

But I am using the svn mplayer with a current codec pack:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

The repository version of mplayer is deliberately limited for political / legal reasons and I suspect that this is the problem that you are coming up against. Better to install and use software as the creators of that software intended.

                Andrew

---

### Post by oygle on 2008-03-06
> **ron999 said:**
> Hi
I haven't been able to do the job in one hit.
But this will do it in two hits.

  {snip}
:)

I tried as you suggested. The first command worked (as always), but the second command came up with the codec errors.

---

### Post by oygle on 2008-03-06
> **andrew.46 said:**
> 
Better to install and use software as the creators of that software intended.


As stated a number of times, I don't want to install/use proprietary software (after all, we are talking GNU). If the creators of the software can't convert a real audio file to WAV, then I guess I'll have to find some other audio software that can do it.

---

### Post by ron999 on 2008-03-06
That file is encoded using sipro (Real Audio 4/5).
Mplayer isn't proprietary software, but I guess it needs to have a suitable codec installed.
:)

---

