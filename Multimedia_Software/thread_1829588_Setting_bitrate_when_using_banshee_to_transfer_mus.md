---
title: "Setting bitrate when using banshee to transfer music to ipod"
date: 2011-08-20
forum: Multimedia Software
---

### Post by db579 on 2011-08-20
Hi, I'm using banshee to transfer a playlist of (mostly flac) music to my 5th gen 60gb video ipod. 

I assume banshee transcodes this to something the iPod can play but is there any way of setting what it transcodes to and at what bitrate? If not what are the defaults?

---

### Post by ritchiew on 2011-08-25
This was tagged as solved, but I see no answer, and I'm wondering it myself.

You mean like in iTunes, there's an option to compress files with high bitrate when you put them on an iPod? Because that's exactly what I'm trying to do, but it looks like Banshee is just throwing big files on my iPod.

Any suggestions?

---

### Post by db579 on 2011-08-25
Hi, yeah you can do the same thing on banshee the confusing bit is that banshee doesn't actually do it itself it has gstreamer do it and is just a frontend.

You need to install the appropriate gstreamer encoder which can be found in the software centre or with sudo apt-get install (I think it's the libmp3lame0 and lame packages that you need). One you have those installed plug your iPod in and right click it in banshee and click properties and you should have options to change what banshee puts on the iPod from .wav to mp3 from the drop down menu. Click edit and you can change the bitrate.

Hope that helps

---

### Post by ritchiew on 2011-08-25
Awesome! That menu is a little out of the way, but everything seems to be working great. Even has more options than iTunes.

For reference, the gstreamer/mp3 libraries I installed were

```
sudo aptitude install gstreamer0.10-lame lame libmp3lame0
```

Thanks again

---

### Post by ritchiew on 2011-08-26
Shoot, I should have done a test batch instead of syncing my whole library overnight.

My music library is mostly mp3s at 320kbps, and when I put them on my Ipod, I want them at some lower bitrate to fit them all. It looks like setting the conversion rates like you suggest only applies to stuff that isn't mp3 to start with. So all my larger mp3s are just thrown on my ipod, unconverted.

I know this seems like a minor detail, but I'm trying to put ~110gigs of music on an 80GB ipod....

---

