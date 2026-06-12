---
title: "Can't watch certain video types"
date: 2009-05-12
forum: Multimedia Software
---

### Post by Tribulation on 2009-05-12
I'm not sure what video types it is that I cannot watch, but when I go to sites like traileraddict I can't watch any of the trailers. I have no problems with youtube or anything though. I've installed everything I need to view them, I just helped a friend set up a new 9.04 install and he can watch them no problem, but I can't for some reason. Any ideas why?

---

### Post by Tribulation on 2009-05-14
I just removed all special effects and tried watching a video that previously refused to work. I watched a Nostalgia Critic video, and it loaded fine. I turned on Extra special effects again and it no longer felt like loading. Is there any known solution to this?

---

### Post by ranie on 2009-05-14
Since Ubuntu is based on free software some codecs is not installed.
If you try installing mplayer using system>Administration>Synaptic Package Manager

or go for vlc.

If I'm not mistaken M-player will search for codecs automatically when you try launch your videos.

---

### Post by Tribulation on 2009-05-14
That didn't work. Also, I found out that I no longer have sound in youtube videos. I found this thread [http://ubuntuforums.org/showthread.php?t=321048](http://ubuntuforums.org/showthread.php?t=321048) but when I open /etc/firefox/firefoxrc all I see is a blank document. Also, whenever I update my sources.list I get the message 

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B9F1C432AE74AE63
```

near the bottom. I have no idea why I'm having all these problems, Ubuntu has pretty much always worked perfectly for me before.

---

### Post by andrew.46 on 2009-05-14
Hi Tribulation,

> **Tribulation said:**
> I'm not sure what video types it is that I cannot watch, but when I go to sites like traileraddict I can't watch any of the trailers. I have no problems with youtube or anything though. I've installed everything I need to view them, I just helped a friend set up a new 9.04 install and he can watch them no problem, but I can't for some reason. Any ideas why?

One method to achieve this:

[LIST=1]
[*]Download a new copy of MPlayer from [RVM's PPA]("https://launchpad.net/~rvm/+archive/mplayer")
[*]Add the medibuntu repository [w32codecs]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu4_i386.deb")
[*]Install the MPlayer plugin from the Ubuntu repository
[/LIST]

Hopefully this will allow you to watch your videos.

Andrew

---

### Post by Tribulation on 2009-05-17
Thanks for the information. Sound is working in Youtube again for some reason. Unfortunately I still can't watch some videos. I can't watch any of the videos on Screw Attack.com for instance. They simply don't load.

---

