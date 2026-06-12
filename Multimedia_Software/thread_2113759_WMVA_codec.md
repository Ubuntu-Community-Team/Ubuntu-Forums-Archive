---
title: "WMVA codec?"
date: 2013-02-08
forum: Multimedia Software
---

### Post by Macamba on 2013-02-08
Hi,

I want to view video files with the extension wmv. MPlayer and VLC media player show only a black screen. No luck. I tried it on Windows XP too, and found out that VLC media player did not work there either. Strangely enough, WMA Player showed the video. 

Anyway, VLC media player gave me the following information:
[IMG]http://oi49.tinypic.com/dre2rr.jpg[/IMG]
So, the codec should be 'Windows Media Video Advanced Profile'. **What do I need to do to be able to view this type of videos?**

I already installed [Medibunti]("https://help.ubuntu.com/community/Medibuntu") 

FWIW:
```

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

```

TIA,
Macamba

---

### Post by ron999 on 2013-02-08
> **Macamba said:**
> **What do I need to do to be able to view this type of videos?**

Hi
Try using MPlayer with commands like this:-

```
mplayer filename.wmv
```
Or this:-
```
mplayer -vfm dmo filename.wmv
```
Or this:-
```
mplayer -vfm ffmpeg filename.wmv
```

---

### Post by Macamba on 2013-02-08
Thanks for your input. I got:
```

A:   7.1 V:   7.2 A-V: -0.051 ct: -0.188  56/ 56  0%  0%  2.1% 0 0 
[vc1 @ 0x7f67f8c07380]Error in WVC1 interlaced frame
Error while decoding frame!

```
ad infinitum.

---

### Post by evilsoup on 2013-02-08
If neither VLC nor Mplayer can play the files, but Windows Media Player can, there's a pretty strong chance that you're coming up against DRM within the WMV file.

---

### Post by Macamba on 2013-02-08
> **evilsoup said:**
> If neither VLC nor Mplayer can play the files, but Windows Media Player can, there's a pretty strong chance that you're coming up against DRM within the WMV file.

Well. I actually never installed Windows Media Player. I played it in WMA Player, which I use to listen to my mp3's. 

DRM is a whole new ball game. Searching on DRM removal under Ubuntu gave me no joy (at the moment). So does someone else have solutions?

---

### Post by ron999 on 2013-02-08
> **Macamba said:**
> ... So does someone else have solutions?
Upload a sample file somewhere.

---

### Post by mc4man on 2013-02-08
> **Macamba said:**
>  So does someone else have solutions?
As ron999 mentioned try with mplayer. If using dmo then you'd need to be on a 32 bit install with w32codecs installed.
(or running a standalone 32 bit mplayer

There are some vc1 encoded files that vlc has issue decoding thru avcodec, as far as vlc with a dmo decoder again only on a 32 bit install & vlc has to be built with dmo enabled.

---

### Post by andrew.46 on 2013-02-08
> **ron999 said:**
> Upload a sample file somewhere.

A good spot would be here:

[http://www.datafilehost.com/](http://www.datafilehost.com/)

---

### Post by Yellow Pasque on 2013-02-11
I once had a stubborn WMA lossless audio file that wouldn't play in Linux. I had to boot to windows and convert the thing (and that's probably your best option too).

---

### Post by Zteam on 2013-02-13
I belive this wmv-files is encrypted with DRM if so, tru to install windows media player with wine and see if that helps you.

---

