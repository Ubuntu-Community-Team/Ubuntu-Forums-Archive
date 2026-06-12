---
title: "How do I Configure audio output for 24 bit depth?"
date: 2013-11-18
forum: Multimedia Software
---

### Post by rocky_raccoon on 2013-11-18
I've been trying to set up Ubuntu to output 24 bit audio. Looking around the net I haven't been able to put anything together, I can't figure out how this works. I used this command on the terminal:

```
pacmd list-sinks
```

And I got a lot gibberish that I do not understand but I noticed some lines stating:

```
alsa.resolution_bits = "16"
```

and

```
sample spec: s16le
```

How do I change that to 24? Or how do I get 24 bit output anyhow?

Many thanks

---

### Post by shantiq on 2013-11-20
hey there RR [¡Hola!]


i am not convinced this is needed i think the players "know"   how to find those specs and use them

> shan@shan:~/Music/1969 - Trout Mask Replica [24bit 96khz][FLAC]$ [mpv]("http://ubuntuforums.org/showthread.php?t=2187364&p=12845794#post12845794") *
Playing: 01 Frownland.flac
Detected file format: raw FLAC (libavformat)
Clip info:
 TITLE: Frownland
 track: 01
 ALBUM: Trout Mask Replica [24bit 96khz]
 DATE: 1969
 ARTIST: Captain Beefheart & His Magic Band
 GENRE: Progressive Rock
[stream] Audio (+) --aid=1 (flac)
Video: no video
Selected audio codec: FLAC (Free Lossless Audio Codec) [lavc:flac]
**AO: [alsa] 96000Hz stereo 2ch s32le**
A: 00:00:30 / 00:01:37 (31%)                                                    


Exiting... (Quit)
shan@shan:~/Music/1969 - Trout Mask Replica [24bit 96khz][FLAC]$ mplayer *
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 01 Frownland.flac.does not show
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
Audio only file format detected.
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 96000 Hz, 2 ch, s32le, 2960.8 kbit/48.19% (ratio: 370097->768000)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
==========================================================================
**AO: [pulse] 96000Hz 2ch s32le (4 bytes per sample)**
Video: no video
Starting playback...
A:  13.4 (13.3) of 97.0 (01:37.0)  2.1% 
[1]+  Stopped                 mplayer *
shan@shan:~/Music/1969 - Trout Mask Replica [24bit 96khz][FLAC]$ 



[ATTACH=CONFIG]247959[/ATTACH]


But anyway reading around this seems to be the route one should take to change default settings


**check** your card can support 24-bit !

```
 cd /proc/asound/
```

list cards ```
   ls
```


i find     ```
Alpha  card0  card1  card2  card3  cards  devices  hwdep  IXP  modules    NVidia    pcm  seq  timers  U0x46d0x9a4  version
```

go to card** you **wish to use    

```
cd Alpha
```      obviously mine not yours

list again```
  ls
```

i find   ```
 id  pcm0c  pcm0p  stream0  usbbus  usbid  usbmixer
```

```
gedit stream0
```     see that 24 bit is available on your card


so for me   ```
leafpad  /proc/asound/Alpha/stream0
```

```
Lexicon Lexicon Alpha at usb-0000:00:13.0-2, full speed : USB Audio

Playback:
  Status: Running
    Interface = 1does not show
    Altset = 1
    Packet Size = 192
    Momentary freq = 48000 Hz (0x30.0000)
  Interface 1
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 1 OUT (SYNC)
    Rates: 44100, 48000
  Interface 1
    Altset 2
**    Format: S24_3LE**
    Channels: 2
    Endpoint: 1 OUT (SYNC)
    Rates: 44100, 48000

Capture:
  Status: Stop
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 2 IN (SYNC)
    Rates: 44100, 48000
  Interface 2
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 2 IN (SYNC)
    Rates: 44100, 48000
```

if card does not show 24-bit there is no point in continuing



[SIZE=4]** [SIZE=3]then enter[/SIZE]**[/SIZE] your modified settings



```
 sudo gedit /etc/pulse/daemon.conf 
```


i  use leafpad instead of gedit   as it has line numbers


then find on line 76

```
 ; default-sample-format = s16le
```

and change to  

```
default-sample-format = s24le
```

     [make sure you remove the ";"  apparently it is important]

[ATTACH=CONFIG]247958[/ATTACH]


and SAVE     YOU CAN ALSO CHANGE  sample-rate and sample-channels in same way


hope this works for you     shan

PS again i am not sure any of this is needed

---

### Post by stevergarner on 2014-01-31
Thank you Shantiq. Apologies for commenting on this older thread, but it was helpful to me.

I recently purchased a HRT Music Streamer II (external USB audio), that supports up to 96kHz/24bit and was annoyed that the LED on the device was not showing 96kHz when I was playing audio files that were 96kHz. Meaning, the 96kHz was down sampled to 48kHz with the default settings.

These are my current changed entries in /etc/pulse/daemon.conf that eliminates down sampling for 96kHz audio.

```

resample-method = speex-float-5
;resample-method = speex-float-1


default-sample-format = s24le
; default-sample-format = s16le
alternate-sample-rate = 96000
; default-sample-rate = 44100

```

The change to the resample method was based on the following link and the belief that my recent quad core cpu can handle the work. The audio that will be resampled will be 88200 and 48000 where 88200 is sampled down to 44100 and 48000 is sampled up to 96000. I have very little music at either 88200 or 48000, so this is not a big issue for me. 
[http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Audiophile/](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Audiophile/)

Were these changes necessary given the current quality of my speakers and headphones? Probably not, but I will test again after I upgrade my headphones.

---

