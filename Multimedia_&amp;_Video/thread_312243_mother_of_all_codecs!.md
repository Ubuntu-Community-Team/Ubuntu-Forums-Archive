---
title: "mother of all codecs!"
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by rkakkar on 2006-12-04
hey all.. i found the mother of all codecs here:

[http://www.codecguide.com/download_mega.htm](http://www.codecguide.com/download_mega.htm)

unfortunately its windows only!! ](*,) 

anyone can please tell me if there is a way to integrate these codecs into MPlayer?

---

### Post by nalmeth on 2006-12-04
Except for WM9 (I think) and DRM files, which klite doesn't support, it's all available here:
[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

Or automatix/easyubuntu/bumps/yadayada for an automated way.

I've heard that soon gstreamer is supposed to natively support wmv9, anyone know anything about this?
EDIT: I mean future release

---

### Post by rkakkar on 2006-12-04
i seriously doubt the codec pack you mentioned supports all these codecs:

ffdshow:

    * ffdshow [rev. 571]
    * extra plugins
    * ffdshow VFW interface

DirectShow video filters:

    * XviD [version 1.2.0-dev build 2006-11-08]
    * DivX [version 6.2.5.34]
    * On2 VP6 [version 6.4.2.0]
    * On2 VP7 [version 7.0.10.0]
    * MPEG-1 / MPEG-2 (Cyberlink) [version 6.0.0.3402]
    * MPEG-1 / MPEG-2 (InterVideo) [version 7.0.27.191]
    * MPEG-1 / MPEG-2 (DScaler5) [version 0.0.8.0]
    * MPEG-1 / MPEG-2 (Gabest) [version 1.0.0.3]
    * MPEG-1 / MPEG-2 (MainConcept) [version 1.0.0.78]
    * MPEG-1 / MPEG-2 (Ligos) [version 4.0.0.77]

VFW video codecs:

    * XviD [version 1.2.0-dev build 2006-11-08]
    * DivX Pro [version 6.4.0.51]
    * x264 [rev. 578]
    * Windows Media 9 VCM [version 9.0.1.369]
    * On2 VP6 [version 6.4.2.0] [Encoding]
    * On2 VP7 [version 7.0.10.0] [Encoding]
    * Intel Indeo [version 5.2562.15.54]
    * Intel Indeo [version 4.51.16.2]
    * Intel Indeo [version 3.24.15.03]
    * Intel I.263 [version 2.55.1.16]
    * huffyuv [version 2.1.1 CCE Patch 0.2.5]
    * I420 (Helix) [version 1.2]
    * YV12 (Helix) [version 1.2]

QuickTime Alternative:

    * QuickTime codecs [version 7.1.3.100]
    * QuickTime plugin for Internet Explorer
    * QuickTime plugin for Firefox/Mozilla/Netscape/Opera
    * Extra QuickTime plugins
    * QuickTime DirectShow parser
    * QuickTime DirectShow decoder wrapper

Real Alternative:

    * RealMedia codecs [version 6.0.12.1741]
    * RealMedia plugin for Internet Explorer
    * RealMedia plugin for Firefox/Mozilla/Netscape/Opera
    * RealMedia DirectShow splitter [version 1.0.1.1]

DirectShow audio filters:

    * MP3 (Fraunhofer) [version 1.9.0.311]
    * AC3/DTS/LPCM (AC3Filter) [version 1.11]
    * AC3/DTS/LPCM (InterVideo) [version 7.0.27.191]
    * MP1/MP2 (MainConcept) [version 1.0.0.78]
    * Vorbis (CoreVorbis) [version 1.1.0.79]
    * AAC (CoreAAC) [version 1.2.0.575]
    * AAC (3ivX Pro) [version D4 4.5.1]
    * MusePack [version 1.0.0.3]
    * Monkey's Audio [version 1.00]
    * WavPack (CoreWavPack) [version 1.0.3]
    * FLAC (illiminable) [version 0.73.1936]
    * Voxware MetaSound [version 1.0.0.12]
    * AAC encoder (3ivX Pro) [version D4 4.5.1]

ACM audio codecs:

    * MP3 (Fraunhofer) [version 3.3.2]
    * MP3 (LAME) [version 3.97]
    * AC3 (ffcHandler) [version 1.3.1]
    * Vorbis [version 0.0.3.6]
    * DivX ;) Audio [version 4.2.0.0]

DirectShow source filters:

    * MP4 splitter (Haali Media Splitter) [version 1.6.338.23]
    * MP4 splitter (Gabest) [version 1.0.0.3]
    * Matroska splitter (Haali Media Splitter) [version 1.6.338.23]
    * Matroska splitter (Gabest) [version 1.0.2.9]
    * Ogg splitter (Haali Media Splitter) [version 1.6.338.23]
    * FLV splitter (Gabest) [version 1.0.0.1]
    * MPEG-TS splitter (Haali Media Splitter) [version 1.6.338.23]
    * MPEG demuxer (Cyberlink) [version 1.0.0.4528]
    * MPEG demuxer (Gabest) [version 1.0.0.3]
    * MPEG demuxer (MainConcept) [version 1.0.1.20]
    * MPEG demuxer (Elecard) [version 1.0.31.51211]
    * MP3 Source (DCoder) [version 1.3]
    * SHOUTcast Source [version 1.0.0.1]

DirectShow subtitle filter:

    * DirectVobSub (a.k.a. VSFilter) [version 2.37]
    * DirectVobSub (a.k.a. VSFilter) [version 2.33]

DirectShow audio filters (general purpose):

    * Morgan Multimedia Stream Switcher [version 0.9.9]

I know this because after installing this pack in windows.. some of my videos which weren't working in Ubuntu ran in windows media player because of the availability of the codec.

---

### Post by Hairy_Palms on 2006-12-04
nope, other than wmv9 im sure ubuntu can play all those things on mine, cant be sure about the realmedia files, coz i dont have any, but seeing as their is a realplayer for linux id bet they can.

---

### Post by true_friend on 2006-12-04
yup rm files can be played.

---

### Post by an.echte.trilingue on 2006-12-04
Just out of curiosity, what kind of files can't you play on Ubuntu, excluding wmv9?

---

### Post by true_friend on 2006-12-06
i did not experienced any file not to be played. may be quicktime files.....
but usuaul media, music, movie files are played correctly after codecs installation. i install them from Automatix

---

### Post by weiersc on 2006-12-14
I'm having trouble with the VP7 codec?

How can I get that to work in ubuntu?

Thanks

Weiers

---

### Post by mcduck on 2006-12-14
Windows codec packs are probably the work of the Devil. One of the easiest ways to mess your system and get spyware & viruses :D

Anyway, follow the instructions in the Restricted Formats page and you'll be able to play about anything. I haven't yet found a video/music file I couldn't play.

If you are still using Windows too, get VLC media player. It includes it's own codecs and plays anything you throw at it :)

---

### Post by drphilngood on 2006-12-14
> **mcduck said:**
> Windows codec packs are probably the work of the Devil....

I had to clean the coffee off my LCD after reading this; hilarious!:D

I do agree that the OP should probably leave these alone, though.

---

