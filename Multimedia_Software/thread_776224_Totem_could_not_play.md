---
title: "Totem could not play"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Sergiu on 2008-04-30
Hello .

Can't stream the [http://kab.tv/?item=2093](http://kab.tv/?item=2093) , i use totem-plugin-viewer 2.20.0, Browser Plugin using xine-lib version 1.1.10, Copyright © 2002-2006 Bastien Nocera .

When i open it with "Movie Player" it says: Totem could not play 'mms://vod.kab.tv/vod/rus/shag navstrechu/rus_o_rav_2007-07-26_shag-navstrechu_vospriyatie-realnosti_part-1_mast_cbr.wmv'

There is no input plugin to handle the location of this movie...

---

### Post by Sergiu on 2008-04-30
the media is just stopped , and don't ever want to start.

here is an image

[img]http://www.torrentsmd.com/imagestorage/719999_927.png[/img]

---

### Post by warp99 on 2008-04-30
> **Sergiu said:**
> Hello .

Can't stream the [http://kab.tv/?item=2093](http://kab.tv/?item=2093) , i use totem-plugin-viewer 2.20.0, Browser Plugin using xine-lib version 1.1.10, Copyright © 2002-2006 Bastien Nocera .

When i open it with "Movie Player" it says: Totem could not play 'mms://vod.kab.tv/vod/rus/shag navstrechu/rus_o_rav_2007-07-26_shag-navstrechu_vospriyatie-realnosti_part-1_mast_cbr.wmv'

There is no input plugin to handle the location of this movie...

It works fine with mplayer and the mozilla-mplayer plugins, so you can install that player if you like. You have to enable the multiverse repositories in Synaptic, then download and install mplayer and mozilla-mplayer. I would also suggest installing mplayer-skins since the default GUI for mplayer is kind of utilitarian. 

You also need to remove totem-gstreamer-firefox-plugin and/or the totem-mozilla plugin so the mplayer plugins can work. Mplayer is a much better player then Totem since you can capture streams at the command prompt and play many more file formats if you have the w32codecs package installed from [medibuntu.org.]("http://medibuntu.org/")

---

### Post by wayfarer51 on 2008-05-04
Let me say to start, my multimedia knowledge is minuscule.  That being said, I installed the mozilla-mplayer plugin.  It works for audio, but when I try a podcast from The Onion, I get (roughly and too fast to get it totally accurate) the following: 

download complete
buffering
mplayer: connection refused
connecting to server
stopped

I tried it at apple.com/trailers.  It played the first video (MOV) I tried, but each subsequent attempt got only the audio.

Does anyone know how I can fix this?

Thanks for your help.

Neill

---

