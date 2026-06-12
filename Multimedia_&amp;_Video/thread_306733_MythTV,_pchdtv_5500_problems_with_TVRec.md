---
title: "MythTV, pchdtv 5500 problems with TVRec"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by ShiftyPowers on 2006-11-25
Hi, I'm having a tough time getting my HTPC setup finalized with a pcHDTV 5500 card.  I managed to install the card and I'm able to use dvb-apps and such to scan channels and play them in mplayer.  That means I know the drivers work and the card loads fine and the setup should techinically work.  

Then problem is trying to get it to work with mythTV.  I am using the HD 5500 card to capture OTA ATSC high definition signal in my area.  

I setup a fresh install of SVN mythtv today and setup the capture card as a DVB card.  Then I used Zap2It for broadcast in my area as the listings source and finally made mythtv scan for channels from the antenna connected to the HD 5500.  

The program scans and finds the channels fine. I can see the output and the success on certain channels.  

The problem is that when I go to play livetv I get a black screen with no signal.  /var/log/mythtv/mythbackend.log has the following errors in it at that time:

```
2006-11-25 10:11:52.892 Using runtime prefix = /usr
2006-11-25 10:11:52.971 New DB connection, total: 1
2006-11-25 10:11:53.034 Connected to database 'mythconverg' at host: localhost
2006-11-25 10:11:53.054 Current Schema Version: 1169
Starting up as the master server.
2006-11-25 10:11:53.087 New DB connection, total: 2
2006-11-25 10:11:53.106 Connected to database 'mythconverg' at host: localhost
2006-11-25 10:11:53.124 EITHelper: localtime offset -8:00:00
2006-11-25 10:11:53.142 New DB connection, total: 3
2006-11-25 10:11:53.158 Connected to database 'mythconverg' at host: localhost
2006-11-25 10:11:53.211 New DB scheduler connection
2006-11-25 10:11:53.222 Connected to database 'mythconverg' at host: localhost
2006-11-25 10:11:53.236 Main::Starting HttpServer
2006-11-25 10:11:53.251 Main::Registering HttpStatus Extension
2006-11-25 10:11:53.293 mythbackend version: 0.20.20061113-1 www.mythtv.org
2006-11-25 10:11:53.302 Enabled verbose msgs:  important general
2006-11-25 10:11:53.314 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2006-11-25 10:11:53.327 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2006-11-25 10:11:55.244 Reschedule requested for id -1.
2006-11-25 10:11:55.279 Scheduled 0 items in 0.0 = 0.02 match + 0.02 place
2006-11-25 10:11:55.301 Seem to be woken up by USER
2006-11-25 10:12:41.501 MainServer::HandleAnnounce Monitor
2006-11-25 10:12:41.515 adding: HTPC as a client (events: 0)
2006-11-25 10:12:41.526 MainServer::HandleAnnounce Monitor
2006-11-25 10:12:41.537 adding: HTPC as a client (events: 1)
2006-11-25 10:12:41.556 MainServer::HandleAnnounce Playback
2006-11-25 10:12:41.571 adding: HTPC as a client (events: 0)
2006-11-25 10:12:41.583 TVRec(1): Changing from None to WatchingLiveTV
2006-11-25 10:12:41.598 TVRec(1): HW Tuner: 1->1
2006-11-25 10:12:41.698 TVRec(1) Error: Failed to setup digital signal monitoring
2006-11-25 10:12:41.757 TVRec(1) Error: Failed to setup signal monitor
2006-11-25 10:12:48.038 TVRec(1): Changing from WatchingLiveTV to None
2006-11-25 10:12:48.057 Finished recording Unknown: channel 1021

```

I've searched all over for this TVRec error and can't find a solution.  Does anyone have a clue?

---

### Post by superm1 on 2006-11-27
This can easily be a permissions related problem where during the scan you may have ran mythtv-setup as a superuser and had permissions for all the dvb devices.  Now when your running the backend, is it running as a user with adequate permissions?

---

