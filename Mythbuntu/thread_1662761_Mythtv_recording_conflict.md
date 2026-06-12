---
title: "Mythtv recording conflict"
date: 2011-01-08
forum: Mythbuntu
---

### Post by DominicF on 2011-01-08
Hi,

I have a 3 tuner setup comprising of a single tuner Satellite card and a dual tuner DVB-T card(Hauppauge DVB-T500) running mythtv 0.23-fixes.  When I try to schedule a recording using the Program Guide (EPG) for DVB-T broadcasts on 2 different channels say channel4 and BBC Three at overlapping times I get a recording conflict despite having 2 DVB-T tuners available to me.  The first program records but the second has a conflict.  I've tried to specify specific tuner inputs in the Edit Option screen when you view "upcoming recordings" but it doesn't make a difference.  

Has anyone experienced this and managed to solve this type of problem?

---

### Post by newlinux on 2011-01-08
Are  all tuners functioning properly? This can happen if there is an error with one tuner. are the sources for the tuners set up with the proper channels?

when you schedule these programs what does it tell you the conflict is (check your logs).

---

### Post by DominicF on 2011-01-09
Hi,

The frontend and backend logs doesn't list anything as conflicting, i.e. I searched for the key word "conflict".

I'm running a test at the moment, the first channel is currently recording (I can view the recording from Media Library), the second channel it set to record a program in an hour.  I've tested the second tuner to watch live TV, so this tuner is working.

In Upcoming Recordings screen, it tells me I have a conflict today, and shows my second channel/recording has the tag "C".  

The current recording has priority of "3".

I've changed the priorities of the conflicting recording to be higher and lower but it still shows as conflicting.

---

### Post by newlinux on 2011-01-09
"C" indicates that there are more overlapping shows to record than there are TV tuners that can record them, which shouldn't be the case.

Did you check your video sources? Do both tuners you are trying to use have the same source? Can you tune livetv to the channel you want to record on the second tuner? Can you do this same thing when the first tuner is recording something? Just out of curiousity do your have your DVB-Tuners set up to use multirecord?

For more information in your logs, run mythbackend with the "-v schedule" flag. It would be helpful to see the relevant portions of your backend logs.

---

### Post by ozybushwalker on 2011-01-09
I have two PCI tuners with the aerial lead daisy chained between the two tuners (card 1 has antenna in and out connectors, card 2 antenna in only). ABC doesn't show up on the channel scan on the second tuner. I know this only because I have carefully watched the channel scan. I haven't come across an obvious way to see what channels are available on what tuners. At first I thought all channels were available on all tuners. Thus I was puzzled when I saw conflicts when tuner 1 was recording a show and I tried to record a show on ABC that started before the show on tuner 1 finished.

Another source of conflict I came across was due to the use of non-zero "start before" and "finish after" times.

---

### Post by vidtek on 2011-10-09
> **newlinux said:**
> "C" indicates that there are more overlapping shows to record than there are TV tuners that can record them, which shouldn't be the case.

Did you check your video sources? Do both tuners you are trying to use have the same source? Can you tune livetv to the channel you want to record on the second tuner? Can you do this same thing when the first tuner is recording something? Just out of curiousity do your have your DVB-Tuners set up to use multirecord?

For more information in your logs, run mythbackend with the "-v schedule" flag. It would be helpful to see the relevant portions of your backend logs.

I have a similar problem, although maybe a clue to the origin of this behavior could be that on my system I can record multiple (up to 6 simultaneous different channel recordings on 6 tuners) as live recordings.  When I attempt a schedule recording I can only do a single channel otherwise I get a conflict.  So it appears with my problem at least, it's the scheduling side of Mythtv that's faulty.

Tried all sorts of fixes but it persists, I've deleted all tuners and video sources and redone them until I'm blue in the face (after rebooting) I've even deleted the tuner drivers and started from scratch.

Anyone any ideas?

Tony.

---

### Post by newlinux on 2011-10-09
Do all your tuners use the same video source? How have you configured their input groups? What does the myth upcoming recording screen say is the reason the recordings won't happen at the same time? Next up is seeing the logs...

---

### Post by vidtek on 2011-10-09
> **newlinux said:**
> Do all your tuners use the same video source? How have you configured their input groups? What does the myth upcoming recording screen say is the reason the recordings won't happen at the same time? Next up is seeing the logs...

Newlinux, many thanks for thr reply.

No, each tuner has it's own source.  I have configured each video source  to it's own input group.

I have a gut feeling this is where the problem lies-input groups and video sources with scheduling.

The upcoming recordings screen says it won't be recorded as there is a conflict.
The first recording is fine, it just won't do simultaneous recordings, although live simultaneous is fine.
Seems weird to me, must be something in the scheduling side I haven't yet grasped.

Best regards, Tony.

---

### Post by nickrout on 2011-10-09
> **vidtek said:**
> Newlinux, many thanks for thr reply.

No, each tuner has it's own source.  I have configured each video source  to it's own input group.

I have a gut feeling this is where the problem lies-input groups and video sources with scheduling.

The upcoming recordings screen says it won't be recorded as there is a conflict.
The first recording is fine, it just won't do simultaneous recordings, although live simultaneous is fine.
Seems weird to me, must be something in the scheduling side I haven't yet grasped.

Best regards, Tony.

If both tuners access the same programming then they should use the same video source.

---

### Post by vidtek on 2011-10-10
> **nickrout said:**
> If both tuners access the same programming then they should use the same video source.

Nickrout-  Thank you for the reply.  I'm not sure I understand you correctly-you mean setup the input groups to one single video source?  i.e. my Hauppauge 2200 has 2 tuners onboard, set both to the same video source?

I'll give it a go and report back, I'll try anything now.

Best regards, Tony.

---

### Post by vidtek on 2011-10-10
> **vidtek said:**
> Nickrout-  Thank you for the reply.  I'm not sure I understand you correctly-you mean setup the input groups to one single video source?  i.e. my Hauppauge 2200 has 2 tuners onboard, set both to the same video source?

I'll give it a go and report back, I'll try anything now.

Best regards, Tony.

Update-

No  ---  tried putting the same video source for the 2200 tuners and no change see screenshot of upcoming recordings screen as an attachment, here is the backend log.

2011-10-10 15:50:13.967 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-10-10 15:50:13.977 Using runtime prefix = /usr
2011-10-10 15:50:13.977 Using configuration directory = /home/mythtv/.mythtv
2011-10-10 15:50:13.979 Using localhost value of mythbuntu
2011-10-10 15:50:14.090 New DB connection, total: 1
2011-10-10 15:50:14.093 Connected to database 'mythconverg' at host: 192.168.0.42
2011-10-10 15:50:14.098 Closing DB connection named 'DBManager0'
2011-10-10 15:50:14.100 Connected to database 'mythconverg' at host: 192.168.0.42
2011-10-10 15:50:14.102 Current locale en_GB
2011-10-10 15:50:14.103 Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2011-10-10 15:50:14.109 Current MythTV Schema Version (DBSchemaVer): 1264
2011-10-10 15:50:14.113 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-10-10 15:50:14.123 Enabling Upnpmedia rebuild thread.
2011-10-10 15:50:15.326 MythBackend: Starting up as the master server.
2011-10-10 15:50:15.331 New DB connection, total: 2
2011-10-10 15:50:15.333 Connected to database 'mythconverg' at host: 192.168.0.42
2011-10-10 15:50:15.334 mythbackend: MythBackend started as master server
2011-10-10 15:50:15.508 New DB connection, total: 3
2011-10-10 15:50:15.510 Connected to database 'mythconverg' at host: 192.168.0.42
2011-10-10 15:50:16.611 New DB scheduler connection
2011-10-10 15:50:16.613 Connected to database 'mythconverg' at host: 192.168.0.42
2011-10-10 15:50:16.616 Scheduler, Warning: Listings source 'DVB2' is defined, but is not attached to a card input.
2011-10-10 15:50:16.618 Main::Registering HttpStatus Extension
2011-10-10 15:50:16.619 Enabled verbose msgs:  important general
2011-10-10 15:50:16.624 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-10-10 15:50:17.410 adding: workshopserver as a slave backend server
2011-10-10 15:50:19.619 Reschedule requested for id -1.
2011-10-10 15:50:19.667 Scheduled 5 items in 0.0 = 0.01 match + 0.03 place
2011-10-10 15:50:19.670 scheduler: Scheduled items: Scheduled 5 items in 0.0 = 0.01 match + 0.03 place
2011-10-10 15:50:19.675 Seem to be woken up by USER
2011-10-10 15:50:23.422 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-10-10 15:50:24.125 UPnpMedia: BuildMediaMap VIDEO scan starting in :/192.168.0.13/record:
2011-10-10 15:50:24.136 UPnpMedia: BuildMediaMap Done. Found 0 objects
2011-10-10 15:50:26.622 mythbackend: Running housekeeping thread
2011-10-10 15:50:34.411 MainServer::ANN Monitor
2011-10-10 15:50:34.428 adding: mythbuntu as a client (events: 0)
2011-10-10 15:50:34.429 MainServer::ANN Monitor
2011-10-10 15:50:34.446 adding: mythbuntu as a client (events: 1)
2011-10-10 15:50:34.447 Reschedule requested for id -1.
2011-10-10 15:50:34.489 Scheduled 5 items in 0.0 = 0.00 match + 0.03 place
2011-10-10 15:50:34.492 scheduler: Scheduled items: Scheduled 5 items in 0.0 = 0.00 match + 0.03 place
2011-10-10 15:50:40.790 MainServer::ANN Monitor
2011-10-10 15:50:40.791 adding: mythbuntu as a client (events: 0)
2011-10-10 15:50:40.792 MainServer::ANN Monitor
2011-10-10 15:50:40.805 adding: mythbuntu as a client (events: 1)
2011-10-10 15:50:53.021 Reschedule requested for id 226.
2011-10-10 15:50:53.047 Scheduled 4 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:50:53.051 scheduler: Scheduled items: Scheduled 4 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:50:53.437 Reschedule requested for id 223.
2011-10-10 15:50:53.462 Scheduled 3 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:50:53.465 scheduler: Scheduled items: Scheduled 3 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:50:53.717 Reschedule requested for id 224.
2011-10-10 15:50:53.741 Scheduled 2 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:50:53.744 scheduler: Scheduled items: Scheduled 2 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:50:53.933 Reschedule requested for id 225.
2011-10-10 15:50:53.952 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2011-10-10 15:50:53.955 scheduler: Scheduled items: Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2011-10-10 15:50:54.212 Reschedule requested for id 227.
2011-10-10 15:50:54.230 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2011-10-10 15:50:54.233 scheduler: Scheduled items: Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2011-10-10 15:51:36.627 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-10-10 15:52:19.788 Reschedule requested for id 228.
2011-10-10 15:52:19.827 Scheduled 1 items in 0.0 = 0.02 match + 0.02 place
2011-10-10 15:52:19.836 scheduler: Scheduled items: Scheduled 1 items in 0.0 = 0.02 match + 0.02 place
2011-10-10 15:52:20.227 MainServer::ANN Monitor
2011-10-10 15:52:20.276 adding: mythbuntu as a client (events: 0)
2011-10-10 15:52:20.278 MainServer::ANN Monitor
2011-10-10 15:52:20.278 adding: mythbuntu as a client (events: 1)
2011-10-10 15:52:20.280 Reschedule requested for id -1.
2011-10-10 15:52:20.309 Scheduled 1 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:52:20.313 scheduler: Scheduled items: Scheduled 1 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:52:25.492 Reschedule requested for id 229.
2011-10-10 15:52:25.517 Scheduled 2 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:52:25.521 scheduler: Scheduled items: Scheduled 2 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:52:28.396 Reschedule requested for id 230.
2011-10-10 15:52:28.421 Scheduled 3 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:52:28.425 scheduler: Scheduled items: Scheduled 3 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:52:32.380 Reschedule requested for id 231.
2011-10-10 15:52:32.405 Scheduled 4 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:52:32.409 scheduler: Scheduled items: Scheduled 4 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:53:40.924 Reschedule requested for id 232.
2011-10-10 15:53:40.956 Scheduled 5 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:53:40.959 scheduler: Scheduled items: Scheduled 5 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:53:54.355 MainServer::ANN Monitor
2011-10-10 15:53:54.376 adding: workshopserver as a client (events: 0)
2011-10-10 15:53:54.377 MainServer::ANN Monitor
2011-10-10 15:53:54.378 adding: workshopserver as a client (events: 1)
2011-10-10 15:53:54.379 Reschedule requested for id -1.
2011-10-10 15:53:54.419 Scheduled 5 items in 0.0 = 0.00 match + 0.03 place
2011-10-10 15:53:54.423 scheduler: Scheduled items: Scheduled 5 items in 0.0 = 0.00 match + 0.03 place
2011-10-10 15:53:54.956 Reschedule requested for id 228.
2011-10-10 15:53:54.982 Scheduled 4 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:53:54.985 scheduler: Scheduled items: Scheduled 4 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:55:17.483 Reschedule requested for id 232.
2011-10-10 15:55:17.511 Scheduled 4 items in 0.0 = 0.00 match + 0.02 place
2011-10-10 15:55:29.375 MainServer::ANN Monitor
2011-10-10 15:55:29.377 adding: workshopserver as a client (events: 0)
2011-10-10 15:55:29.381 MainServer::ANN Monitor
2011-10-10 15:55:29.382 adding: workshopserver as a client (events: 1)

Tony

---

### Post by vidtek on 2011-10-10
OK got mine sorted.  See the jpg attached

Not sure if it was the video sources or something else.

I read on a thread somewhere never to run mythfilldatabase on a slave backend.  Since then I haven't done so.

I just ran mythfilldatabase on my slave backend and hey presto-no more conflicts!

Surely it can't be that simple?

Hope this helps someone out there.

All the best to all who helped.

Tony.

---

