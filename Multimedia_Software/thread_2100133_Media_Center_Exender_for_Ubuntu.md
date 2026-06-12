---
title: "Media Center Exender for Ubuntu"
date: 2012-12-31
forum: Multimedia Software
---

### Post by Mythblstr on 2012-12-31
I am seriously thinking about weaning myself off Windows and into Ubuntu.. Does anyone know of a Media Center Extender that can connect to Ubuntu and play the files that I have on NTFS partitions. I currently have an XBox360 but let my script to XBox live expire because I'm not going to pay Microsoft their extortion fee just to watch Netflix. I'm going to get a new Media Extender that streams Netflix but I want one that can connect to Linux operating systems...
Anyone know about this stuff????:popcorn:

---

### Post by sdowney717 on 2012-12-31
Do you mean a DLNA server?
There is minidlna and rygel which work well.
minidlna runs as a service, and rygel from the commandline, which you can set to autostart at boot.

Netflix now works on Ubuntu using a special form of wine.

---

### Post by Mythblstr on 2012-12-31
I'm talking about a receiver that can connet to my TV through an HDMI cable that can connect to Ubuntu through Ethernet and see .avi, mp4 and .mkv files on the NTFS partitions from my computer.

---

### Post by sdowney717 on 2012-12-31
I would just make a theater PC and connect it to the TV.
The TV just becomes a large monitor. Files I share across the LAN or copy to the local PC hooked to the TV.
That is what I did and I dropped cable and satellite and now just use internet for TV and antenna for local. 

I dont know what your gaining doing something else except perhaps the cost.

---

### Post by Mythblstr on 2012-12-31
The PC I have that has 4TB worth of video is in a different room. I have an HDMI sound system attached to the TV. I will get a WD Live (that's a Western Digital Media Extender) and just watch the files from a USB flash drive if I have to. I only have basic Dish with local channels and need to be able to play downloaded files to my TV. I've been using my XBox360. You have to pay for Xbox Live to stream Netflix to it which is kind of ridiculous to me. That's why I going to buy a different Media Extender that plays files from my computer and also streams Netflix and a ton of other things like Hulu....
I just wanted to know if anyone has experience with one that can connect to the linux OS...

---

### Post by nhtrader on 2013-01-11
> **Mythblstr said:**
> The PC I have that has 4TB worth of video is in a different room. I have an HDMI sound system attached to the TV. I will get a WD Live (that's a Western Digital Media Extender) and just watch the files from a USB flash drive if I have to. I only have basic Dish with local channels and need to be able to play downloaded files to my TV. I've been using my XBox360. You have to pay for Xbox Live to stream Netflix to it which is kind of ridiculous to me. That's why I going to buy a different Media Extender that plays files from my computer and also streams Netflix and a ton of other things like Hulu....
I just wanted to know if anyone has experience with one that can connect to the linux OS...

As you stated you're planning on getting WD HD LIVE. Get it. It works as advertised.

I have set up an older PC to run MythTV (ubuntu based media server) and it works very well with WD HD LIVE.

I also have external HDDs with media content and I also have a Netflix account. 

So it sounds as if we are doing almost the same thing. And so I can tell you the WD HD Live will access your Netflix account. It will play media content from your HDD (IMHO, it handles the most formats out of all media players. The ones you need. However there's one notable omission - Windows WTV format. But this is proprietary, so not WD's fault. You'll need XBOX only for Win Media Center Recordings.)

Product Spec: [http://wdc.com/en/products/products.aspx?id=330]("http://wdc.com/en/products/products.aspx?id=330")

It works flawlessly with MythTV's built in UPnP server.

Connections:
I take the HDMI out from WD and plug the other end into my receiver's HDMI in.
I plug in an external HDD into WD using standard USB A/B cable.
I plug in an ethernet cable into WD in which the other end plugs into a Network Switch.

Turn it on and it finds everything on its own. It really works great.

And I can add that this week a bought another device which was only another disappointment. I thought would be great to use elsewhere in the house, but its weakness is that it only supports three media formats: MP3, MPG, MP4. This isn't enough. So once again I tried another media player only to discover that it is only capable of playing/streaming what I call "re-pay for" content. The value of WD HD Live is that it lets you play your "already paid for" content.

And if you're thinking what I was thinking when I was at your stage of Home Theater development. Let me clue you in on something. If you decide to go to the next level, streaming your content to yourself anywhere in the world. You should consider using MythTV and one of its features MythWeb (your personal web/media server to the world from your own home). 

Yes, I can stream my media content to my hotel's TV using my laptop. (BTW, I added a TV tuner to allow MythTV to record TV shows, which of course can be streamed as well. Plus, I can select which TV shows to record and watch from my Hotel.)
 
How about that!

---

### Post by dannyboy79 on 2013-01-11
i personally run an original apple tv version 1 and I installed crystalbuntu on it. it can playback 1080p content with the broadcom crystal hd decoder card. without it, it can still play 1080i content.

since netflix can be installed in ubuntu with wine, i am sure you could create a xbmc app launcher that would launch the wine netflix BUT I am totally guessing and I have no idea. I don't use netflix, I personally don't even feel the $7 or $15 is even worth what they have to offer.

---

