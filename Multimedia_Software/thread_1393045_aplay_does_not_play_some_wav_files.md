---
title: "aplay does not play some wav files"
date: 2010-01-28
forum: Multimedia Software
---

### Post by saskms on 2010-01-28
Okay, this is probably an easy question to answer, although not for me apparently. 

My audio is working on my recent koala install. System wav files play without a problem.

However, when I open a terminal to play my own wav files I get an error. (I encountered this problem merely by trying to setup an incoming mail notification with CheckGmail....)

**The command:** aplay /home/saskms/Music/test.wav
[B]
The error:[/B] aplay: test_wavefile:807: can't play WAVE-file format 0x0002 which is not PCM or FLOAT encoded

I think I have installed all the necessary gstreamer options. I am guessing that maybe I just need to re-rip the WAV file into a different format. I also tried doing searches on the error, but yielded no results. 

Any suggestions would be very appreciated!

---

### Post by mc4man on 2010-01-28
Don't now where you got or produced those troublesome .wav's though the error suggests they're creative labs files. (mabe some form of .voc

If you have mplayer installed then this may show some info about the file

mplayer /path/to/filename


possibly relevant
> Valid values of wFormat are:

		  0x0000  8-bit unsigned PCM
		  0x0001  Creative 8-bit to 4-bit ADPCM
		 [COLOR="Blue"] 0x0002  Creative 8-bit to 3-bit ADPCM[/COLOR]
		  0x0003  Creative 8-bit to 2-bit ADPCM
		  0x0004  16-bit signed PCM
		  0x0006  CCITT a-Law
		  0x0007  CCITT u-Law
		  0x02000 Creative 16-bit to 4-bit ADPCM


---

### Post by saskms on 2010-01-28
Okay. Thank you. I installed mplayer and ran the file again. The file played perfectly. However, I get the same error as in my initial post using aplay. Hmmmm.

saskms@saskms:~$ mplayer /home/saskms/Music/test.wav
Creating config file: /home/saskms/.mplayer/config
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/saskms/Music/test.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 11025 Hz, 1 ch, s16le, 45.3 kbit/25.70% (ratio: 5666->22050)
Selected audio codec: [ffadpcmms] afm: ffmpeg (FFmpeg MS ADPCM audio)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 11025Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.9 (01.8) of 2.0 (02.0)  0.1% 

Exiting... (End of file)

---

### Post by saskms on 2010-01-28
So, I guess mplayer will play the wav file, but not aplay. (Nor my checkgmail incoming mail notifier).

Am I missing a codec or something? That is odd because mplayer plays the file. :(

---

### Post by mc4man on 2010-01-28
So it's a MS ADPCM file which I'd think most players could play.

I guess if need be you could convert to a pcm, though it would increase the size quite a bit. 
(unless your checkgmail can use something other than .wav ...?, then you could convert to that format - mp3, ogg, ect.


```
ffmpeg -i /home/saskms/Music/test.wav /home/saskms/Music/test-1.wav
```

---

### Post by saskms on 2010-01-29
THANK YOU! That worked perfectly. Many many thinks. I was really banging my head on this.

---

