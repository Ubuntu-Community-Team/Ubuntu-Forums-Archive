---
title: "Problem transferring MPD/Icecast setup to 16.04"
date: 2016-08-08
forum: Multimedia Software
---

### Post by bvargo on 2016-08-08
Originally, I had an MPD/Icecast setup on 12.04 which was working fine.  When I went to 16.04, I decided to install fresh onto a new drive instead of doing a release upgrade (numerous problems with the old system despite upgrade to 14.04).  I figured I would basically be able to move my old configuration files to the new system for e.g. MPD, Icecast2, Deluge, etc.  When I moved the MPD configuration over, I had some permissions issues to work out but I'm able to connect to it with GMPC.  The problem is that when I moved the configuration files over for Icecast2, I cannot get MPD to connect to it.  I'm not really concerned about the ALSA issue because it wasn't working on the old system.  The problem is I cannot connect to Icecast2.

```

$ tail /var/log/mpd/mpd.log
Aug 08 15:08 : alsa_output: "My ALSA Device" [alsa] failed to play: Broken pipe
Aug 08 15:08 : output: Failed to open audio output
Aug 08 15:08 : player: played "Grateful Dead -- 1989-10-09 -- Hampton Coliseum/gd89-10-09d1t04.wav_vbr.mp3"
Aug 08 15:08 : avahi: Service 'Music Player' successfully established.
Aug 08 15:08 : client: [0] opened from 127.0.0.1:58600
Aug 08 15:16 : shout_output: Failed to open "My Shout Stream" [shout]: problem opening connection to shout server localhost:8000: Couldn't connect
Aug 08 15:16 : shout_output: Failed to open "My Shout Stream" [shout]: problem opening connection to shout server localhost:8000: Couldn't connect
Aug 08 15:16 : shout_output: Failed to open "My Shout Stream" [shout]: problem opening connection to shout server localhost:8000: Couldn't connect
Aug 08 15:16 : shout_output: Failed to open "My Shout Stream" [shout]: problem opening connection to shout server localhost:8000: Couldn't connect
Aug 08 15:16 : shout_output: Failed to open "My Shout Stream" [shout]: problem opening connection to shout server localhost:8000: Couldn't connect

```

```

$ sudo netstat -ltpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:6600            0.0.0.0:*               LISTEN      26907/mpd       
tcp        0      0 127.0.0.1:60015         0.0.0.0:*               LISTEN      26257/GoogleTalkPlu
tcp        0      0 127.0.0.1:48175         0.0.0.0:*               LISTEN      26257/GoogleTalkPlu

```

It seems that Icecast2 won't load and I can't figure out why it would work on the old system but not on the new system.

Help would be appreciated.

---

