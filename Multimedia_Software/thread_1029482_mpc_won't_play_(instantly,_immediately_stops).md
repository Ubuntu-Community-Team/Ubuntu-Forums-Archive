---
title: "mpc won't play (instantly, immediately stops)"
date: 2009-01-03
forum: Multimedia Software
---

### Post by Tonren on 2009-01-03
I'm a big fan of the mpd/mpc audio playing solution.  I recently re-installed my OS with 8.10, keeping my home directory and .rc files from previous versions.  I'm on an HP Compaq Presario v2565us.  I've installed the stuff for restricted codecs, installed mpd and mpc from the Ubuntu repos, done a --create-db, and made sure all of my permissions are in order, but this is my output from mpc:

mcantor@zanpakuto ~: mpc play
Yoko Kanno - Intro Theme
[playing] #1/52   0:00/4:23 (0%)
volume: 81%   repeat: off   random: off
mcantor@zanpakuto ~: mpc
volume: 81%   repeat: off   random: off

Here's my mpd config file:

music_directory		"/var/lib/mpd/music"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"
pid_file		"/var/run/mpd/pid"
state_file		"/var/lib/mpd/state"
user                            "mpd"
bind_to_address                 "localhost"
filesystem_charset              "UTF-8"
id3v1_encoding                  "UTF-8"

/var/lib/mpd/music is symlinked to the music directory in my home folder, though that shouldn't make a difference.

Should I add an audio output device clause to my mpd config file?  I googled around and didn't see anything.

My soundcard doesn't support hw mixing, so that could also be an issue, but I closed pretty much every other application before trying to play (especially Firefox).  I've heard that adding a plughw:0,0 audio device can sometimes fix things, or enabling dmix in alsa, but I don't want to start screwing around with all that nonsense if someone out there has a solution.

So, any suggestions?

---

### Post by Tonren on 2009-01-03
Think I figured it out... I added this clause to the config file:

audio_output {
        type                    "alsa"
        name                    "My ALSA Device"
        device                  "hw:0,0"     # optional
        format                  "44100:16:2" # optional
}

And restarted mpd.  I guess it's possible that just restarting mpd fixed it, but who knows?

---

