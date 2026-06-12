---
title: "What shouold firefox mp3, ogg, ets plugins do?"
date: 2011-01-09
forum: Multimedia Software
---

### Post by pnguine on 2011-01-09
I suppose this is probably a pretty lame question but as the topic indicates I am not sure what multi-media plugins are supposed to do. I say this because I assumed that a properly installed and functioning plugin (mozilla-plugin-vlc specifically) would preclude the necessity of redirecting the stream to an external program such as Banshee. Am I wrong? No matter what I do, whenever I try to listen to Absolute Radio (whatever stream format) Firefox wants to open another app (Media Player, Banshee, whatever) and I was hoping that it wouldn't do that. It does this whether I have a plugin or not so that is why I am wondering if I have the wrong idea about what plugins are there for. If anyone could enlighten me as to the truth of the matter I would be really appreciative as it's really starting to get up my nose. Thanks.

---

### Post by lovinglinux on 2011-01-10
Each plugin is capable of playing a limited set of media formats. When Firefox detects the plugin cannot handle the format, it asks which standalone player you wan to use.

The real problem is that mozilla-plugin-vlc is not the best plugin available. You should remove mozilla-plugin-vlc and totem-mozilla, if you have installed it, and install gecko-mediaplayer.

Follow the tutorial below and you will be able to play almost everything:

[Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by pnguine on 2011-01-20
Thank you. I will try that soon and return with my results.

---

