---
title: "Cannot play MMS after installing Edgy"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by nlippincott on 2006-12-24
I am hoping that someone can tell me what I need to install in order to play the audio stream from this page on Edgy:
[http://www.pennspeakradio.com/Player_Window_3.php](http://www.pennspeakradio.com/Player_Window_3.php)

I had this working fine on Dapper. On my latest Dapper install, I used Automatix to install 'Multimedia Codecs' and 'MPlayer and FF Plugin'. This seemed to be sufficient to play this audio stream. But installing the same packages on Edgy, I try to play this audio stream and I get:

Totem could not play 'mms://a111.l3072827569.c30728.g.lm.akamaistream.net/D/111/30728/v0001/reflector:27569?auth=caEaWboacbxd.dgbzbibMbtcdcicEdycscu-bfJOxh-kJa-EoCCFxq=0001'.
There is no input plugin to handle the location of this movie

I should also note that after installing 'MPlayer and FF Plugin', Firefox still seems to use Totem. That was not the case with Dapper.

I have had trouble with media on other sites too, not just the URL listed above. But I think if I can find the missing piece of the puzzle for this one, others (including online listening at sirius.com) will work as well.

Any help on this will be much appreciated.

](*,)

---

### Post by PurplePenguin on 2006-12-24
VLC seems to work with everything... totem seems hit and miss (depending on whether gstreamer or xine is the engine behind it).

You should be able to copy this url and paste it into VLC (there's a field for MMS streams).

This probably isn't the best fix, but hopefully should let you listen to audio streams in the meantime - somebody else should pop by soon with a true solution to your problem! :)

---

### Post by nlippincott on 2006-12-24
Thanks for that reply, PurplePenguin. VLC plays that audio stream just fine - after I looked at the HTML source for the web page and found the HTTP address they were using.

Albeit not a "true solution" as you say, it does get me back listening to my favorite Internet radio station, and holds off my urge to dump Edgy and go back to Dapper.

I think that, even after I find a true solution to this problem, I'll continue to use VLC for this stream. I won't have to keep the web browser active to listen. And further, when Firefox crashes, it won't interrupt my audio stream. I've already added a launcher in my panel to bring up VLC and go directly to this stream. Nonetheless, I'd still like to get things working in Firefox so that I can enjoy other online media.

Thanks again.

---

### Post by PurplePenguin on 2006-12-24
I think I'm one of the lucky ones who got it all right the first time around (in terms of getting multimedia set up via a how-to for beginners), so I didn't learn a thing. :)

The next time you need a half-arsed band-aid solution to a problem, though, just shout! ;)

---

