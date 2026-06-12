---
title: "how to get artist and track info to stream"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by drh2020 on 2006-06-09
I want to be able to listen to a streaming music radio station from firefox and have the artist/title show in the media stream. My test station is at [http://radioparadise.com](http://radioparadise.com) (mp3 at 192k)
So far I have gotten movie player/totem to work fine in firefox at radioparadise.com (mp3 192 stream). But the artist/track info does not get updated when the next song comes on. Is there a plugin or other player or configuration method I can use to keep the artist/track info up to date during a radio music stream?
Thanks!

ps - I used these helpful links to get my codecs, players, firefox plugins, etc very useful!!!

1) [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)  This totally ROCKS!!
2) [http://www.beginningubuntu.com/dapper_tips.html](http://www.beginningubuntu.com/dapper_tips.html) (tempoarily down)

---

### Post by drh2020 on 2006-06-09
As usual I fixeded my own problem before anybody else could reply ;) 

Anyway... Installing VLC and related packages satisfied what I was looking for, a great streaming audio player, a related VLC/mozilla plugin that actually worked with radioparadise.com's streams, and it actually shows the artist and track as it changes! (something taken for granted in most windows players like winamp, etc..)

Here is the history output from synaptic for the packages I installed along with VLC to get it all to work with firefox when I browse my favorite radio station radioparadise.com (mp3 at 192k)

Commit Log for Fri Jun  9 18:13:43 2006

Installed the following packages:
libdvbpsi4 (0.1.5-1)
libdvdnav4 (0.1.9-3)
libiso9660-4 (0.76-1ubuntu1)
libtar (1.2.11-4)
libvcdinfo0 (0.7.23-1ubuntu1)
libwxgtk2.6-0 (2.6.1.2ubuntu2)
libxosd2 (2.2.14-1.2ubuntu2)
mozilla-plugin-vlc (0.8.4.debian-1ubuntu6)
vlc (0.8.4.debian-1ubuntu6)
vlc-plugin-alsa (0.8.4.debian-1ubuntu6)
vlc-plugin-esd (0.8.4.debian-1ubuntu6)
wxvlc (0.8.4.debian-1ubuntu6)

---

