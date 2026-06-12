---
title: "GNOME MPlayer opens stream, command line mplayer does not"
date: 2016-09-29
forum: Multimedia Software
---

### Post by mwmw on 2016-09-29
I'm trying to stream audio from a local NPR station via mplayer.  When I try and open the URL ([http://wamu.org/streams/live/1/live.m3u](http://wamu.org/streams/live/1/live.m3u)) in mplayer via command line ($ mplayer [http://wamu.org/streams/live/1/live.m3u](http://wamu.org/streams/live/1/live.m3u)) I get the following error:

[INDENT]MPlayer 1.2.1 (Debian), built with gcc-5.3.1 (C) 2000-2016 MPlayer Team[/INDENT]
[INDENT]mplayer: could not connect to socket[/INDENT]
[INDENT]mplayer: No such file or directory[/INDENT]
[INDENT]Failed to open LIRC support. You will not be able to use your remote control.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Playing [http://wamu.org/streams/live/1/live.m3u](http://wamu.org/streams/live/1/live.m3u).[/INDENT]
[INDENT]Resolving wamu.org for AF_INET6...[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Couldn't resolve name for AF_INET6: wamu.org[/INDENT]
[INDENT]Resolving wamu.org for AF_INET...[/INDENT]
[INDENT]Connecting to server wamu.org[199.79.48.26]: 80...[/INDENT]
[INDENT]Resolving static.wamu.org for AF_INET6...[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Couldn't resolve name for AF_INET6: static.wamu.org[/INDENT]
[INDENT]Resolving static.wamu.org for AF_INET...[/INDENT]
[INDENT]Connecting to server static.wamu.org[52.85.90.235]: 80...[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Cache size set to 320 KBytes[/INDENT]
[INDENT]Cache fill:  0.01% (31 bytes)   [/INDENT]
[INDENT]
[/INDENT]
[INDENT]libavformat version 56.40.101 (external)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Exiting... (End of file)[/INDENT]

However, when I open the same stream using GNOME MPlayer it takes a few seconds to buffer and then starts playing. Since I think GNOME MPlayer is just a front end for mplayer, what can I use in the command line to open this stream?

thanks

---

### Post by mc4man on 2016-09-29
Don't particularly use mplayer much anymore but i'd guess this may work - 
```
mplayer -playlist http://wamu.org/streams/live/1/live.m3u
```

---

### Post by ajgreeny on 2016-09-30
> **mc4man said:**
> Don't particularly use mplayer much anymore but i'd guess this may work - 
```
mplayer -playlist http://wamu.org/streams/live/1/live.m3u
```
That is the way it used to work and certainly I managed to listen to concerts broadcast as m3u playlists in the past using cron to time them and mplayer.

The cli version of mplayer demands that you tell it that the stream is a playlist or it does exactly what you have found; nothing.
Gnome-mplayer, however,  sees that it is a playlist and manages to add that **-playlist** option automatically.

---

### Post by mwmw on 2016-09-30
That's the one - thanks!

---

