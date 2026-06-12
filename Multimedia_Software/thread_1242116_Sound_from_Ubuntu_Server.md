---
title: "Sound from Ubuntu Server"
date: 2009-08-16
forum: Multimedia Software
---

### Post by Choobie on 2009-08-16
Hi everybody!

I am needing some help outputting some sound from my Ubuntu server. This is a personal server running off a box that was built from the time of Windows 95.

So it is running a text-only server for the sake of running at a decent speed, but I was wondering why it isn't putting out any sound. Here are the things that I have done so far:

>Installed: alsa, alsa-base, alsa-utils, pulseaudio, gstreamer0.10*, linux-sound-base

>modprobed the correct alsa driver (well pretty much everything from the Comprehensive Sound Problem guide), and I am a member of the audio group.

>Plugged in speakers, headphones, everything that fit the hole.

>Tried a variety of players (mpd, vlc, mplayer) as well as speaker-test to ensure it is not codec problems.

>Also, all volumes on full in alsamixer and everywhere else I could find a volume switch.

When using mplayer (e.g. 'mplayer /path/some\ song.ogg') it acts like it is playing the song (as in I can see it progressing through the song like it is playing) and it says that alsa is functioning correctly, but I do get a 'A0: [pulse] Failed to connect to server: Connection refused.' (and running mplayer at root doesn't get rid of the problem). Perhaps I just don't have pulseaudio configured correctly?

Is there some package or something that I am just missing? It would be ideal for my situation to use mpd and remote in with sonata to control it since my music will be put on the server and connected to my sound system if this gets working. I do have mpd running and I can can control it remotely, just need to get sound working and I am a happy cookie.

Thanks!

---

