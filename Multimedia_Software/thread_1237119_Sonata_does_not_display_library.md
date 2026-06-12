---
title: "Sonata does not display library"
date: 2009-08-11
forum: Multimedia Software
---

### Post by HyperHacker on 2009-08-11
This used to be working, then suddenly mpd just stopped playing in the middle of a song. Since then Sonata does not display the library anymore. The directory is set correctly in both mpdconf and Sonata. If I run "mpd --create-db" it appears to build a database just fine, and then if I do Update Library in Sonata it says it's updating, but no files show up.

~/mpdconf:> music_directory "/home/hyperhacker/music"
playlist_directory "/home/hyperhacker/music/!Playlists"
db_file "/home/hyperhacker/music/.mpd/db"
log_file "/home/hyperhacker/music/.mpd/status.log"
error_file "/home/hyperhacker/music/.mpd/err.log"
pid_file "/home/hyperhacker/music/.mpd/pid"
state_file "/home/hyperhacker/music/.mpd/state"
bind_to_address "127.0.0.1"
log_level "secure"
#password "xxxxxx@read,add,control,admin"
volume_normalization "yes"


---

