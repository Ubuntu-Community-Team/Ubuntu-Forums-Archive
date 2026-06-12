---
title: "MPD Setup"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by crisnoh on 2008-04-08
Been trying to setup mpd my following this guide:

[http://mpd.wikia.com/wiki/Getting_Started]("http://http://mpd.wikia.com/wiki/Getting_Started")

When I attempt mpc update I get the following error:

```
$ mpc update
MPD_HOST and/or MPD_PORT environment variables are not set
error: problems getting a response from "localhost" on port 6600 : Connection refused

```

Here is my .mpdcof file:

```
port			"6600"
music_directory         "~/Music"
playlist_directory      "~/.mpd/playlists"
db_file                 "~/.mpd/mpd.db"
log_file                "~/.mpd/mpd.log"
error_file              "~/.mpd/mpd.error"
```

Hope someone can help!

---

### Post by crisnoh on 2008-04-09
::bump::

---

### Post by djnm on 2008-04-09
try commenting out the port line and add
```
bind_to_address "127.0.0.1"
```

---

