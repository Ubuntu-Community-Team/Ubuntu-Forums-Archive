---
title: "VLC and WMV files not playing"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by Geekkit on 2007-12-30
Anyone know how to make FLV and WMV files under Gutsy viewable in Totem and show up as thumbnails? This all worked in Feisty but seems to be missing in Gutsy.

When I try certain WMV files with Totem I get:

Video codec 'DivX 5' is not handled. You might need to install additional plugins to be able to play some types of movies

---

### Post by Geekkit on 2007-12-30
Update:

Cannot play videos with the following CODECS:

'Windows Media Video 9'
 'Windows Media Video 7'
 'DivX 5'
'Sorenson Video 1' 
 'Cinepak'

I have the following installed:

Totem Xine
ffmpeg
ffmpeg codec library - Medibuntu package
software library for DV format digital video (runtime lib) 
library for reading and writing Quicktime files
the xine video/media player library, binary files
mpeg related plugins for libxine1
MPlayer's Movie Encoder

---

### Post by taurus on 2007-12-30
Try the ubuntu-restricted-extras package.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Geekkit on 2007-12-30
> **taurus said:**
> Try the ubuntu-restricted-extras package.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

Thanks for the reply but this is what the command line states after I do that:


ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So I already have that installed.

:confused:

---

### Post by Geekkit on 2007-12-30
So I guess playing FLV, MOV, and WMV under Ubuntu/Linux is gibbled then huh? I've found no hint in any forum/Web FAQ that states that this can be fixed. Is Windows the only OS that can do this?

---

### Post by Geekkit on 2007-12-31
EDIT:

Well apparently the problem fixed itself ... strange. An update kicked in (via auto updates) and FFMPEG, Totem and a few other applications updated themselves and now all types of media play and have thumbnails generated for them in Nautilus.

The following video types were not working but now are:
WMV
MOV
FLV

The following CODECs weren't working but now are:
Sorensen
Divx (any version)
MPEG 4
Windows Media (any version)
Cinepak

As for the thumbnails, I had to go into the ~./.thumbnails subdirectories and delete all the thumbnails.

I thought my old animation files were not going to be viewable in Ubuntu. I am happy this is fixed but I'd sure like to know why this happened. I had all the restricted drivers installed. I searched all last night on Google and found nothing pertaining to this. Oh well, at least it healed itself and fixed the problem.

---

