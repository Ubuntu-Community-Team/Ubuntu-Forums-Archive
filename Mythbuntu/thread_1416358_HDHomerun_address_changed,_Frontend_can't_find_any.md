---
title: "HDHomerun address changed, Frontend can't find any stations"
date: 2010-02-26
forum: Mythbuntu
---

### Post by boombox1387 on 2010-02-26
I'm using a single tuner version of the SiliconDust HDHomeRun.  This is an external tuner that connects with computers via the network.  For some reason the address of the tuner changed from xxx.xxx.x.3 to xxx.xxx.x.2, and MythTV didn't exactly handle this change gracefully.

After wondering why no channels were working, I ran the hdhomerun_config CLI tool and found the new location of the device.  I went into the mythtv-setup and changed the location there.  After doing that, the backend can find all the stations again in a scan, but the frontend still doesn't work.  When a navigate to "Watch TV", it tells me to "Please Wait..." for several seconds, but then goes back to the main menu without any explanation.

Running the frontend from the command line gives this:

```
2010-02-26 00:30:28.629 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-02-26 00:30:28.630 Using protocol version 50
2010-02-26 00:30:30.261 New DB connection, total: 2
2010-02-26 00:30:30.262 Connected to database 'mythconverg' at host: localhost
2010-02-26 00:30:30.433 TV: Attempting to change from None to Watching WatchingLiveTV
2010-02-26 00:30:30.434 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-02-26 00:30:30.436 Using protocol version 50
2010-02-26 00:30:30.582 Spawning LiveTV Recorder -- begin
2010-02-26 00:30:30.909 Spawning LiveTV Recorder -- end
2010-02-26 00:30:30.910 GetEntryAt(-1) failed.
2010-02-26 00:30:30.912 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-02-26 00:30:30.912 TV Error: HandleStateChange(): LiveTV not successfully started
2010-02-26 00:30:30.912 We have a RingBuffer
2010-02-26 00:30:30.962 TV Error: LiveTV not successfully started

```

A little browsing on the internet hints that the "failed to get pginfo" error has something to do with having multiple cards in the database.  Is my "first" card still there causing problems?

Any help would be awesome.

---

### Post by boombox1387 on 2010-02-28
So it wasn't magic that made the ip address of my hdhomerun change - I accidentally plugged it into a different (wrong) spot in my router.  Unfortunately, I changed the settings in the backend to reflect the change I made, which should have worked out fine, but it led to this error.  Moving the router back to x.x.x.3 instead of x.x.x.2, and changing the backend to reflect this (the original settings) still doesn't let me tune any channels.  I still get the same error as in my original post.

Any help would still be appreciated.  What does the error mean?  If I delete the mythtv database, will it automatically recreate this for me?  Where is this file even located?  Would it be better to just reinstall?

---

### Post by boombox1387 on 2010-03-01
Turns out the issue had absolutely nothing to do with the address of the HDHomeRun, and it had everything to do with the fact that I set the directory for storing LiveTV recordings to something other than /var/lib/mythtv/livetv.  Why live TV fails every time I try to set the directory to /media/livetv is still a mystery to me.

---

### Post by nickrout on 2010-03-01
probably permission issues, but perhaps your logs would be worth looking at?

---

### Post by boombox1387 on 2010-03-02
> **nickrout said:**
> probably permission issues, but perhaps your logs would be worth looking at?

I don't think it's permissions, because I made sure that the permissions of the /media/livetv exactly matched /var/lib/mythtv/livetv.  Owner and group are mythtv:mythtv, permissions are 2775 (if I'm remembering correctly off the top of my head).

If logs would be helpful, just let me know how I can get them.  I'd really like to get this figured out, but I don't know where to start.

---

### Post by nickrout on 2010-03-02
> **boombox1387 said:**
> I don't think it's permissions, because I made sure that the permissions of the /media/livetv exactly matched /var/lib/mythtv/livetv.  Owner and group are mythtv:mythtv, permissions are 2775 (if I'm remembering correctly off the top of my head).

If logs would be helpful, just let me know how I can get them.  I'd really like to get this figured out, but I don't know where to start.

```
ls -ld /media/livetv
```

then look at /var/log/mythtv/mythbackend.log and /var/log/mythtv/mythfrontend.log at the point when livetv starts.

---

### Post by LowSky on 2010-03-02
I have learned if you reserve a port number on the router for a the device you dont get these issues. Highly recommended for the backend to have a reserved port so it doesn't throw off your settings.

---

### Post by nickrout on 2010-03-02
> **LowSky said:**
> I have learned if you reserve a port number on the router for a the device you dont get these issues. Highly recommended for the backend to have a reserved port so it doesn't throw off your settings.

I assume you mean reserve an IP address??

> The first thing we do, let's kill all the lawyers.
-- Wm. Shakespeare, "Henry VI", Part IV 

I assume you realise the reason the villains wanted to kill all the lawyers after the revolution is because lawyers were seen as the bastions of freedom and were therefore seen to be against the totalitarian regime of the rebels?

IAAL :)

---

### Post by boombox1387 on 2010-03-03
> **nickrout said:**
> ```
ls -ld /media/livetv
```

then look at /var/log/mythtv/mythbackend.log and /var/log/mythtv/mythfrontend.log at the point when livetv starts.

So, earlier I lied for the sake of simplicity. I was actually trying to store livetv in /media/backup/mythtv/recordings.  Here's how the permissions compare with the default /var/lib/mythtv/livetv:

```
michael@michael-desktop:~$ ls -ld /media/backup/mythtv/recordings
drwxrwsr-x 2 mythtv mythtv 4096 2010-02-25 19:10 /media/backup/mythtv/recordings
michael@michael-desktop:~$ ls -ld /var/lib/mythtv/livetv
drwxrwsr-x 2 mythtv mythtv 4096 2010-03-03 10:04 /var/lib/mythtv/livetv

```

As far as I can tell, things look identical, but watching TV silently fails every time I add this directory to the Backend.  I don't think it's a permissions problem, unless permissions of the containing folders are also important.  What exactly am I looking for in the log?

---

### Post by nickrout on 2010-03-03
just watch the log while you start livetv. ssh in from a laptop and run ```
tail -f /var/log/mythtv/mythbackend.log
```. Then start livetv and report what happens in the logs.

---

