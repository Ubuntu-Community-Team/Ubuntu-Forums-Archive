---
title: "Flash Player Picture Quality"
date: 2011-03-06
forum: Multimedia Software
---

### Post by user68 on 2011-03-06
I just installed 10.04 (32 bit) Desktop with Adobe Flash Player 10.2 and Mozilla plug-in on an HP laptop that has a Celeron 540 2.0Ghz CPU and Intel X3100 video card. I'm trying to watch a multi bitrate video stream in Firefox. Speedtest says I have 9MB download speed. When I start watching the video in Firefox the resolution is excellent then, after a second or two, the resolution reduces significantly to a blur. CPU is running at around 56%. Adobe settings are greyed out, so I can't test with/without hardware acceleration. I ran flash-aid but no difference.

Is there anyway to force flash to show the higher bitrate stream or to access the greyed out settings?

---

### Post by beew on 2011-03-06
Instead of trying to trouble shoot flash there are ways to watch Youtube without flash, and with better results too. You cam either install the flashvideoreplacer plugin for Firefox or install minitube. This way you don't need flash at all and in general they work better than flash, use a lot less CPU. 

If you want to try minitube, make sure you get version 1.4 from a PPA, the version in the Ubuntu repo is very outdated and broken.

---

### Post by user68 on 2011-03-06
Thanks beew, that sounds like a good suggestion. I wasn't aware of Flashvideoreplacer. I'm not sure of it makes any difference, but it's not Youtube videos that I'm watching. It's an H264 RTMP stream from a Wowza server that appears in my browser as flash in JW Player.  

I found this: [http://www.longtailvideo.com/players/](http://www.longtailvideo.com/players/)

I don't really understand what this all means, but will try experimenting with Flashvideoreplacer to see if I can improve the picture quality in the player.

---

### Post by user68 on 2011-03-06
This is interesting: I did a test watching the same stream from my Macbook Pro (Snow Leopard, Firefox) on the same network and found the picture quality was just as poor as the HP laptop (Ubuntu, Firefox). Watching the same stream on a different network with the Macbook Pro, 5MB ADSL, gave me a far better picture!

So it appears the network is the common factor in reducing the quality of my stream. The 5MB ADSL is better than the 9MB cable and it seems that the processor, graphics card and software are not factors.

Now I'm confused :confused:

---

### Post by beew on 2011-03-06
> **user68 said:**
> Thanks beew, that sounds like a good suggestion. I wasn't aware of Flashvideoreplacer. I'm not sure of it makes any difference, but it's not Youtube videos that I'm watching. It's an H264 RTMP stream from a Wowza server that appears in my browser as flash in JW Player.  

I found this: [http://www.longtailvideo.com/players/](http://www.longtailvideo.com/players/)

I don't really understand what this all means, but will try experimenting with Flashvideoreplacer to see if I can improve the picture quality in the player.


I am not sure flashvideoreplacer would work in your case because unfortunately it works only on several websites (Youtube being the most popular) You can see which ones are supported by clicking on the icon and there are a few websites listed. 

If you have any question you should post it in this thread as the developer is very helpful in answering questions.[URL="http://ubuntuforums.org/showthread.php?t=1487327"]
http://ubuntuforums.org/showthread.php?t=1487327[/URL]

---

