---
title: "mplayer 24bit/96Khz from DVD to hard disk (s24be)"
date: 2014-01-12
forum: Multimedia Software
---

### Post by stevergarner on 2014-01-12
I have the 40th anniversary DVD of Jethro Tull's "Thick as a Brick" that includes the 24bit/96Khz pcm audio of the remaster. I want to be able to listen to the music without inserting the DVD by copying to the hard drive. 

I determined the title I wanted was 2 and tried this first:
```

$ mplayer dvd://2 -dvd-device /dev/sr0 -chapter 1-1 -vc null -vo null -ao pcm:file=16taabside1.wav
...
==========================================================================
Opening audio decoder: [dvdpcm] Uncompressed DVD/VOB LPCM audio decoder
AUDIO: 96000 Hz, 2 ch, s24be, 4608.0 kbit/100.00% (ratio: 576000->576000)
Selected audio codec: [dvdpcm] afm: dvdpcm (Uncompressed DVD/VOB LPCM)
==========================================================================
[AO PCM] File: 16taabside1.wav (WAVE)
PCM: Samplerate: 96000 Hz   Channels: 2   Format: s16le
[AO PCM] Info: Faster dumping is achieved with -novideo
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 96000Hz 2ch s16le (2 bytes per sample)
Starting playback...

```

Sampled down from 24bit to 16bit, not what I wanted. 
Tried changing pulse audio configs with no luck.
Tried dvd::rip on same title, audio was corrupted.
Tried vlc convert and audio was corrupted.
Tried ffmpeg/avconv directly and also corrupted.

What finally worked for me was asking mplayer to use a 32bit little endian format instead. (32bit big endian also output as 16bit for some reason)
```

$ mplayer dvd://2 -dvd-device /dev/sr0 **-format s32le** -chapter 1-1 -vc null -vo null -ao pcm:file=32taabside1.wav
...
==========================================================================
Opening audio decoder: [dvdpcm] Uncompressed DVD/VOB LPCM audio decoder
AUDIO: 96000 Hz, 2 ch, s24be, 4608.0 kbit/100.00% (ratio: 576000->576000)
Selected audio codec: [dvdpcm] afm: dvdpcm (Uncompressed DVD/VOB LPCM)
==========================================================================
[AO PCM] File: 32taabside1.wav (WAVE)
PCM: Samplerate: 96000 Hz   Channels: 2   Format: s32le
[AO PCM] Info: Faster dumping is achieved with -novideo
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
**AO: [pcm] 96000Hz 2ch s32le (4 bytes per sample)**
Starting playback...

```

I looked at this "32bit" file in a hex editor and indeed, every 4th byte in the data section was "00" and the file was larger than the 16bit file by about 2 times. 
Next I converted to 24bit little endian audio and created a flac from the 24bit wav to save on some space. 
```

$ avconv -i 32taabside1.wav **-acodec pcm_s24le** 24taabside1.wav
$ flac 24taabside1.wav
$ ls -l 
523108396 Jan 12 11:15 16taabside1.wav
489362123 Jan 12 11:16 24taabside1.flac
784613444 Jan 12 11:16 24taabside1.wav
1046151212 Jan 12 11:14 32taabside1.wav

```

Playing the FLAC results in it being sampled up to 32 bits on the fly by mplayer, but that is ok. According to aplay, only 16 and 32 bit are supported on my system. For 96Khz/24bit audio I have purchased from HDTracks, I also see this up sampling from s24le to s32le

```

mplayer 24taabside1.flac 
...
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 96000 Hz, 2 ch, s32le, 0.0 kbit/0.00% (ratio: 0->768000)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
==========================================================================
AO: [pulse] 96000Hz 2ch s32le (4 bytes per sample)
Video: no video
Starting playback...

```

There may be an easier way to do this, but this sounds like it worked.

---

