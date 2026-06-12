---
title: "Play Flash Stream from internet in standalone player"
date: 2009-09-11
forum: Multimedia Software
---

### Post by brotakul on 2009-09-11
Hi.

I'm watching a lot of Live TV and news online, from the national tv stations. They use embedded flash to steam videos, just like YouTube. And i don't want to depend on the browser to watch them, so i'm looking for some way to play those streams in a standalone player which i could resize, minimize, etc.
The problem is that i can't even find the url to these streams from the sites, or i just don't know how.

For WMV streams i used to use "mediaplayerconnectivity" plugin for firefox, but this is flash and it's different.

So, any suggestion might help.
Thanks.

---

### Post by Labello on 2009-09-11
I am not really shure if this is what you want, but you can do the following:

open firefox, with the page that displays the stream, and let it buffer a bit the clip.

now open up you filebrowser and look into the directory /tmp

there should be a flashfile, that can be played by movieplayer or vlc. it should even use less CPU cycles since the use accelerated video-output to display the clip.

---

