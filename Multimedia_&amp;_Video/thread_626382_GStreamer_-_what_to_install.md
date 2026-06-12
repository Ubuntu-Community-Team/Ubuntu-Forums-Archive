---
title: "GStreamer - what to install?"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by dcas1 on 2007-11-29
Hi,
I want to listen to internet streaming radio and podcasts, and watch the odd video - what GStreamer components should I install? Some are listed "bad" "base" "good" - what does that mean? Wil I mess up the system if I install "bad"? Should I install Mplayer instead?
Denis

---

### Post by erfahren on 2007-11-29
first of all, I've personally had better luck with vlc and the mozilla-vlc-plugin
and I uninstall the totem-mozilla plugin (although I don't know if that's necessary)

but I do install the gstreamer plugins for totem to play some videos I have offline (humorous ones, not porn - lol !)

Anyway, the ones I get are listed here: [https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)
(that's Ubuntu 7.04 documentation, but I'm sure it's still applicable) 

I also get the w32codecs

To be honest, I'm still somewhat confused about all of that myself. There's alot of documentation I've found concerning online streaming video, but I don't think any of it really says "this works the best" in so many words.
some links I have:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo](https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
[https://help.ubuntu.com/7.04/musicvideophotos/C/onlinemedia.html](https://help.ubuntu.com/7.04/musicvideophotos/C/onlinemedia.html)

I've tried totem and mplayer for online video, but again, I've seemed to have the best luck with vlc.

-- probably wasn't much help, was it? - lol !

---

### Post by mdpalow on 2007-11-29
Hi Denis,

Visit links below in my signature for help.

---

### Post by koleoptero on 2007-11-29
The bad and the ugly plugins won't do anything to harm your system. But there is a better solution to this. Open synaptic and search for the packet ubuntu-restricted-extras and it will install all the codecs and plugins including flash, java, fonts, etc.

---

