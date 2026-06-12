---
title: "Sounds Issues 10.04"
date: 2010-09-04
forum: Multimedia Software
---

### Post by garyozzy on 2010-09-04
(selected all variants because it's all from the shell)

Ok--so here's what's going on. 

mpd used to work great, but now mpc gives the error
```
error: Connection refused
```

and ncmpcpp gives the error:
```
Cannot connect to mpd: problems connecting to "localhost" on port 6600: Connection refused
```

Trying to use espeak gives the error
```
bt_audio_service_open: connect() failed: Connection refused (111)

```

Audio works in VLC just fine.

In a previous install, mpd would work until I used another application that used sound. Now it won't work at all even after a reboot.

mpd.conf:

(without most comments--I'm viewing over ssh)
```
# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

music_directory         "/home/gary/Music"

playlist_directory              "/varr/lib/mpd/playlists"
db_file                 "/var/lib/mpd/tag_cache"
log_file                        "/var/log/mpd/mpd.log"
pid_file                        "/var/run/mpd/pid"
state_file                      "/var/lib/mpd/state"
user                            "mpd"
bind_to_address         "localhost"
#bind_to_address                "/var/run/mpd/socket"
#port                           "6600"


input {
        plugin "curl"
#       proxy "proxy.isp.com:8080"
#       proxy_user "user"
#       proxy_password "password"
}

audio_output {
        type            "alsa"
        name            "My ALSA Device"
        device          "hw:0,0"        # optional
        format          "44100:16:2"    # optional
        mixer_device    "default"       # optional
        mixer_control   "PCM"           # optional
        mixer_index     "0"             # optional
}
filesystem_charset              "UTF-8"
id3v1_encoding                  "UTF-8"

```

Hope someone can make sense of this!
Gary

---

