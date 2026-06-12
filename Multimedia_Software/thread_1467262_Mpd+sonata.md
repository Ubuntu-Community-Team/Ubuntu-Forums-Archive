---
title: "Mpd+sonata"
date: 2010-04-30
forum: Multimedia Software
---

### Post by darkwish_ on 2010-04-30
Hello, i have read some MPD+Sonata HOWTO but they all are outdate, so they didnt help.
I just want to make Sonata play my music on mounted NTFS.
So i have:
Ubuntu 10.04
Sonata
MPD
Music on "/media/media/music" (mounted partition "media")

pls, help me with mpd.conf:
```
######################## REQUIRED PATHS ########################
music_directory                 "/var/lib/mpd/music"
playlist_directory              "/var/lib/mpd/playlists"
db_file                         "/var/lib/mpd/mpd.db"
log_file                        "/var/log/mpd/mpd.log"
error_file                      "/var/log/mpd/mpd.error"
pid_file                        "/var/run/mpd/mpd.pid"
state_file                      "/var/run/mpd/mpd.state"
```

---

### Post by madchine on 2010-05-13
I'm not running the daemon (MPD, as such) on Ubuntu, only clients (the user interface for controlling the daemon), so I don't know what the standard Ubuntu MPD setup is. Seeing as noone else has come to the rescue...

Your configuration poses one obvious question: The 'music_directory' doesn't point to your music collection (BTW 'media'? I know it seems... logical, but that's asking for confusion....)

You could just change it to /media/media/music but that direcotry might not always be present, so I'd say the cleverer option is to enter the /var/lib/mpd directory and create the music folder and inside that create a symbolic link to your media collection.
```
cd /var/lib/mpd/
sudo mkdir music ### unless it already exists
cd music 
sudo ln -s /media/media/music mediamusic
```
In previous releases the question of which user is assigned the job of running MPD has created huge problems especially when Ubuntu demoted pulseaudio from a systemwide daemon to per-user-status, but you can worry about that when you get there.... :)

---

