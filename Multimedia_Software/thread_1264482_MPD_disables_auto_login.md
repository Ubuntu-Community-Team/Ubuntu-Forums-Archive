---
title: "MPD disables auto login?"
date: 2009-09-12
forum: Multimedia Software
---

### Post by chaopoch on 2009-09-12
I just install MPD, and it works fine, the only problem is MPD seems to disable the auto login, does any one experience this problem? and how to solve it? thanks for reply.

---

### Post by chaopoch on 2009-09-13
No one had this problem before?

---

### Post by mcduck on 2009-09-13
MPD shouldn't have anything to do with your login.

Could you explain in a bit more detail the steps you took to install & configure MPD?

---

### Post by chaopoch on 2009-09-13
Thanks for reply.

> **mcduck said:**
> MPD shouldn't have anything to do with your login.

I don't know, but if I remove MPD, the auto login is back.

> **mcduck said:**
> Could you explain in a bit more detail the steps you took to install & configure MPD?

here is my /etc/mpd.conf for your reference.

music_directory        "/media/sda2/&#38899;&#27138;"
playlist_directory    "~/mpd/playlists"
db_file            "~/mpd/tag_cache"
log_file        "~/mpd/mpd.log"
error_file        "~/mpd/errors.log"
pid_file        "~/mpd/pid"
state_file        "~/mpd/state"

user                            "xxxxx"    ( xxxxx is my login name )

bind_to_address                 "127.0.0.1"
port                            "6600"

audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
}

---

### Post by mcduck on 2009-09-13
> **chaopoch said:**
> Thanks for reply.



I don't know, but if I remove MPD, the auto login is back.



here is my /etc/mpd.conf for your reference.

music_directory        "/media/sda2/&#38899;&#27138;"
playlist_directory    "~/mpd/playlists"
db_file            "~/mpd/tag_cache"
log_file        "~/mpd/mpd.log"
error_file        "~/mpd/errors.log"
pid_file        "~/mpd/pid"
state_file        "~/mpd/state"

user                            "xxxxx"    ( xxxxx is my login name )

bind_to_address                 "127.0.0.1"
port                            "6600"

audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
}

Based on setting the user to your own user, I suppose you are not running MPD as system service (which is the way that works best and gives you most benefits).

This could be related to your login problem. For example if MPD is still being autostarted during boot your configuration makes it run as your user. That could mess with autologin as it would mean that you are already logged in (eb´´´ven though it's not really you, but MPD running as your user).

The way I always setup MPD is to simply let it run as it's own user (that's why it's called Music Player *Daemon*), and only symlinking my personal music directories into MPD's default directories. Takes less than 2 min to set up, usually no changes into MPD's default configurations, and works perfectly. :)

---

### Post by chaopoch on 2009-09-13
Do you mean that I should set the user to be "root"?

Would you please show me your /etc/mpd.conf? thanks a lot.

---

### Post by mcduck on 2009-09-13
No, it should be set to user "mpd", like it is by default. If it's set to start automatically at boot it's started by root, and then changes into running in the background as the user specified (pretty much the definition of a linux daemon).


Anyway, here's my mpd.conf:
```
## /etc/mpd.conf

music_directory		"/var/lib/mpd/music"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"

pid_file		"/var/run/mpd/pid"
state_file		"/var/lib/mpd/state"

user                            "mpd"
bind_to_address                 "localhost"
port                            "6600"

audio_output {
	type		"pulse"
	name		"MPD PulseAudio"
}
mixer_type                      "software"

filesystem_charset              "UTF-8"
id3v1_encoding                  "UTF-8"

gapless_mp3_playback             "yes"
```
None of the changes I've made to the default file are relevant to MPD actually working. The only thing I did after installing the MPD package was linking my music directories into MPD's default musoc directory, like this:
```

sudo ln -s /home/mcduck/Music/ /var/lib/mpd/music/mcduck
sudo ln -s /media/Helios/Music /var/lib/mpd/music/helios
```
(If you only have one music directory you can also link it directly into /var/lib/mpd/music nstead of linkin into a subdirectory like I do.)

---

### Post by chaopoch on 2009-09-13
mcduck,

I did the same changes to my /etc/mpd.conf as yours, and now it works great, thanks a lot!

---

### Post by mcduck on 2009-09-13
> **chaopoch said:**
> mcduck,

I did the same changes to my /etc/mpd.conf as yours, and now it works great, thanks a lot!

no problem :)

---

