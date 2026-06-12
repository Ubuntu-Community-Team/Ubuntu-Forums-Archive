---
title: "Convert anything to XviD with ffodivx codec"
date: 2010-08-08
forum: Multimedia Software
---

### Post by pepitux on 2010-08-08
[in spanish]

Recientemente he adquirido un reproductor MP4 Energy Sistem que funciona con ficheros de video en formato **XviD** y audio **MP2**. El problema que tengo es que no consigo realizar la conversión desde otros formatos, aunque puedo ver y oir correctamente en Ubuntu los ficheros de muestra que se incluyen.

Lo he intentado ya con **ffmpeg**, **mencoder** y **avidemux**, combinando varios codecs y codificadores distintos, y cuando intento visualizarlo en el MP4 me responde siempre lo mismo "*Atención, archivo no soportado*".

En uno de los ficheros de muestra he obtenido la siguiente información:
```
$ mplayer -identify Energy.Sistem.avi
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Energy.Sistem.avi.
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  160x128  12bpp  15.000 fps  366.5 kbps (44.7 kbyte/s)
Clip info:
 Software: MEncoder 1.0rc2-4.2.1
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=MEncoder 1.0rc2-4.2.1
ID_CLIP_INFO_N=1
ID_FILENAME=Energy.Sistem.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=366496
ID_VIDEO_WIDTH=160
ID_VIDEO_HEIGHT=128
ID_VIDEO_FPS=15.000
ID_VIDEO_ASPECT=1.2500
ID_AUDIO_FORMAT=80
ID_AUDIO_BITRATE=304
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=104.27
ID_SEEKABLE=1
ID_CHAPTERS=0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mp3
Starting playback...
VDec: vo config request - 160 x 128 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.25:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.2500
VO: [xv] 160x128 => 160x128 Planar YV12 
A:4192.2 V:  10.8 A-V:4181.444 ct:  1.080 163/163  1%  1%  0.5% 1 0

```

La verdad es que aunque se puede visualizar vídeos codificados en **ffodivx**, desconozco si en Ubuntu se puede codificar vídeo haciendo uso de dicho codec. :-k 

Por tanto agradezco cualquier ayuda que me puedan dar. Utilizo Karmic 64.

Un saludo

---

### Post by fmmarzoa on 2011-01-11
[English version below]

Hola,

Estoy experimentando el mismo problema. ¿Conseguiste solucionarlo?

Saludos,




Hello,

I'm facing the same problem. Did you solve it?

Regads,

---

### Post by fmmarzoa on 2011-01-21
I've managed to solve this, if you're still interesting, you may read my blog entry about that:

[http://marzoa.com/2011/01/21/ubuntu-linux-encoding-videos-for-energy-sistem-mp4-devices/](http://marzoa.com/2011/01/21/ubuntu-linux-encoding-videos-for-energy-sistem-mp4-devices/)

---

### Post by andrew.46 on 2011-01-21
The sticking point with many of these devices is b-frames so you may find that the magic setting is *max_bframes=0*, as you have used it in your MEncoder string. You could try a similar command with FFmpeg utilising the equivalent *-bf 0* + the successful codecs and bitrates.

Andrew

---

