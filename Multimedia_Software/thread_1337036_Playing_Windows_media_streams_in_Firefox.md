---
title: "Playing Windows media streams in Firefox"
date: 2009-11-25
forum: Multimedia Software
---

### Post by bablo on 2009-11-25
To be able to play WMP video streams in Firefox, I've installed the mplayerplug-in 3.55. What I don't understand however is how I link this plugin to the WMP streaming formats:
video/x-ms-asf
application/asx Microsoft ASX playlist
 
In Firefox I can go to Tools > Applications, but for these mimetypes I can only select "Windows Media Player Plugin", not the "mplayerplug-in 3.55 Plugin" that I'd like to use. The mplayerplug-in is however (succesfully) linked to all kinds of other formats, like MPEG-4 and DivX.
 
And now the strange thing is:
A lot of WMP like streams open up in some Totem plugin, which doesn't work, while others open up in mplayer and run just fine. Usually the stream URLs starting with "mms://" work fine, while streams like "http://.../stream.asx" won't work. E.g. most of the streams from [http://nl.wwitv.com/](http://nl.wwitv.com/) won't open in Firefox.
 
Anyone got an idea what I'm doing wrong? I'm guessing I'm missing some essential and fundamental piece of info on Firefox plugins, WMP codecs and/or video streaming.

---

### Post by wilee-nilee on 2009-11-25
Your first link is dead but I was able to play tv on the second. Install the restricted extras in synaptic. You might also get the medibuntu package.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
I also have vlc and smplayer installed so there may be more added codecs along with these packages.
You also may need to go inti FF preferences applications, and make sure whatever media type it is is being played with the appropriate player. Not knowing which distribution your running the Ubuntu version of restricted
is ubuntu restricted extras kubuntu and xubuntu would be the OS in front of the restricted extras.

---

### Post by bablo on 2009-11-25
> **wilee-nilee said:**
> Your first link is dead but I was able to play tv on the second.
The first link wasn't really a link, but an (incomplete) example of a link that's not working in my Firefox.
 
> **wilee-nilee said:**
> Install the restricted extras in synaptic. You might also get the medibuntu package.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
I also have vlc and smplayer installed so there may be more added codecs along with these packages.
You're assuming I'm missing the right codec for these ASX streams, but I'm pretty sure the mplayerplug-in should be able to handle this format.
 
The problem is that when I go to Firefox > Tools > Applications and try to set the default plugin for this format, I can't select the mplayerplug-in, just the Windows Media Player Plugin, which results in a Totem player opening the ASX stream and unable to handle it.

---

