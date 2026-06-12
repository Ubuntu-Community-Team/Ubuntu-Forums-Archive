---
title: "MPD: &quot;Connection Refused&quot;"
date: 2013-02-27
forum: Multimedia Software
---

### Post by RPisces on 2013-02-27
I'm trying to get MPD/MPC working to play an online radio stream. But any time I try to
-Add this link (tested working on my laptop with MPC) :
[http://audio-mp3.ibiblio.org:8000/wdav-112k]("http://audio-mp3.ibiblio.org:8000/wdav-112k")
-Add a playlist through MPC
-Play anything through MPD

Or really, do anything involving MPC/MPD, I get the following
```

error: Connection refused
```

I've tried everything at this thread to no avail:
[http://ubuntuforums.org/showthread.php?t=1842170&highlight=mpd+connection+refused&page=2](http://ubuntuforums.org/showthread.php?t=1842170&highlight=mpd+connection+refused&page=2)

Though, I tried this: 
```
/etc/init.d/mpd start
``` 
...and got this interesting output:
```
 * Starting Music Player Daemon mpd                                             daemon: cannot init supplementary groups of user "ubuntu": Operation not permitted
Failed to load database: Database corrupted
daemon: could not create pid file "/var/run/mpd/pid": Permission denied                                                             [fail]
```

Here is my mpd.conf file:
```

music_directory         "/var/lib/mpd/music"
playlist_directory              "/home/ubuntu/.mpd/playlists"
db_file                 "/home/ubuntu/.mpd/mpd.db"
log_file                        "/home/ubuntu/.mpd/mpd.log"
pid_file                        "/var/run/mpd/pid"

```

I'm running Ubuntu-minimal-armhf 12.10. Any ideas? :-k

---

### Post by RPisces on 2013-03-04
bump.

---

### Post by moody_mark on 2013-03-10
Hi, what user are you running mpd as? Looks like a permissions problem.

See this link for mpd help, I found it quite useful: [http://mpd.wikia.com/wiki/Music_Player_Daemon_HOWTO_Troubleshoot](http://mpd.wikia.com/wiki/Music_Player_Daemon_HOWTO_Troubleshoot)

---

### Post by tgalati4 on 2013-03-10
Do you have a real user named "ubuntu"?  According to your configuration file, you are pointing to this database file:

db_file                 "/home**/ubuntu**/.mpd/mpd.db"

Since MPD couldn't find the database, perhaps you have created a different user--unless your name is ubuntu.

Who is listed in /home?

```
ls -la /home
```

I believe that MPD and MPC need to have the same user accounts on different machines (or the same machine) in order to communicate smoothly.

---

