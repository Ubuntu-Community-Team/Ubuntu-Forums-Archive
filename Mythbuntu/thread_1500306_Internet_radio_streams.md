---
title: "Internet radio streams ?"
date: 2010-06-03
forum: Mythbuntu
---

### Post by laffinet on 2010-06-03
Hiya !

This isn't strictly a mythbuntu questions, but since it's related to my myth setup I though I post the question here.

Is there an easy, yet hopefully user friendly way to incorporate internet radio (as in streams from radio station websites) to a mythbuntu system ?

It doesn't have to be from inside mythtv, I'd be happy to have a separate application. However what I would like to have is the ability to at least control the volume via my existing IR remote.

Any ideas how this can be achieved ? Thanks.

---

### Post by ian dobson on 2010-06-03
Hi,

Have a look here:- [http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/2537-internet-radio-linux.html](http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/2537-internet-radio-linux.html)

It shouldn't be too hard to integrate the audio player you use into mythtv, you just need to edit the xml menu config file. The program you decide to use for playback just needs to support lirc (most do), or they can be got to work.

Regards
Ian Dobson

---

### Post by Akumuumy on 2010-06-03
VLC player internet radio.
Install VLC player:
apt-get install vlc

start vlc.
go to Media> Services Discovery> Shoutcast Radio Listings

Then go to View> Playlist> Shoutcast radio listings
Choose your music genre and a radio station.

Have fun.

---

### Post by williammanda on 2010-06-03
From what I'm seeing offered here....Boxee would be an option.

---

### Post by laffinet on 2010-06-03
Who would have thought it would be so easy ?

The solution was xbmc, which I already run for all my movies, videos etc.

[This wiki entry ]("http://wiki.xbmc.org/index.php?title=HOW-TO_play_internet_video_and_audio_streams")explains it all, took me 5 min to set it up, works like a charm.

---

