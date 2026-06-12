---
title: "mp3 issues"
date: 2009-06-11
forum: Multimedia Software
---

### Post by zackpete on 2009-06-11
I have a bunch of mp3s that i want to be able to play with mplayer from the command line. When I try to play one... nothing. I tried transcoding a few to a higher bitrate with lame and they will play, but not the whole thing. Here's the output from mplayer:

> MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing paciente.mp3.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 32.0 kbit/9.07% (ratio: 4000->44100)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 22050Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame 1.0 (00.9) ??,?% 
A:  -0.0 (unknown) of 1.0 (00.9) ??,?% 

Exiting... (End of file)


The mp3 is attached. How can I get these mp3s to play?

---

### Post by andrew.46 on 2009-06-11
Hi zackpete,

> **zackpete said:**
> The mp3 is attached. How can I get these mp3s to play?

Yes, it plays perfectly with my copy of MPlayer:

```

andrew@skamandros~/Desktop$ mplayer paciente.mp3 
MPlayer SVN-r29352-4.2.4 (C) 2000-2009 MPlayer Team

Playing paciente.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.7 (00.6) of 1.0 (00.9)  0.2% 

Exiting... (End of file)

```

and seems to simply a heavily accented voice saying the word 'paciente'?. If you are keen on MPlayer you can get an easy upgrade / reinstall by using the [MEdibuntu]("https://help.ubuntu.com/community/Medibuntu") MPlayer and this might be enough to get mp3s playing. If you follow this road and are using a 32bit system it would be a good idea, but not needed for mp3s, to pick up the w32codecs as well.

All the best,

Andrew

---

### Post by mc4man on 2009-06-11
try 
mplayer paciente.mp3 -ac mp3

Ex.
> doug@doug-laptop:~/Desktop/audtest$ mplayer paciente.mp3 -ac mp3
MPlayer SVN-r29330-4.2.4 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing paciente.mp3.
Audio only file format detected.
==========================================================================
[COLOR="Blue"]Forced audio codec: mp3[/COLOR]
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.9 (00.8) of 1.0 (00.9)  1.3% 


---

### Post by zackpete on 2009-06-11
The '-ac mp3' option worked. I had to be able to play .wav files with the same command (using it in the program FullRecall) so I just added a comma:
'mplayer -ac mp3,'
The comma makes mplayer look for another codec if mp3 fails, as with wav files. (I found that in the giant man page for mplayer)
Thank you for your help!

---

### Post by andrew.46 on 2009-06-11
Hi zackpete,

> **zackpete said:**
> The '-ac mp3' option worked. I had to be able to play .wav files with the same command (using it in the program FullRecall) so I just added a comma:
'mplayer -ac mp3,'
The comma makes mplayer look for another codec if mp3 fails, as with wav files. (I found that in the giant man page for mplayer)

My apologies for proposing such a huge solution to a problem that has obviously benefited by a more *focused* solution :-). While you are digging in the man pages have a look at the '-afm' option which might be useful as well. For example if you wanted MPlayer to try libavcodec codecs *first* you could try:

```

andrew@skamandros~/Desktop$ **[COLOR="Purple"]mplayer -afm ffmpeg paciente.mp3[/COLOR]**
MPlayer SVN-r29355-4.2.4 (C) 2000-2009 MPlayer Team

Playing paciente.mp3.
Audio only file format detected.
==========================================================================
Trying to force audio codec driver family ffmpeg...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 32.0 kbit/9.07% (ratio: 4000->44100)
**[COLOR="Purple"]Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio)[/COLOR]**
==========================================================================
AO: [oss] 22050Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.0 (00.9) of 1.0 (00.9)  0.4% 

Exiting... (End of file)

```

and as the man pages explain you can see all of the available 'families' by running:

```

andrew@skamandros~$ **[COLOR="Purple"]mplayer -afm help[/COLOR]**
MPlayer SVN-r29355-4.2.4 (C) 2000-2009 MPlayer Team
Available (compiled-in) audio codec families/drivers:
    afm:    info:  (comment)
   mp3lib  MPEG layer-2, layer-3 (Optimized to MMX/SSE/3Dnow!)
   liba52  AC3 decoding with liba52
    hwac3  AC3/DTS pass-through S/PDIF
    hwmpa  MPEG audio pass-through (fake decoder) (For hardware decoders)
   ffmpeg  FFmpeg/libavcodec audio decoders
      pcm  Uncompressed PCM audio decoder
   dvdpcm  Uncompressed DVD/VOB LPCM audio decoder
     alaw  aLaw/uLaw audio decoder
 imaadpcm  IMA ADPCM audio decoder
  msadpcm  MS ADPCM audio decoder
 dk3adpcm  Duck Corp. DK3 ADPCM decoder
    msgsm  native GSM/MSGSM audio decoder
    dshow  Win32/DirectShow decoders
      dmo  Win32/DMO decoders
      acm  Win32/ACM decoders
      vqf  TWinVQ decoder (Ported from MPlayerXP)
  qtaudio  QuickTime Audio Decoder (uses win32 quicktime DLLs)
     faad  AAC (MPEG2/4 Advanced Audio Coding) (uses libfaad2)
   tremor  Ogg/Vorbis audio decoder
    speex  Speex audio decoder
   libmad  libmad mpeg audio decoder (based on Xine's libmad/xine_decoder.c)
  realaud  RealAudio decoder (binary real audio codecs)
    libdv  Raw DV Audio Decoder
   mpcdec  Musepack audio decoder
   libdca  DTS decoding with libdca

```

To my mind the *ffmpeg* option is probably the most useful of these. The video equivalent of this setting is *mplayer -vfm ffmpeg <filename>*. What a fantastic program!!!

Andrew

---

