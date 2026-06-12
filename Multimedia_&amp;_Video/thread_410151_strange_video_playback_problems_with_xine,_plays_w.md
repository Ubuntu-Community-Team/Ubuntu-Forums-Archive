---
title: "strange video playback problems with xine, plays wmv fine but nothing else"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by Nesnej Trick on 2007-04-15
I've been setting up my Edgy system here for a while, but I haven't found a solution for this one problem. I've successfully installed xinelib, xine-ui, and the mplayer win32 (all) codecs, but for some reason Xine refuses to play properly anything but wmv, which is somewhat odd.

When attempting to launch an .mpg video from the console in verbose mode, I get this error message: 
```
xine: found demuxer plugin: MPEG program stream demux plugin
audio_decoder: no plugin available to handle 'MPEG layer 2/3'

```

When trying to open a .mov file, this is what I get:
```
xine: found demuxer plugin: Apple Quicktime (MOV) and MPEG-4 demux plugin
video_decoder: no plugin available to handle 'Sorenson Video 1'
External func COMCTL32.dll:16
External func COMCTL32.dll:17
wine/module: QuickTime6.3 DLLs found
wine/module: QuickTime.qts patched!!! old entry=0x6693c3e0
theQuickTimeDispatcher caught -> 0x6693c3e0
wine/win32: Win32 Warning: Accessed uninitialized Critical Section (0x66bd5028)!
WARNING! Invalid Ptr handle!
wine/win32: Win32 Warning: Accessed uninitialized Critical Section (0x66bd5010)!
### FindNext: AvidQTAVUICodec.qtx
### FindNext: BeHereiVideo.qtx
### FindNext: QuickTimeEssentials.qtx
### FindNext: QuickTimeInternetExtras.qtx
### FindNext: AvidQTAVUICodec.qtx
### FindNext: BeHereiVideo.qtx
### FindNext: QuickTimeEssentials.qtx
### FindNext: QuickTimeInternetExtras.qtx
### FindNext: AvidQTAVUICodec.qtx
### FindNext: BeHereiVideo.qtx
### FindNext: QuickTimeEssentials.qtx
### FindNext: QuickTimeInternetExtras.qtx

```


Some avi files do work:
```
xine: found demuxer plugin: AVI/RIFF demux plugin
Loading codec DLL: 'iccvid.dll'
Loaded DLL driver iccvid.dll

```

Most, however, don't:
```
xine: found demuxer plugin: AVI/RIFF demux plugin
video_decoder: no plugin available to handle 'Motion JPEG'

```

What to do?

---

### Post by Nesnej Trick on 2007-04-15
I also did some testing with mplayer, it won't play most of the .wmv files I've thrown at it and attempting to play an .mpg file results in the following message:
```
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.

```
Oddly enough, the sound does play though.
.mov files play without a hitch.

---

### Post by Nesnej Trick on 2007-04-16
I also tried recompiling ffmpeg and xine-lib, to no avail. Mplayer, however, seems to work now. I guess it's time to switch players.

---

