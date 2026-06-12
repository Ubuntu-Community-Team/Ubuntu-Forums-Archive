---
title: "VLC media player .ts file and error."
date: 2010-01-01
forum: Multimedia Software
---

### Post by Mu-oht-Ahn-jay on 2010-01-01
[I]Okay running on 64bit karmic 9.10
[/I] [I]i have been trying to get this .ts file to play nicely on vlc, 
but no success of getting it work nicely what 
so ever. 
It actually starts under VLC and gives image and sound but not the way i would prefer it. 
[/I] [I]
I don't quite get it but when i start it with vlc it actually 
displays it with lower resolution
this is HD file, as its a stream capture from tv 
but it outputs it with much smaller resolution about 320 x 180. 

[/I]  [I]Tried it with other players too but the only one that accepted it nicely was xine 
"but problems ahead again" it outputs no sound? the image though  was and is what it should be.

[/I]  [I]Tried it with Totem too and it did accept it too actually "hurray! but with the same symptoms as VLC + 
it doesn't output any sound out from the file only the image is what gets generated out from the player. 

I ran VLC from the terminal and it outputs following data when i start to play the file:


VLC media player 1.0.2 Goldeneye
[0x15af888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 0) for PID 8136
[0x1b3dce8] ts demux error: MPEG-4 descriptor not found
libdvbpsi error (PSI decoder): TS discontinuity (received 14, expected 0) for PID 1064
[0x1b3dce8] ts demux error: MPEG-4 descriptor not found
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 0) for PID 1065
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 0) for PID 1066
[0x2071cf8] packetizer_mpeg4audio packetizer: AAC channels: 2 samplerate: 24000
[0x20af678] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 0) for PID 17
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
QPainter::begin: Paint device returned engine == 0, type: 1
[0x1b3dce8] ts demux error: MPEG-4 descriptor not found
[0x1b3dce8] ts demux error: MPEG-4 descriptor not found
libdvbpsi error (PSI decoder): TS discontinuity (received 14, expected 11) for PID 1066
libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 10) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 4, expected 12) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 13) for PID 1064
libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 11) for PID 1065
libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 9) for PID 8136
out of range intra chroma pred mode at 14 5
error while decoding MB 14 5
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 2) for PID 17

[/I]     [I]

so if any ONE knows what should i do, feel free to step up and advise me ;-) would be appreciated (thanks in advance)
If this has value if's mpeg2 ts file.  And no...the file ain't corrupted that much i know, but what could generate this problem. If it ain't broken? Seeking works nice etc... except the low resolution display.
[/I]

---

### Post by Mu-oht-Ahn-jay on 2010-01-08
bump... haven't yet been able to solve this by myself.

---

### Post by mc4man on 2010-01-08
You could ck  in tools -> preferences that "resize interface to video size" is enabled. (also avail. as "resize interface to the native video size" - same thing 
If it is already than vlc has an issue with that file, though if you close vlc when the interface is maximized then it will re-open that way.

xine -> settings -> setup, change the experience level and then under audio tab try a different driver (alsa may do

---

