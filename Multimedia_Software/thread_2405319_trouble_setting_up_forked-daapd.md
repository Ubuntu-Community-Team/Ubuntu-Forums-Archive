---
title: "trouble setting up forked-daapd"
date: 2018-11-04
forum: Multimedia Software
---

### Post by TechnoJunky on 2018-11-04
I installed forked-daapd from Git, source.  I had trouble setting it up and while searching for results I found that I could have installed it from the Ubuntu repositories.  So I did that, overwriting what I installed from source.  Probably not the right way, but now I've gotten a lot further, but still can't access the library from my iPhone.  What I've done since then is to create a new user just for this, music_manager.  I then set the permissions for /var/logs/forked-daapd.log to music_manager:music_manager.  I also did this for /var/cache/forked-daapd.  I modified the /etc/forked-daapd.conf file to change uid= to music_manager, ipv6 = to no, direcories to the path of my music files, and left everything else the default answer.  After this I ran into the first issue.  Mpd would fatally not start.  After some research I found that it conflicts somehow (port?) with forked-daapd.  I stopped the MPD service, then was able to successfully start forked-daapd.  After rebooting I have this problem again.  Do I need to change the port that mpd uses to be the same as what forked-daapd uses, or vise versa?  

The second issue is that after starting, I am no able to see my library from my iPhone.  Supposedly forked-daapd allows you to see the music server from Airplay and iTunes and other stuff, but I can't.  However, I can see the server from an app I downloaded, SimpleDaap.  However, after clicking on my server in the app, I get nothing, no artists, no albums, no nuttin.  Below is the output from the /var/log/forked-daapd.log.

2018-11-04 08:05:15] [  LOG]     main: Forked Media Server Version 25.0 taking off
[2018-11-04 08:05:15] [  LOG]     main: Built Jul 28 2018 with: --enable-itunes --enable-lastfm --enable-chromecast --enable-mpd --enable-verification --with-alsa --with-pulseaudio
[2018-11-04 08:05:15] [  LOG]     main: mDNS init
[2018-11-04 08:05:15] [  LOG]     mdns: Avahi state change: Client running
[2018-11-04 08:05:15] [  LOG]       db: Now vacuuming database, this may take some time...
[2018-11-04 08:05:15] [  LOG]       db: Database OK with 0 active files and 6 active playlists
[2018-11-04 08:05:15] [  LOG]   laudio: Pulseaudio failed with error: Connection refused
[2018-11-04 08:05:15] [  LOG]   laudio: Error initializing Pulseaudio: Connection refused
[2018-11-04 08:05:19] [  LOG]     scan: Scanned 200 files...
                     - deleted unneccesary scan results

[2018-11-04 08:10:05] [  LOG]       db: BUG: dbmfi column map out of sync with schema
[2018-11-04 08:10:05] [  LOG]     daap: Error fetching results
[2018-11-04 08:10:05] [  LOG]       db: BUG: dbpli column map out of sync with schema
[2018-11-04 08:10:05] [  LOG]     daap: Error fetching results
[2018-11-04 08:10:06] [  LOG]       db: BUG: dbmfi column map out of sync with schema
[2018-11-04 08:10:06] [  LOG]     daap: Error fetching results
[2018-11-04 08:10:07] [  LOG]       db: BUG: dbpli column map out of sync with schema
[2018-11-04 08:10:07] [  LOG]     daap: Error fetching results
[2018-11-04 08:10:55] [  LOG]     scan: Bulk library scan completed in 340 sec
[2018-11-04 08:10:55] [  LOG]      lib: Library init scan completed in 340 sec
[2018-11-04 08:11:05] [  LOG]    cache: Beginning DAAP cache update
[2018-11-04 08:11:05] [  LOG]    cache: DAAP cache updated

I'm assuming that the issue with no library is the db:BUG: statements in the log.  I know a little bit about MS SQL.  I don't know anything about Sqlite.

---

### Post by TechnoJunky on 2018-11-04
FYI, the db:Bug lines don't show up until I try to connect to the server using SimpleDaap.

---

### Post by ejurgensen on 2018-11-06
It is probably because you downgraded forked-daapd, so the database isn't valid any more. Just stop forked-daapd, delete /var/cache/forked-daapd/songs3.db and restart. It should be recreated. I'm not sure SimpleDaap works, better to try with Remote.

---

### Post by TechnoJunky on 2018-11-06
That fixed it.  But this is not what I was looking for.  I want a media server that allows me, and others in the house, to connect to it and listen to it on our phones.  The description for forked-daapd made it sound like it would act like iTunes and allow me to connect to it to listen.  However this seems more like a radio station, where I tell the server to play this or that and others can listen in via Safari, or I can have it pushed to an Apple TV.  I want something that allows you to pick what you want to listen to and allows others to pick what they want.  :(

---

### Post by TechnoJunky on 2018-11-07
Like I said, this isn't exactly what I'm looking for but since I have it setup, I'm going to try using it for now till I find something better.  In the documentation, it says that for IOS, you have to connect using Safari.  I've done that but it disconnects or stops after 1 minute.  I then have to refresh the link.  Just clicking the play button does nothing, I have to click the arrowed circle (F5 on a keyboard).  Do I have some setting wrong?  I looked in the config file but couldn't find anything related to disconnecting after 1 minute.

---

