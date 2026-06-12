---
title: "Media Player to Play MP3 Streams?"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by psadams on 2007-10-18
I am using Ubuntu 7.10 & I'm trying to play online radio stations. I need a media player that can play MP3 streams. 

Last night I tried Rythmbox, Amarok, XMMS & XMMS2 & I couldn't get any of these to play these files. I installed all of these from Synaptic in Gutsy.

This is the site I'm trying to play stations from. [http://www.internode.on.net/radio/](http://www.internode.on.net/radio/)

The file format is *.m3u. I also tried playing *.pls files with each player & this didn't work either.

I remember being able to play these files using XMMS in Ubuntu 6.10. Have they removed the codecs from XMMS for these file formats? I install all of the plugins for XMMS that were listed in Synaptic.

Can anyone suggest a player that will play this format or do I need to install extra codecs?

Your help is much appreciated.

---

### Post by andreeh on 2007-10-19
If I remember correctly, you need two packs:

```
sudo apt-get install libxine1-codecs libxine1-ffmpeg
```

if you already got them, try reinstalling them with the --reinstall parameter. That did it for me.

---

