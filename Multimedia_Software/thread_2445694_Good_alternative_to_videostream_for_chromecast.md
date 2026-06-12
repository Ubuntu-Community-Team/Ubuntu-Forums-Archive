---
title: "Good alternative to videostream for chromecast"
date: 2020-06-18
forum: Multimedia Software
---

### Post by crip720 on 2020-06-18
Have been using videostream for a few years and find it works very well, pick a local video file and it plays on chromecast right away, does not seem to matter which video format.  Chrome is going to disable apps soon, but videostream only has desktop app for Windows and Mac.  Was wondering if there is another program that works as well?  Have tried VLC and gnomecast so far, but VLC seems to take for ever to convert and Gnomecast uses extreme resources to convert with an I7 cpu and 16GBs of ram.  

Is there another program that works for casting local videos with a different formats(avi, h-264, mp4, mkv) as well as videostream?

---

### Post by TheFu on 2020-06-18
Plex Media Server will transcode videos based on the renderer's capabilities. It is free, but not F/LOSS.  There's minidlna, but you'd need to transcode any files do the format supported by the highly, highly, limited Chromecast.  webm should be safe.

To transcode manually, this will work:
```
   nice ffmpeg -i "$1" "$1.webm"
```
With additional options, we can get exactly the quality of transcode for our viewing hardware. For example, there's little point in transcoding with more than 720p resolution to watch on 40 inch or smaller TV.  Those would just be wasted pixel and processing time.

---

### Post by SeijiSensei on 2020-06-18
If you have an Android phone, you can use minidlna as a DLNA server, then retrieve the videos with [BubbleUPnP]("https://bubbleupnp.en.uptodown.com/android") app and view them with [MXPlayer]("https://play.google.com/store/apps/details?id=com.mxtech.videoplayer.ad&hl=en_US").  You can cast to Chromecast from MXPlayer.  MXPlayer supports pretty much any format I throw at it.

Have you tried playing the video in Chrome then casting the tab to the TV?

Chromecast is a licensed proprietary technology so it isn't widely supported by open-source applications.

To configure minidlna, you just need to edit /etc/minidlna.conf and change these lines to fit your needs:
```

media_dir=V,/path/to/video/directory
media_dir=A,/path/to/music/directory
media_dir=P,/path/to/photos/directory

```
You can have multiple entries for any of these options by simply adding another line with the correct path.

Some modern TVs come with a built-in DLNA client, though support for subtitled videos and some formats like Matroska (".mkv") can be spotty.  Sony, ever carrying the torch for proprietary systems, makes TVs that barf at pretty much anything other than .mp4 containers and a limited range of codecs like AAC.  My Roku stick has a decent DLNA player, though it displays the subtitles using the closed-captioning feature rather that showing the formatted subtitles in most shows I watch.

Usually I just watch my videos over the network (using NFS) on an old laptop running Ubuntu connected to one of the TV's HDMI ports.

---

### Post by crip720 on 2020-06-18
Chrome does not seem to want to play videos from local, even mp4(will list it,not play).  No android phone, but really would like a Ubuntu desktop answer.  Don't think my TVs have DLNA, cheap RCA models that work, 720s and one 50 inch 4k(happy with 720).  Do have an older android tablet(4.4 or 5), but not sure if I could just connect my external hard drive to it(does have USB port) without quite a bit of work to play videos.

---

### Post by TheFu on 2020-06-18
> **crip720 said:**
> Chrome does not seem to want to play videos from local, even mp4(will list it,not play).  No android phone, but really would like a Ubuntu desktop answer.  Don't think my TVs have DLNA, cheap RCA models that work, 720s and one 50 inch 4k(happy with 720).  Do have an older android tablet(4.4 or 5), but not sure if I could just connect my external hard drive to it(does have USB port) without quite a bit of work to play videos.

A chromecast is a "DLNA Renderer".
You need a "DLNA Server" and a "DLNA Controller". These can be the same or different machines.  Old Android should be fine as any of those and BubbleUPnP can provide the Server and Controller or just be the controller.  It is really pretty slick.

So ... what I think  SeijiSensei and I are saying is similar stuff.
[LIST]
[*]DLNA Server - miniDLNA or Plex or Windows Media Center or whatever you like .... there are options for every OS. My HD-Homerun TV Tuners are DLNA Servers. So is an old TP-Link router that I'll never allow on the internet due to other security failures in that machine.
[*]DLNA Controller - BubbleUPnP or Roku and probably 20 others.
[*]DLNA Renderer - Chromecast, VLC, Roku, BubbleUPnP, XBMC, Kodi, and probably 50 others.
[/LIST]

I use VLC on Android as the Controller and Renderer for local playback.
I use VLC on Ubuntu as the Controller and Renderer for local playback on a desktop.

I use BubbleUPnP on Android (tablet or phone) to send content at different devices - chromecast, Roku, Kodi, Raspberry Pi running Kodi, or locally to any player that can accept HTTP URLs (mxplayer, vlc, etc...)

I don't know how to have any Linux desktop as the DLNA Controller.  
[LIST]
[*]Servers - yes!  
[*]Controllers+Renderers - yes!  
[*]But no DLNA-Controller-only solution. Sorry.  
[/LIST]
Some DLNA web interfaces have a "Play-To" option which really tells the DLNA Server where to send stuff, but support for that is extremely limited. I've never gotten it working even with browser addons for Plex. That could be simply because I refuse to sign up for a free Plex account and block almost all Plex internet requests.

It really does seem like an easy thing to want.

BTW, file extensions don't equate to any specific video or audio encoding.  .mp4 is just a container with many different video-codecs and audio-codecs possible.  A Chromecast has some very specific ideas about what it can play. I have a very early v1 Chromecast and it wouldn't play any mpeg2 video or AC3 audio - which is what TV broadcast do here. Basically, it could play h.264 video and either ogg, mp3 or aac audio, nothing else. I've recently learned that newer chromecasts support some other audio formats, but not FLAC.

Because I was tired of having to fight for reasonable video support, I got a raspberry pi v3 and loaded OSMC onto it. OSMC is a customized version of Kodi designed specifically for stock r-pi systems.  A raspberry pi is ($35).  The v4 is out now for $35 (you'll need a case, PSU, and microSD too) and probably 2x faster than the v3.  The case + PSU should be under $15 total. The microSD just needs to have enough storage for the OS and KODI database, so 8G or 16G should be sufficient, unless you have thousands of videos. Get the official PSU. When people try to use some other PSU, it usually doesn't provide sufficient power and leads to odd failures that can never be uncovered. Just get the official PSU for the r-pi model you choose.
R-Pi CPUs are fast enough to handle CPU-based playback for 720p content of pretty much any type of video.  However, they have hardware support enabled for h.264 video decoding for hidef content, so the playback is next to zero CPU for that. Kodi can play from local attached storage or remote network storage (nfs or CIFS). It can access DLNA servers. It handles pretty much any audio file formats.  The r-pi v4 has 2 HDMI outputs and claims to support dual 4K output. 

We're getting beyond my knowledge at this point.

---

### Post by SeijiSensei on 2020-06-19
> **crip720 said:**
> Do have an older android tablet(4.4 or 5), but not sure if I could just connect my external hard drive to it(does have USB port) without quite a bit of work to play videos.
Don't know if you can connect your USB drive (my guess is no), but you could use the tablet via wifi in the same manner I described for using an Android phone.

---

### Post by crip720 on 2020-06-19
Tried going over to the dark side,  What a mess to set up an OS.  Was wondering if there is a way of freezing Chrome from updating or removing apps in future?  Only use Chrome to use videostream.  Have found most of your suggestions don't work as well or tend to try to burn up cpu.

---

### Post by TheFu on 2020-06-19
> **crip720 said:**
> Tried going over to the dark side,  What a load of c**p to set up an OS.  Was wondering if there is a way of freezing Chrome from updating or removing apps in future?  Only use Chrome to use videostream.  Have found most of your suggestions don't work as well or tend to try to burn up cpu.

Transcoding is always heavy on a CPU. Always.  There is literally, no way around that.

---

### Post by crip720 on 2020-06-19
Don't know how videostream does it, but it does not seem to use much cpu.  Have never heard my fans come on when using videostream.  With plex fans went to maximum and was not even trying to convert video, gnomecast had fans high converting/transcoding.  TVs are in other rooms and chromecast has been easier to use than moving computer or getting very long HDMI cable.

---

### Post by TheFu on 2020-06-19
> **crip720 said:**
> Don't know how videostream does it, but it does not seem to use much cpu.  Have never heard my fans come on when using videostream.  With plex fans went to maximum and was not even trying to convert video, gnomecast had fans high converting/transcoding.  TVs are in other rooms and chromecast has been easier to use than moving computer or getting very long HDMI cable.

On Windows, using the **GPU** for encoding of videos is mostly possible. 
On Linux, that capability isn't universal because the arms-length driver development for many GPU drivers.  I suspect much of this is due to fear by vendors that Linux people would crack any DRM and steal content must more than Windows [s]sh[/s] people.  But that's just a guess.

update: fix GPU where needed.

---

### Post by crip720 on 2020-06-19
Don't know how videostream does it, but it does not seem to use much cpu.  Have never heard my fans come on when using videostream.  With plex fans went to maximum and was not even trying to convert video, gnomecast had fans high converting/transcoding.  TVs are in other rooms and chromecast has been easier to use than moving computer or getting very long HDMI cable.

---

### Post by crip720 on 2020-06-20
Question, by unticking/removing the google chrome line in software sources, will that prevent/disable chrome from updating and/or removing apps during future updates?  I know it is bad to not update, but only use chrome for the videostream app.  Use firefox and/or opera for most browsing.

---

### Post by CelticWarrior on 2020-06-20
Removing the Goggle Chrome repository will prevent updates, of course, as that is the only source for those updates. Chromium OTOH comes from official sources.

---

### Post by durandot on 2021-02-03
[LEFT][COLOR=#000000][FONT=Arial]As far as I know, there are many alternatives to the video stream for chromecast. Personally, I use virgin multi room TV. This is a device, after connecting which, everyone in the house watches different shows at the same time, without interfering with each other. Fortunately, many channels are included in the package, so there are always interesting shows or movies. By the way, this is a useful device for those families and homes that have more than one TV. You can buy a virgin multi room here [https://xtrium.com/virgin-multi-room/](https://xtrium.com/virgin-multi-room/)  it is really very economical and we do not pay several different bills.[/FONT][/COLOR][/LEFT]

---

