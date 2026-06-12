---
title: "Trying to play WMV files"
date: 2009-10-07
forum: Multimedia Software
---

### Post by Rick Abraham on 2009-10-07
Hi Guys Im using Ubuntu 9.04 64bit and Im trying to play some .wmv movie files in Movie Player.
I downloaded the following

w64codecs_20071007-0.3_amd64.deb

and I installed it, I restarted the PC and tried to open a .wmv file and NO GOOD.
Movie Player trys to search for a suitable Plugin but doesnt fine one.

Does anyone know what Im doing wrong ?????
Any help would be awesome.

---

### Post by mastermindg on 2009-10-07
Quick Suggestion: Use VLC. 

I'm not a huge fan of Totem anyway and VLC has way more functionality.

---

### Post by Rick Abraham on 2009-10-07
Hi I downloaded VLC and tried to run a .wmv file I have and this is the error message I got.

[COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this.[/COLOR]


[COLOR=#000000]Does anyone know what this means ?
[/COLOR]

---

### Post by Rick Abraham on 2009-10-07
I seem to be able to play other WMV files, just not a few, something must be different with these particular files.
The ones Im trying to play are Train Signal training videos.

---

### Post by mastermindg on 2009-10-07
Probably an issue with the video itself, i.e. specialized codecs. Go2Meeting doesn the same thing where it's got wmv files but uses a proprietary codec. Good luck finding the codec to play these.

---

### Post by mc4man on 2009-10-07
mss2 is microsoft screen codec
vlc doesn't support mss2 but mplayer does

see here
[http://ubuntuforums.org/showthread.php?t=1229073](http://ubuntuforums.org/showthread.php?t=1229073)

---

### Post by mastermindg on 2009-10-07
VLC can support MSS2 by enabling DMO (Direct Memory Object) access and copying the windows media dll's to /usr/win32. This is directly from the VLC site:

> Under linux, you can use them with the --enable-loader switch that uses Wine's emulation. You have to put the Windows Media dlls in the /usr/win32 folder. 

This is why I love VLC! It's VERSATILE!

---

### Post by mc4man on 2009-10-07
> VLC can support MSS2 by enabling DMO (Direct Memory Object) access 

Note that --enable-loader is a compile option not a runtime one

Also "can support" is true, does is not.

In the above linked thread there is a wget in post 3 to a typical mms2 file, if you can get it to play in vlc would be interested in hearing about

---

