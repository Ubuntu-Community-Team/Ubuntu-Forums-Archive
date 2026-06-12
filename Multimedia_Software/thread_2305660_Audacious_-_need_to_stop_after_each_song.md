---
title: "Audacious - need to stop after each song"
date: 2015-12-08
forum: Multimedia Software
---

### Post by Jan_Erik on 2015-12-08
I am considering using Ubuntu for a live show and I want to set up the playback list for the show. I then need a player that stops after each song so that each new song needs to be manually started. In Audacious there is an option to "Stop after this song". This is basically what I need but I need the value to retain. I.e setting this in the meny only is valid for the current song and then the application reset it to normal playback. Is there some way I can set Audacious to retain this value or alternatively is there another application that will be better for me to use? Thanks!

---

### Post by howefield on 2015-12-08
Can't answer for Audacious but you might get VLC to do what you need.

From the VLC > Tools > Preferences > Show Advanced > Playlists > Play and Stop.. then use the "n" key to play the next song (or the "p" key to go back)

---

### Post by Jan_Erik on 2015-12-08
Brilliant! Just what I needed:)
(However in order to get it to work I had to select both "Play and stop" and "Play and pause")

---

### Post by howefield on 2015-12-08
Cool, works for me with just the "Play and Stop" control checked, but glad you got it sussed.

---

### Post by Jan_Erik on 2015-12-08
Hi again. I have been testing this again tonight with a playlist and the functionalities seems to be a bit buggy in VLC. Suddenly the "n" button stops moving to the next track. I have seen the same issue on both Linux and windows. Maybe there is something with the audio file... Maybe I'll have to stick with VUPlayer on windows after all.. I will test some more and see if I can figure it out.

---

### Post by Dennis N on 2015-12-08
Here's how in Audacious:
Disable the repeat function on toolbar and in menu set **playback > "no playlist advance"**. Start play with '**x**' key and when play stops, advance with '**b**' key and repeat.

---

### Post by Jan_Erik on 2015-12-08
Nice! I will test this out in Audacious. However with regards to VLC i found out that I can use the arrow key up and down and launch with Return key and this works fine:)

---

### Post by Dennis N on 2015-12-08
It works. I checked it before answering to be sure.

---

### Post by tgalati4 on 2015-12-08
For a live show, I would use *mpd* on a sound server machine and an Android mpd client to control it via wireless network, or just a console terminal on the sound server.

> mpc - command-line tool to interface MPD
mpd - Music Player Daemon
mpd-dbg - Music Player Daemon debugging symbols
mpd-sima - Automagically add titles to MPD playlist
mpdcon.app - MPD controller for GNUstep
mpdcron - add scrobbler, rating, play counts and other functionalities to MPD
mpdris2 - media player interface (MPRIS2) bridge for MPD
mpdscribble - Last.fm reporting client for mpd
mpdscribble-dbg - Last.fm reporting client for mpd - debugger symbols
mpdtoys - small command line tools and toys for MPD


---

