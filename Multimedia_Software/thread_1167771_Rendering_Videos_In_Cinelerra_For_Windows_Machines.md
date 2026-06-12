---
title: "Rendering Videos In Cinelerra For Windows Machines"
date: 2009-05-23
forum: Multimedia Software
---

### Post by umechanism on 2009-05-23
I've created a video in Cinelerra and want to render it to a format that can be played on any Windows based computer.  I've tried .AVI which rendered but will not play on a Windows computer.  What format should I render to?  Also, Does the base install of Cinelerra come with all the codecs I need to do this?

Thanks!!

---

### Post by labinnsw on 2009-05-23
.wav should be the default windows file but it should be able to read other types including .avi

---

### Post by bobince on 2009-05-23
The selection of codecs included with a vanilla install of Windows is very limited, for both licensing and political reasons. If you can't persuade the user to install a codec, and you can't rely on any of the common codecs (Xvid/DivX, MPEG-4 AVC etc.) being installed, the only usable options are:

* Windows Media [WMV video+WMA audio in ASF container, .wmv]
* MPEG-1 [MPEG-1 video+MP3 audio in MPEG Program Stream container, .mpeg]

I'm not sure what codecs Cinelerra gives you. Possibly MPEG-1, though that's an old and somewhat inefficient format which is limited in its resolution. WMV, probably not. You could export video in the least-lossy format available (MJPEG? DV?) then use ffmpeg to convert to WMV (“-vcodec wmv2 -acodec wmav2”, or use a front-end such as winff).

---

### Post by umechanism on 2009-05-23
> **bobince said:**
> The selection of codecs included with a vanilla install of Windows is very limited, for both licensing and political reasons. If you can't persuade the user to install a codec, and you can't rely on any of the common codecs (Xvid/DivX, MPEG-4 AVC etc.) being installed, the only usable options are:

* Windows Media [WMV video+WMA audio in ASF container, .wmv]
* MPEG-1 [MPEG-1 video+MP3 audio in MPEG Program Stream container, .mpeg]

I'm not sure what codecs Cinelerra gives you. Possibly MPEG-1, though that's an old and somewhat inefficient format which is limited in its resolution. WMV, probably not. You could export video in the least-lossy format available (MJPEG? DV?) then use ffmpeg to convert to WMV (“-vcodec wmv2 -acodec wmav2”, or use a front-end such as winff).

I have attached two images of the export options that I am given when rendering.  I'm a video noob so I'm not sure which one is best but I want to share this video with a Windows user.  I do have Winff installed along with Kino and Kdenlive.

Thanks for your help.

---

### Post by bobince on 2009-05-29
Yeah, the only plausible formats I can see in there are:

* MPEG (would have to be MPEG-1; relatively poor compression; limited resolution)
* AVI (would have to be DV-in-AVI, assuming that's offered; full resolution only, minimal compression)

---

### Post by umechanism on 2009-05-29
Actually, I used .MP4 which worked great!  9 out of 10 Windows machines have iTunes on them and, if so, they can play .MP4 file formats.  I'll use .MP4 for now.

However, I would like to know if there are additional codecs that I can download for Cinelerra and, if so, where do I find them?

Thanks!

---

### Post by kelvin spratt on 2009-05-29
VLC for windows will play all Linux formats I find rendering video4linux is the best format for rendering in Cinelerra for normal use.
winff is a very good straight linux converter that I use to convert dodgy formats before editing with Cinelerra.

---

### Post by umechanism on 2009-05-29
The problem I have with VLC is that not all my Windows-using-noob family members know anything about VLC and struggle even with Windows medial players.  I'm sure you know what I'm talking about.  Whatever I render must work with the native Windows install or, at least, iTunes.

---

### Post by brousch on 2009-11-09
> **umechanism said:**
> Actually, I used .MP4 which worked great!  9 out of 10 Windows machines have iTunes on them and, if so, they can play .MP4 file formats.  I'll use .MP4 for now.


Which of the options produced a usable MP4 for you?

---

