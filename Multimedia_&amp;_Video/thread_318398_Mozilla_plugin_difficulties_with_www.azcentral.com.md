---
title: "Mozilla plugin difficulties with www.azcentral.com"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by desertViking on 2006-12-13
Hi,

I'm using 6.10, and have followed the unofficial guide to add extra repositories, media codecs and flash plugins.  I've installed the mozilla plugin for VLC media player.

I can visit and watch clips on [www.cnn.com](www.cnn.com), no problems. 

However, I get nothing but a grey screen when I try to look at media published on [www.azcentral.com](www.azcentral.com).  It doesn't matter which clips I try.

I've also tried copying the URL and pasting it to oneof the media players, but its a mangled, Java name of some sort.  

Does anyone have advice to share?

---

### Post by ciscosurfer on 2006-12-13
I took a look at that site and I believe its an issue on their end, not ours.

But I could be wrong.

---

### Post by d3v1ant_0n3 on 2006-12-13
I randomly clicked on one of the video links on that site ('This week's high school sport preview') and selected 'Windows Media Player' as the player, and it worked fine (using mplayer plugin, firefox 2, flash 9 beta

---

### Post by ciscosurfer on 2006-12-13
> **d3v1ant_0n3 said:**
> I randomly clicked on one of the video links on that site ('This week's high school sport preview') and selected 'Windows Media Player' as the player, and it worked fine (using mplayer plugin, firefox 2, flash 9 betaI have those enabled as well but still can't view videos there.  What gives?

---

### Post by desertViking on 2006-12-13
I tried mplayer, too, using the MediaPlayerConnectivity add-on, but was getting the mangled Java script names.

I am wondering if it's because you're using Java 9.  I followed the instructions to install Flash 9 from the unofficial guide.  I'm wondering if I'm stuck on 7.  Is there a way to check?

---

### Post by drphilngood on 2006-12-14
> **d3v1ant_0n3 said:**
> I randomly clicked on one of the video links on that site ('This week's high school sport preview') and selected 'Windows Media Player' as the player, and it worked fine (using mplayer plugin, firefox 2, flash 9 beta

Exactly the same for me, right down to the same video.

---

### Post by desertViking on 2006-12-14
I have a workaround.

First, using "apt-get remove" I removed all repository plugins to start from scratch.  In my case I had to remove the plugin for xine and vlc.  One plug in at a time, thank-you.

I installed mozilla-mplayer, and navigated to azcentral.  Grabbed a video, and at least it connected.  But it got stuck in this perpetual connection mode, but would not play anything.  So I dropped back again to the MediaPlayerConnectivity tool from Mozilla and allowed it to select mplayer for everything.  

After some fiddling with video output, I can watch media this way on both azcentral and CNN.  It was a bit jerky so I enabled a 2048 cache for Mplayer (context menu, right mouse click over player controls).

This seems to have something to do with a relatively slow wireless card (b) that I am using. When I connect the laptop to a hardwire, the regular Mplayer plugin seems to work OK.

---

