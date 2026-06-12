---
title: "Media Player Problems"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by Martygraw450 on 2008-02-04
Hi,

I am fairly new to Linux, but prior to this weekend I had everything working great. I don't know what happened, I didn't change any settings, or add any new programs or codecs, but for some reason, no media player I have will work. Armarok wont even start, Totem will open but I have to force quit after attempting to play anything. Rhythm box will play, but If I try to skip tracks It locks up. I have tried uninstalling these players and all related packages, and re installing them, Thinking something was possibly corrupt, but no change, still same problems. I am lost at what to try next, and this in driving me crazy, so any help would be appreciated.

Thanks

---

### Post by stooshbunutu on 2008-02-05
I use a good multi-media player that seems to play every fil;e extension I have found. It is VLC player, available throught the software channel or the [ubuntu packages website]("http://packages.ubuntu.com/gutsy/graphics/vlc").

Hope this helps you. :)

---

### Post by Martygraw450 on 2008-02-05
I tried VLC, banshee, junk, almost every media player I could find to see if they would work. Only Rhythmbox will start up, but you can't skip tracks, stop, or interact with it at all after I start playing a track, if I attempt to it locks up. All the others I have tried won't even start up. I don't think its a media player problem but a driver or possible desktop environment problem but I can't figure it out.

---

### Post by Martygraw450 on 2008-02-05
So far after doing some investigating today I found that the problem was with the ALSA sound "drivers" If I switch to OSS "drivers" it works fine. Ill keep investigating.

---

