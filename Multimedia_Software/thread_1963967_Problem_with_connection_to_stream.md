---
title: "Problem with connection to stream"
date: 2012-04-23
forum: Multimedia Software
---

### Post by mihoo on 2012-04-23
Hi, I can't connect to any stream via Totem, Rhythmbox, VLC also can't open playlists like [http://somafm.com/groovesalad130.pls](http://somafm.com/groovesalad130.pls) 

Only in Audaciuos i can open playlist and stream also streamripper works for example:
streamripper [http://voxsc1.somafm.com:3000](http://voxsc1.somafm.com:3000) -r
Recording works but only in Audaciuos i can open [http://localhost:8000](http://localhost:8000) to listen other players give me http 404 error. I check that in terminal with "rhythmbox -d" command.

I use Tor and Privoxy maybe im messed up with configuration?

---

### Post by ron999 on 2012-04-23
> **mihoo said:**
>  VLC also can't open playlists like [http://somafm.com/groovesalad130.pls](http://somafm.com/groovesalad130.pls) 


I use Tor and Privoxy maybe im messed up with configuration?

VLC plays this pls OK for me.
Media > Open location from clipboard

Or try it from the command line
Like this:-
```
vlc http://somafm.com/groovesalad130.pls
```

---

### Post by mihoo on 2012-04-23
After run vlc [http://somafm.com/groovesalad130.pls](http://somafm.com/groovesalad130.pls) in terminal i have this info in vlc log:

access_mms error: unrecognized chunk FATAL (0x705b)
access_mms error: header size == 0
main error: open of `[http://somafm.com/groovesalad130.pls](http://somafm.com/groovesalad130.pls)' failed

I don't know where to start to do anything with this problem :/

---

### Post by ron999 on 2012-04-23
> **mihoo said:**
> 

I don't know where to start to do anything with this problem :/
What about MPlayer from command line?
```
mplayer http://somafm.com/groovesalad130.pls
```

---

### Post by mihoo on 2012-04-23
Mplayer and Audacious works fine.

```
$ mplayer http://somafm.com/groovesalad130.pls
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://somafm.com/groovesalad130.pls.
Resolving somafm.com for AF_INET6...

Couldn't resolve name for AF_INET6: somafm.com
Resolving somafm.com for AF_INET...
Connecting to server somafm.com[64.147.167.20]: 80...

Cache size set to 320 KBytes
Unknown entry type Version=2


Playing http://voxsc1.somafm.com:3000.
Resolving voxsc1.somafm.com for AF_INET6...

Couldn't resolve name for AF_INET6: voxsc1.somafm.com
Resolving voxsc1.somafm.com for AF_INET...
Connecting to server voxsc1.somafm.com[74.63.47.82]: 3000...

Name   : Groove Salad from SomaFM [aac] [SomaFM]
Genre  : Downtempo Ambient Groove
Website: http://SomaFM.com
Public : yes
Bitrate: 128kbit/s
Cache size set to 320 KBytes
Cache fill:  7.50% (24576 bytes)   
ICY Info: StreamTitle='Pay-Per-Frog - Over Easy';StreamUrl='http://somafm.com/logos/512/groovesalad512.png';
Cache fill: 12.50% (40960 bytes)   

AAC file format detected.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 44100 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->176400)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  57.4 (57.3) of 0.0 (unknown)  0.6% 45% 
ICY Info: StreamTitle='Zigo - Voodoo';StreamUrl='http://somafm.com/logos/512/groovesalad512.png';

```

Totem, VLC, Rhythmbox not works. Tere is some lib dependency or some common files between them?

---

### Post by mihoo on 2012-05-09
@[ron999]("http://ubuntuforums.org/member.php?u=139331") Thank You for Your time and suggestions :) 
I think now so this is a some proxy problem with some apps but still I don't know where, why...

Solved simply with switch in system settings from direct connection to automatic and back to direct again :D

---

