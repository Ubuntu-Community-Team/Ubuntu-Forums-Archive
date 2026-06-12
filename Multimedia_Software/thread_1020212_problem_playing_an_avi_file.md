---
title: "problem playing an avi file"
date: 2008-12-23
forum: Multimedia Software
---

### Post by uhha on 2008-12-23
i have a problem playing some avi files on Ubuntu 8.10 with any players:

vlc PRADA.avi

[mp3 @ 0xb0882388]Could not find codec parameters (Audio: mp1, 128 kb/s)
[00000424] avformat demux error: av_find_stream_info failed
[00000424] ps demux error: cannot peek
[00000424] dummy demux error: unknown command `PRADA.avi'
[00000414] main input error: no suitable demux module for `/://PRADA.avi'



mplayer  PRADA.avi

Playing PRADA.avi.
libavformat file format detected.
[mp3 @ 0x8837aa8]Could not find codec parameters (Audio: mp3, 64 kb/s)
LAVF_header: av_find_stream_info() failed
[/CODE]



gxine -v PRADA.avi

xine: found input plugin  : file input plugin
ebml: invalid master element
demux_dts: unsupported DTS stream type, or not a DTS stream
xine: couldn't find demux for >file:///home/uhha/downloads/video/PRADA.avi<
xine-lib: error: The xine engine failed to start.: No demuxer found - stream format not recognised.
xine: found input plugin  : file input plugin
xine: found demuxer plugin: image demux plugin


[B]
i also have an _other maschine_ with the same ubuntu version where i have _no problems_ playing this file...[/B]

here is an example output, where everything is ok:


mplayer  PRADA.avi

AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1

gxine -v PRADA.avi

xine: found input plugin  : file input plugin
failed to read 8 bytes at pos 1468549120
xine: found demuxer plugin: AVI/RIFF demux plugin


**how can i found out, what is the difference between this two maschines?**

---

### Post by 2hot6ft2 on 2008-12-23
You need codecs. Go here to get them. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by binbash on 2008-12-24
did you install w32codecs?

---

### Post by uhha on 2008-12-24
thank you for your answers. i've already had all that codecs (including w32codecs), mentioned in that tutorial. 
i've done all stuff that one more time, just to make sure, and i have all of them from medibuntu interpid.
but i'm still facing just the same problem...

---

### Post by mr_anas on 2009-01-14
I am having the same problem :(

the application like mplayer just turn off when i try.no any notes or any thing

i hope someone can help us

---

