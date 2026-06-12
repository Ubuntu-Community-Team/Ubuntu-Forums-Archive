---
title: "WatchTV fails in MythTV"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by brandon_r87 on 2007-04-11
Hello,

After much fiddling around, I got a MythTV install working to the point where I can start the backend, but now I am unable to watch TV.  My tuner card is a Hauppauge PVR-500.  I know it is setup correctly in mythtv-setup because I was able to watch TV one time, so I'm not sure what is going on.  When I load the frontend and select "Watch TV" the screen flashes black and then goes back to the main menu.

Here's a log of booting the backend and frontend.  I bolded the part that looks like what is going on.  As for the permisson denied mpg file, it doesn't exist.
```
2007-04-11 01:09:16.555 Using runtime prefix = /usr
2007-04-11 01:09:16.602 New DB connection, total: 1
2007-04-11 01:09:16.607 Connected to database 'mythconverg' at host: localhost
2007-04-11 01:09:16.611 Current Schema Version: 1160
Starting up as the master server.
2007-04-11 01:09:16.644 New DB connection, total: 2
2007-04-11 01:09:16.645 Connected to database 'mythconverg' at host: localhost
2007-04-11 01:09:16.647 EITHelper: localtime offset -5:00:00 
2007-04-11 01:09:16.650 New DB connection, total: 3
2007-04-11 01:09:16.651 Connected to database 'mythconverg' at host: localhost
2007-04-11 01:09:16.698 EITHelper: localtime offset -5:00:00 
2007-04-11 01:09:16.742 New DB scheduler connection
2007-04-11 01:09:16.747 Connected to database 'mythconverg' at host: localhost
2007-04-11 01:09:16.749 Main::Starting HttpServer
2007-04-11 01:09:16.754 Main::Registering HttpStatus Extension
2007-04-11 01:09:16.759 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-04-11 01:09:16.761 Enabled verbose msgs:  important general
2007-04-11 01:09:16.761 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-04-11 01:09:16.762 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-04-11 01:09:18.756 Reschedule requested for id -1.
2007-04-11 01:09:18.963 Scheduled 1 items in 0.2 = 0.20 match + 0.01 place
2007-04-11 01:09:18.966 Seem to be woken up by USER
2007-04-11 01:09:42.283 MainServer::HandleAnnounce Monitor
2007-04-11 01:09:42.286 adding: ubuntu as a client (events: 0)
2007-04-11 01:09:42.301 MainServer::HandleAnnounce Monitor
2007-04-11 01:09:42.302 adding: ubuntu as a client (events: 1)
2007-04-11 01:09:42.308 MainServer::HandleAnnounce Playback
2007-04-11 01:09:42.315 adding: ubuntu as a client (events: 0)
[B]2007-04-11 01:09:42.318 TVRec(1): Changing from None to WatchingLiveTV
2007-04-11 01:09:42.322 TVRec(1): HW Tuner: 1->1
2007-04-11 01:09:42.450 TFW, Error: Opening file '/var/lib/mythtv/recordings/1046_20070411010942.mpg'.
			eno: Permission denied (13)
2007-04-11 01:09:42.453 TVRec(1) Error: RingBuffer '/var/lib/mythtv/recordings/1046_20070411010942.mpg' not open...
2007-04-11 01:09:42.456 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2007-04-11 01:09:42.467 TVRec(1) Error: Failed to create RingBuffer 2
2007-04-11 01:09:42.469 TVRec(1): Changing from WatchingLiveTV to None[/B]
2007-04-11 01:10:32.041 Reloading backend settings
2007-04-11 01:11:10.080 Reschedule requested for id 0.
2007-04-11 01:11:10.096 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2007-04-11 01:11:25.329 MainServer::HandleAnnounce Playback
2007-04-11 01:11:25.332 adding: ubuntu as a client (events: 0)
[B]2007-04-11 01:11:25.334 TVRec(1): Changing from None to WatchingLiveTV
2007-04-11 01:11:25.337 TVRec(1): HW Tuner: 1->1
2007-04-11 01:11:25.445 TFW, Error: Opening file '/var/lib/mythtv/recordings/1046_20070411011125.mpg'.
			eno: Permission denied (13)
2007-04-11 01:11:25.447 TVRec(1) Error: RingBuffer '/var/lib/mythtv/recordings/1046_20070411011125.mpg' not open...
2007-04-11 01:11:25.449 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2007-04-11 01:11:25.450 TVRec(1) Error: Failed to create RingBuffer 2
2007-04-11 01:11:25.452 TVRec(1): Changing from WatchingLiveTV to None[/B]

```

---

### Post by barney_1 on 2007-04-11
I sounds like the directory you have set up to record TV is not accessible.  Try this:

```
sudo chmod 777 /var/lib/mythtv/recordings
```

---

### Post by superm1 on 2007-04-11
The permissions on /var/lib/mythtv/ are by default set to be writable by the mythtv user that starts the backend process via init script.

How did you start your backend?

---

### Post by majoridiot on 2007-04-12
> **barney_1 said:**
> I sounds like the directory you have set up to record TV is not accessible.  Try this:

```
sudo chmod 777 /var/lib/mythtv/recordings
```


or

```
sudo chmod -R 777 /var/lib/mythtv/recordings
```

which will change the write permissions recursively, to make sure the nfslockfile and anything else in
that directory is also writable.

you shouldn't have permission issues if installed correctly, tho.

---

### Post by barney_1 on 2007-04-12
majoridiot you are absolutely right, sorry I forgot the -R

---

### Post by majoridiot on 2007-04-12
> **barney_1 said:**
> majoridiot you are absolutely right, sorry I forgot the -R

let's not let that happen again... ok?  LOL :D

---

