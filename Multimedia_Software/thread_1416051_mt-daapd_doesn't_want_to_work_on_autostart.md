---
title: "mt-daapd doesn't want to work on autostart"
date: 2010-02-25
forum: Multimedia Software
---

### Post by matthewboh on 2010-02-25
I decided to try and get my firefly server to start up at boot, and it starts, but it doesn't stream the music.  If I bring up Rhythmbox, it looks like it's playing, but no music.

I've checked syslog and everything looks alright.  If I do a manual restart on mt-daapd, then everything is fine.

Here's the output from a cold boot
```
Feb 25 15:31:45 ubuntu mt-daapd[6221]: Firefly Version svn-1696: Starting with debuglevel 2 
Feb 25 15:31:45 ubuntu mt-daapd[6221]: Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load 
Feb 25 15:31:45 ubuntu mt-daapd[6221]: Plugin loaded: ssc-ffmpeg/svn-1696 
Feb 25 15:31:45 ubuntu mt-daapd[6221]: Plugin loaded: daap/svn-1696 
Feb 25 15:31:45 ubuntu mt-daapd[6221]: Plugin loaded: rsp/svn-1696 
Feb 25 15:31:45 ubuntu mt-daapd[6221]: Starting rendezvous daemon 
Feb 25 15:31:45 ubuntu mt-daapd[6223]: *** WARNING *** The program 'mt-daapd' uses the HOWL compatibility layer of Avahi.
Feb 25 15:31:45 ubuntu mt-daapd[6223]: *** WARNING *** Please fix your application to use the native API of Avahi!
Feb 25 15:31:45 ubuntu mt-daapd[6223]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=howl&e=mt-daapd>
Feb 25 15:31:45 ubuntu mt-daapd[6221]: Starting signal handler 
Feb 25 15:31:45 ubuntu mt-daapd[6225]: Initializing database 
Feb 25 15:31:49 ubuntu mt-daapd[6225]: Starting web server from /usr/share/mt-daapd/admin-root on port 3689 
Feb 25 15:31:49 ubuntu mt-daapd[6225]: Registering rendezvous names 
Feb 25 15:31:49 ubuntu mt-daapd[6225]: Serving 3819 songs.  Startup complete in 4 seconds
```

Here's the output from the restart
```
Feb 25 15:35:21 ubuntu mt-daapd[6225]: Got shutdown signal. 
Feb 25 15:35:21 ubuntu mt-daapd[6225]: Stopping gracefully 
Feb 25 15:35:21 ubuntu mt-daapd[6225]: Stopping rendezvous daemon 
Feb 25 15:35:21 ubuntu mt-daapd[6225]: Closing database 
Feb 25 15:35:21 ubuntu mt-daapd[6225]: Done! 
Feb 25 15:35:21 ubuntu mt-daapd[6223]: Rendezvous socket closed (daap server crashed?)  Aborting. 
Feb 25 15:35:21 ubuntu mt-daapd[6407]: Firefly Version svn-1696: Starting with debuglevel 2 
Feb 25 15:35:21 ubuntu mt-daapd[6407]: Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load 
Feb 25 15:35:21 ubuntu mt-daapd[6407]: Plugin loaded: ssc-ffmpeg/svn-1696 
Feb 25 15:35:21 ubuntu mt-daapd[6407]: Plugin loaded: daap/svn-1696 
Feb 25 15:35:21 ubuntu mt-daapd[6407]: Plugin loaded: rsp/svn-1696 
Feb 25 15:35:21 ubuntu mt-daapd[6407]: Starting rendezvous daemon 
Feb 25 15:35:21 ubuntu mt-daapd[6408]: *** WARNING *** The program 'mt-daapd' uses the HOWL compatibility layer of Avahi.
Feb 25 15:35:21 ubuntu mt-daapd[6408]: *** WARNING *** Please fix your application to use the native API of Avahi!
Feb 25 15:35:21 ubuntu mt-daapd[6408]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=howl&e=mt-daapd>
Feb 25 15:35:21 ubuntu mt-daapd[6407]: Starting signal handler 
Feb 25 15:35:21 ubuntu mt-daapd[6410]: Initializing database 
Feb 25 15:35:21 ubuntu mt-daapd[6410]: Starting web server from /usr/share/mt-daapd/admin-root on port 3689 
Feb 25 15:35:21 ubuntu mt-daapd[6410]: Registering rendezvous names 
Feb 25 15:35:21 ubuntu mt-daapd[6410]: Serving 3819 songs.  Startup complete in 0 seconds

```

What else should I be looking for?

Thanks

---

### Post by doas777 on 2010-02-25
I had trouble getting firefly to start up initially, but magically 24 hours after starting the service for the first time, it just worked perfectly. I also noticed that the number of tracks it had indexed had gone up signifigantly, so I guess it needed to index everything before it would start working, and that took a while on my collection. of course, your millage may very

---

### Post by matthewboh on 2010-02-25
I waited 15 minute after reboot - and still the same - looks like it's playing, but no sound.  Did a restart on mt-daapd and it works fine.

Is there some way to raise the debug level?

---

