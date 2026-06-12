---
title: "Can't set up mpd correctly..."
date: 2009-12-09
forum: Multimedia Software
---

### Post by Pott on 2009-12-09
I'd like to use MPD + sonata on my laptop but I can't seem to set it up correctly. Sonata doesn't see the library I set on the .conf file.

I couldn't find a 'how to' for Karmic out there. Is there anything of the sorts that describes how to do it for beginners..?

Thanks!

---

### Post by InkyDinky on 2009-12-11
Could you post your .mpdconf file and the mpd.log file?
That might help.
Also can you connect to mpd via a client?  See if you can connect via Firefox's Music Player Minion plugin.  That'll at least give us a start.

I don't know anything about getting it to work with sonata but I've gotten mpd to work on my local computer. I can't get music to be heard on a remote one :(

---

### Post by stewpye on 2009-12-11
Hi,I'm having the same problem. I tried with Sonata first but it doesn't seem to even tell you if you are connected to mpd, so then I installed GMPC. That said it was connected to MPD but I still cannot see the library. 

I'm new to linux so I could be missing something obvious.

My music is in the home/user/music directory.
mpd.conf is setup like this

```
music_directory        "~/music"                             *** have I got this wrong?
playlist_directory        "/var/lib/mpd/playlists"
db_file            "/var/lib/mpd/tag_cache"
log_file            "/var/log/mpd/mpd.log"
pid_file            "/var/run/mpd/pid"
state_file            "/var/lib/mpd/state"
```

I can see the state and tag_cache files in the /var/lib/mpd folder.

Pott, I hope you don't mind me hijacking this thread but we seem to have the same problem so may need the same solution.

Cheers,
Stewart.

---

### Post by Raffles10 on 2009-12-11
Have you guys created your database ?

```
mpd --create-db
```

MPD needs to be running before you start Sonata, this shouldn't be a problem because it should install as a daemon. If MPD is running ok it should show this:

```
$ mpd
listen: Failed to listen on any (line 65): Address already in use
Aborted

```

---

### Post by stewpye on 2009-12-11
Hi Raffles,

Thanks. Where do I issue those commands from? Just..
stewart@laptop:~$

or do I have to go into another directory?

Sorry, I really am new to linux

Stewart.

---

