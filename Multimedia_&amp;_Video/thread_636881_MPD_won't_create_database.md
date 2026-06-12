---
title: "MPD won't create database"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by PurposeOfReason on 2007-12-10
When I run the command "sudo mpd --create-db", it gives me no errors but nothing is done. Here is my /etc/mpd.conf. There is a link to my music in the /var/lib/mpd/music.

```
port                            "6600"
music_directory		"/var/lib/mpd/music/"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"
pid_file		"/var/run/mpd/pid"


state_file		"/var/lib/mpd/state"

user                            "mpd"

bind_to_address                 "localhost"

audio_output {
        type                    "alsa"
        name                    "My ALSA Device"
        device                  "hw:0,0"     # optional
        format                  "44100:16:2" # optional
}

mixer_type                      "alsa"
mixer_device                    "default"
mixer_control                   "PCM"
```

---

