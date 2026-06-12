---
title: "Advice required Re: scriptable mp3 player"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by orbeus on 2007-11-17
Hi.

I have been looking (for a long time...) for a mp3 player for a project that has the following:

- Multi instance (3+)

- Output to multiple cards -"hw:0,0" , "hw:1,0" , etc

- Can play long m3u playlists

- Can set "loop" and "random" for playlists

- Preferably has a GUI

- Crossfading would be great...

- All the above to be scriptable including volume.

I found a great scriptable solution with VLC (using ALSA) but unfortunately there is a dropout on the audio every 30 seconds or so across all cards (plus no crossfade). I have tried 7.04 and 7.10, faster processors, expensive audio cards, more RAM and new PCs - to no effect.

Tried ALSA player. The sound quality is excellent and can assign outputs but will not accept long playlists. Crossfade doesn't work...

xmms plays well too but I can't find a way to script routing to separate outputs - as well as other features.

An example of a script I have for VLC is:

=============================
#!/bin/sh

lounge_start() {
echo "Starting lounge..." 
vlc --volume 450 --alsadev "hw:2,0" --random --loop /usr/local/playlists/lounge.m3u &
}

lounge_stop() {
echo "Stopping lounge..."
killall vlc
}

lounge_restart() {
lounge_stop
sleep 1
lounge_start
}

case "$1" in
'start')
lounge_start
;;
'stop')
lounge_stop
;;
'restart')
lounge_restart
;;
*)
lounge_start
esac

============================

Any and all feedback most welcome!

TIA

O

---

