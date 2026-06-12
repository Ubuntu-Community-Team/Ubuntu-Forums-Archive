---
title: "MythTV and Cable Box help"
date: 2010-06-29
forum: Mythbuntu
---

### Post by LowSky on 2010-06-29
I have a Scientific Atlanta 4250HD cable box from Cablevision (in NY). I connected to it using these setting in MythTV p2p 400mbps firewire, and it worked fine on its first recording, but then it started having issues.

Basically it can change channels just fine, but it wont record the channel be it channel 2, 4, 50, or 800. I figure somethings might be blocked but I would love some help. Clearly its changing channels so Firewire port does work on the Cable box.

I looked around the internet and nearly everything is from a few years ago so I'm not sure if it might be helpful. Even the Ubuntu guides are for MythTv .21 and under.

I've already tried rebooting the HTPC, rebooting the Cable box, and even deleting the settings in MythTV and re-adding them again.

Oh and what is P2P and broadcast even mean, no one ever defines the difference.

---

### Post by ian dobson on 2010-06-29
Hi,

p2p is point to point in this case (ie one "wire" with a device at each end).

With regards to you problem, what do you see in your backend log file when you try and record something? (/var/log/mythbackend.log)

Regards
Ian Dobson

---

### Post by Lepy on 2010-06-29
I've never used mythtv with firewire but is it possible that some of the channels you are trying to record have the 5c(?) encryption flag?

Or, did I misunderstand and your first recording will always work, while subsequent recordings do not.

In any case, the backend log should give you a clue as to what is happening.

---

### Post by LowSky on 2010-06-29
I figured some channels will have encryption, like premium...

And  Lepy only the first recording I tried actually worked. Every attemp after has failed. 

When I get home I will look at the log. If I can't get this working, I know a work around. It's buying a [Hauppauge HD PVR ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116030")

---

### Post by LowSky on 2010-06-29
I grabed the log file from  /var/log/mythtv/mythbackend.log

heres what I got going on, anyone know how to decode this:
```
2010-06-29 07:39:30.182 MainServer::ANN Monitor
2010-06-29 07:39:30.182 adding: Media-Server as a client (events: 0)
2010-06-29 07:39:30.463 MainServer::ANN Monitor
2010-06-29 07:39:30.469 adding: Media-Server as a client (events: 0)
2010-06-29 07:39:48.135 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:39:48.142 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:40:01.976 MainServer::ANN Monitor
2010-06-29 07:40:01.983 adding: Media-Server as a client (events: 0)
2010-06-29 07:40:26.339 MainServer::ANN Monitor
2010-06-29 07:40:26.349 adding: Media-Server as a client (events: 0)
2010-06-29 07:40:49.151 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:40:49.163 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:41:55.173 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:41:55.178 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:41:55.712 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 07:42:56.187 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:42:56.199 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:44:03.208 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:44:03.217 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:45:05.226 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:45:05.233 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:46:05.243 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:46:05.251 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:47:12.261 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:47:12.269 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:48:17.278 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:48:17.288 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:49:23.297 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:49:23.302 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:50:01.670 MainServer::ANN Monitor
2010-06-29 07:50:01.683 adding: Media-Server as a client (events: 0)
2010-06-29 07:50:24.311 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:50:24.323 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:51:25.333 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:51:25.345 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:52:26.354 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:52:26.366 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:53:32.376 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:53:32.380 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:54:33.390 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:54:33.402 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:55:33.411 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:55:33.420 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:56:37.429 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:56:37.435 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:56:55.762 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 07:57:43.445 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:57:43.449 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:58:44.459 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:58:44.471 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 07:59:44.480 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 07:59:44.489 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:00:02.218 MainServer::ANN Monitor
2010-06-29 08:00:02.227 adding: Media-Server as a client (events: 0)
2010-06-29 08:00:47.525 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:00:47.533 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:01:48.542 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:01:48.554 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:02:49.563 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:02:49.576 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:03:52.585 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:03:52.596 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:04:53.605 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:04:53.618 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:06:00.627 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:06:00.635 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:07:07.644 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:07:07.653 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:08:13.662 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:08:13.675 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:09:18.684 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:09:18.694 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:10:01.787 MainServer::ANN Monitor
2010-06-29 08:10:01.793 adding: Media-Server as a client (events: 0)
2010-06-29 08:10:25.703 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:10:25.711 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:11:26.721 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:11:26.733 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:11:55.819 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 08:12:28.742 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:12:28.750 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:13:30.759 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:13:30.766 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:14:35.776 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:14:35.785 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:15:39.794 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:15:39.801 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:16:42.810 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:16:42.821 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:17:02.077 MainServer::ANN Monitor
2010-06-29 08:17:02.086 adding: Media-Server as a client (events: 0)
2010-06-29 08:17:02.231 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 08:17:02.237 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 08:17:02.245 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 08:17:46.830 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:17:46.836 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:18:49.846 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:18:49.856 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:19:52.866 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:19:52.877 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:20:02.059 MainServer::ANN Monitor
2010-06-29 08:20:02.065 adding: Media-Server as a client (events: 0)
2010-06-29 08:20:55.903 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:20:55.914 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:22:02.923 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:22:02.931 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:23:03.940 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:23:03.953 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:24:05.962 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:24:05.969 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:25:11.979 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:25:11.992 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:26:18.001 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:26:18.014 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:26:55.871 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 08:27:20.023 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:27:20.031 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:28:27.040 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:28:27.048 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:29:30.057 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:29:30.069 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:30:01.606 MainServer::ANN Monitor
2010-06-29 08:30:01.616 adding: Media-Server as a client (events: 0)
2010-06-29 08:30:36.078 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:30:36.091 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:31:40.100 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:31:40.106 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:32:40.116 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:32:40.124 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:33:40.134 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:33:40.142 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:34:45.152 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:34:45.161 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:35:51.171 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:35:51.184 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:36:56.193 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:36:56.203 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:37:59.212 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:37:59.223 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:38:59.232 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:38:59.241 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:40:00.250 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:40:00.263 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:40:02.171 MainServer::ANN Monitor
2010-06-29 08:40:02.178 adding: Media-Server as a client (events: 0)
2010-06-29 08:41:04.272 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:41:04.278 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:41:55.927 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 08:42:05.287 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:42:05.300 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:43:09.324 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:43:09.332 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:44:10.341 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:44:10.353 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:45:15.362 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:45:15.372 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:46:20.381 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:46:20.391 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:47:27.400 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:47:27.408 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:48:33.418 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:48:33.431 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:49:37.440 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:49:37.446 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:50:01.716 MainServer::ANN Monitor
2010-06-29 08:50:01.729 adding: Media-Server as a client (events: 0)
2010-06-29 08:50:40.455 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:50:40.466 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:51:46.476 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:51:46.489 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:52:51.498 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:52:51.508 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:53:55.517 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:53:55.523 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:55:02.532 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:55:02.541 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:56:02.550 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:56:02.559 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:56:55.980 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 08:57:08.568 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:57:08.581 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:58:08.590 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:58:08.599 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 08:59:08.608 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 08:59:08.617 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:00:02.265 MainServer::ANN Monitor
2010-06-29 09:00:02.274 adding: Media-Server as a client (events: 0)
2010-06-29 09:00:11.626 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:00:11.637 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:01:12.647 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:01:12.659 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:02:19.668 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:02:19.677 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:03:25.686 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:03:25.691 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:04:30.700 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:04:30.709 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:05:37.719 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:05:37.727 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:06:39.736 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:06:39.763 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:07:44.770 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:07:44.779 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:08:51.788 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:08:51.797 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:09:58.806 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:09:58.814 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:10:01.833 MainServer::ANN Monitor
2010-06-29 09:10:01.841 adding: Media-Server as a client (events: 0)
2010-06-29 09:11:02.824 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:11:02.830 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:11:56.038 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 09:12:07.839 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:12:07.849 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:13:09.858 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:13:09.865 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:14:09.875 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:14:09.884 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:15:16.893 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:15:16.901 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:16:20.910 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:16:20.916 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:17:02.140 MainServer::ANN Monitor
2010-06-29 09:17:02.150 adding: Media-Server as a client (events: 0)
2010-06-29 09:17:02.292 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 09:17:02.301 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 09:17:02.309 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 09:17:21.926 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:17:21.938 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:18:25.947 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:18:25.953 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:19:32.963 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:19:32.971 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:20:01.664 MainServer::ANN Monitor
2010-06-29 09:20:01.674 adding: Media-Server as a client (events: 0)
2010-06-29 09:20:38.980 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:20:38.993 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:21:44.003 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:21:44.012 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:22:49.021 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:22:49.031 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:23:51.040 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:23:51.048 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:24:53.057 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:24:53.065 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:25:58.074 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:25:58.083 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:26:56.088 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 09:27:00.093 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:27:00.100 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:28:06.110 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:28:06.123 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:29:08.132 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:29:08.139 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:30:02.227 MainServer::ANN Monitor
2010-06-29 09:30:02.236 adding: Media-Server as a client (events: 0)
2010-06-29 09:30:14.149 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:30:14.162 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:31:18.171 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:31:18.177 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:32:21.186 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:32:21.197 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:33:28.207 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:33:28.215 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:34:30.224 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:34:30.232 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:35:33.241 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:35:33.252 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:36:37.261 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:36:37.277 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:37:43.293 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:37:43.306 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:38:50.316 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:38:50.324 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:39:54.333 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:39:54.339 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:40:01.794 MainServer::ANN Monitor
2010-06-29 09:40:01.803 adding: Media-Server as a client (events: 0)
2010-06-29 09:41:00.348 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:41:00.362 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:41:56.158 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 09:42:02.371 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:42:02.378 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:43:05.388 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:43:05.399 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:44:10.408 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:44:10.417 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:45:17.427 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:45:17.435 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:46:21.444 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:46:21.450 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:47:24.460 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:47:24.471 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:48:28.480 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:48:28.486 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:49:32.495 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:49:32.501 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:50:02.346 MainServer::ANN Monitor
2010-06-29 09:50:02.377 adding: Media-Server as a client (events: 0)
2010-06-29 09:50:38.511 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:50:38.524 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:51:45.533 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:51:45.541 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:52:47.551 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:52:47.558 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:53:54.567 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:53:54.576 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:55:00.585 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:55:00.598 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:56:04.607 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:56:04.614 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:56:56.210 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 09:57:05.623 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:57:05.635 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:58:08.644 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:58:08.655 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 09:59:13.664 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 09:59:13.674 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:00:01.917 MainServer::ANN Monitor
2010-06-29 10:00:01.924 adding: Media-Server as a client (events: 0)
2010-06-29 10:00:13.683 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:00:13.692 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:01:18.701 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:01:18.711 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:02:20.720 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:02:20.728 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:03:27.737 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:03:27.745 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:04:31.755 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:04:31.761 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:05:34.770 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:05:34.788 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:06:39.807 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:06:39.817 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:07:39.826 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:07:39.835 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:08:42.844 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:08:42.855 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:09:44.864 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:09:44.872 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:10:01.487 MainServer::ANN Monitor
2010-06-29 10:10:01.499 adding: Media-Server as a client (events: 0)
2010-06-29 10:10:50.881 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:10:50.886 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:11:55.895 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:11:55.905 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:11:56.270 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 10:13:01.914 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:13:01.954 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:14:04.963 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:14:04.974 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:15:08.984 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:15:08.990 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:16:08.999 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:16:09.008 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:17:01.785 MainServer::ANN Monitor
2010-06-29 10:17:01.794 adding: Media-Server as a client (events: 0)
2010-06-29 10:17:01.938 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 10:17:01.945 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 10:17:01.953 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 10:17:15.017 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:17:15.030 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:18:21.039 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:18:21.053 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:19:28.062 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:19:28.070 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:20:01.907 MainServer::ANN Monitor
2010-06-29 10:20:01.915 adding: Media-Server as a client (events: 0)
2010-06-29 10:20:34.079 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:20:34.093 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:21:40.102 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:21:40.107 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:22:44.116 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:22:44.122 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:23:46.131 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:23:46.139 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:24:49.148 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:24:49.159 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:25:54.168 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:25:54.178 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:26:56.324 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 10:26:58.187 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:26:58.193 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:28:01.203 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:28:01.214 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:29:07.223 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:29:07.236 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:30:01.475 MainServer::ANN Monitor
2010-06-29 10:30:01.482 adding: Media-Server as a client (events: 0)
2010-06-29 10:30:12.245 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:30:12.255 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:31:15.264 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:31:15.275 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:32:21.284 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:32:21.298 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:33:24.307 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:33:24.338 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:34:27.349 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:34:27.361 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:35:32.370 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:35:32.379 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:36:32.389 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:36:32.397 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:37:38.407 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:37:38.420 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:38:41.429 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:38:41.440 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:39:43.449 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:39:43.457 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:40:02.038 MainServer::ANN Monitor
2010-06-29 10:40:02.050 adding: Media-Server as a client (events: 0)
2010-06-29 10:40:46.466 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:40:46.477 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:41:49.486 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:41:49.497 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:41:56.383 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 10:42:49.507 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:42:49.515 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:43:51.525 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:43:51.532 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:44:55.541 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:44:55.548 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:45:56.557 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:45:56.569 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:46:59.578 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:46:59.589 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:48:05.599 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:48:05.612 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:49:05.621 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:49:05.630 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:50:01.602 MainServer::ANN Monitor
2010-06-29 10:50:01.609 adding: Media-Server as a client (events: 0)
2010-06-29 10:50:11.639 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:50:11.644 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:51:18.653 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:51:18.661 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:52:20.670 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:52:20.678 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:53:27.687 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:53:27.696 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:54:34.705 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:54:34.713 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:55:40.722 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:55:40.736 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:56:41.745 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:56:41.757 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:56:56.434 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 10:57:46.786 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:57:46.793 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:58:48.802 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:58:48.809 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 10:59:53.819 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 10:59:53.828 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:00:02.174 MainServer::ANN Monitor
2010-06-29 11:00:02.179 adding: Media-Server as a client (events: 0)
2010-06-29 11:00:57.838 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:00:57.844 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:02:03.853 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:02:03.866 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:03:09.875 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:03:09.889 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:04:12.898 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:04:12.909 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:05:15.918 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:05:15.929 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:06:18.938 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:06:18.949 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:07:18.958 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:07:18.967 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:08:19.976 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:08:19.989 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:09:24.998 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:09:25.008 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:10:01.736 MainServer::ANN Monitor
2010-06-29 11:10:01.746 adding: Media-Server as a client (events: 0)
2010-06-29 11:10:26.017 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:10:26.029 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:11:29.038 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:11:29.050 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:11:56.491 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 11:12:34.059 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:12:34.068 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:13:35.078 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:13:35.090 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:14:36.099 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:14:36.112 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:15:37.121 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:15:37.133 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:16:44.142 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:16:44.151 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:17:02.027 MainServer::ANN Monitor
2010-06-29 11:17:02.039 adding: Media-Server as a client (events: 0)
2010-06-29 11:17:02.173 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 11:17:02.181 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 11:17:02.239 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 11:17:47.160 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:17:47.172 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:18:51.181 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:18:51.188 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:19:58.197 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:19:58.205 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:20:02.148 MainServer::ANN Monitor
2010-06-29 11:20:02.161 adding: Media-Server as a client (events: 0)
2010-06-29 11:20:58.214 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:20:58.223 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:22:01.232 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:22:01.243 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:23:06.253 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:23:06.262 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:24:12.271 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:24:12.276 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:25:17.286 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:25:17.295 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:26:19.305 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:26:19.312 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:26:56.544 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 11:27:20.321 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:27:20.334 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:28:22.343 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:28:22.350 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:29:23.359 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:29:23.372 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:30:01.702 MainServer::ANN Monitor
2010-06-29 11:30:01.711 adding: Media-Server as a client (events: 0)
2010-06-29 11:30:28.381 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:30:28.391 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:31:33.400 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:31:33.410 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:32:38.419 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:32:38.429 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:33:44.438 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:33:44.451 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:34:49.460 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:34:49.470 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:35:49.479 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:35:49.488 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:36:51.497 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:36:51.505 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:37:51.514 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:37:51.523 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:38:52.532 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:38:52.544 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:39:58.553 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:39:58.596 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:40:02.266 MainServer::ANN Monitor
2010-06-29 11:40:02.272 adding: Media-Server as a client (events: 0)
2010-06-29 11:41:04.608 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:41:04.621 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:41:56.603 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 11:42:10.630 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:42:10.643 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:43:12.653 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:43:12.660 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:44:14.669 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:44:14.677 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:45:21.686 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:45:21.694 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:46:24.704 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:46:24.715 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:47:31.724 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:47:31.732 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:48:32.741 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:48:32.754 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:49:35.763 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:49:35.774 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:50:01.818 MainServer::ANN Monitor
2010-06-29 11:50:01.831 adding: Media-Server as a client (events: 0)
2010-06-29 11:50:35.783 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:50:35.792 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:51:37.801 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:51:37.809 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:52:44.818 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:52:44.826 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:53:48.836 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:53:48.842 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:54:55.851 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:54:55.859 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:55:56.869 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:55:56.881 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:56:56.658 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 11:56:58.890 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:56:58.898 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:58:04.907 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:58:04.920 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 11:59:11.929 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 11:59:11.938 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:00:02.362 MainServer::ANN Monitor
2010-06-29 12:00:02.369 adding: Media-Server as a client (events: 0)
2010-06-29 12:00:14.947 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:00:14.958 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:01:16.967 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:01:16.975 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:02:16.984 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:02:17.010 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:03:20.043 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:03:20.054 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:04:24.064 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:04:24.070 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:05:25.079 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:05:25.091 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:06:28.101 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:06:28.112 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:07:33.121 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:07:33.131 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:08:35.140 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:08:35.147 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:09:41.157 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:09:41.170 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:10:01.925 MainServer::ANN Monitor
2010-06-29 12:10:01.936 adding: Media-Server as a client (events: 0)
2010-06-29 12:10:47.179 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:10:47.184 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:11:52.193 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:11:52.203 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:11:56.713 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 12:12:52.212 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:12:52.221 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:13:54.230 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:13:54.237 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:14:56.247 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:14:56.254 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:16:03.263 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:16:03.272 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:17:01.235 MainServer::ANN Monitor
2010-06-29 12:17:01.241 adding: Media-Server as a client (events: 0)
2010-06-29 12:17:01.392 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 12:17:01.401 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 12:17:01.409 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 12:17:05.281 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:17:05.288 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:18:05.298 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:18:05.307 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:19:11.316 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:19:11.329 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:20:01.460 MainServer::ANN Monitor
2010-06-29 12:20:01.469 adding: Media-Server as a client (events: 0)
2010-06-29 12:20:18.338 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:20:18.346 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:21:22.356 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:21:22.362 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:22:25.371 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:22:25.396 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:23:25.408 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:23:25.417 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:24:28.426 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:24:28.437 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:25:31.446 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:25:31.457 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:26:38.466 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:26:38.475 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:26:56.768 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 12:27:44.484 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:27:44.497 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:28:45.506 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:28:45.519 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:29:47.528 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:29:47.535 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:30:01.998 MainServer::ANN Monitor
2010-06-29 12:30:02.007 adding: Media-Server as a client (events: 0)
2010-06-29 12:30:50.545 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:30:50.556 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:31:57.565 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:31:57.573 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:33:04.582 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:33:04.591 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:34:11.600 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:34:11.608 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:35:17.617 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:35:17.631 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:36:20.640 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:36:20.651 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:37:27.660 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:37:27.668 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:38:31.678 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:38:31.684 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:39:31.693 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:39:31.702 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:40:01.578 MainServer::ANN Monitor
2010-06-29 12:40:01.590 adding: Media-Server as a client (events: 0)
2010-06-29 12:40:36.711 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:40:36.721 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:41:41.730 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:41:41.740 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:41:56.824 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 12:42:41.749 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:42:41.758 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:43:45.767 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:43:45.773 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:44:52.782 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:44:52.791 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:45:57.800 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:45:57.830 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:47:02.835 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:47:02.845 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:48:09.854 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:48:09.863 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:49:16.872 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:49:16.880 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:50:02.134 MainServer::ANN Monitor
2010-06-29 12:50:02.144 adding: Media-Server as a client (events: 0)
2010-06-29 12:50:20.889 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:50:20.896 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:51:25.905 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:51:25.915 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:52:25.924 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:52:25.933 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:53:27.942 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:53:27.949 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:54:32.959 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:54:32.968 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:55:33.977 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:55:33.990 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:56:34.999 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:56:35.011 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:56:56.878 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 12:57:38.021 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:57:38.032 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:58:41.041 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:58:41.052 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 12:59:42.061 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 12:59:42.073 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:00:01.688 MainServer::ANN Monitor
2010-06-29 13:00:01.695 adding: Media-Server as a client (events: 0)
2010-06-29 13:00:45.083 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:00:45.094 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:01:50.104 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:01:50.112 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:02:56.122 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:02:56.135 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:04:00.144 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:04:00.150 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:05:01.159 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:05:01.172 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:06:04.181 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:06:04.192 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:07:05.201 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:07:05.214 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:08:06.223 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:08:06.235 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:09:13.244 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:09:13.253 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:10:02.271 MainServer::ANN Monitor
2010-06-29 13:10:02.278 adding: Media-Server as a client (events: 0)
2010-06-29 13:10:15.281 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:10:15.291 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:11:21.300 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:11:21.313 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:11:56.937 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 13:12:28.323 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:12:28.331 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:13:31.340 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:13:31.351 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:14:32.360 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:14:32.372 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:15:32.382 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:15:32.391 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:16:33.400 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:16:33.412 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:17:01.560 MainServer::ANN Monitor
2010-06-29 13:17:01.567 adding: Media-Server as a client (events: 0)
2010-06-29 13:17:01.708 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 13:17:01.718 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 13:17:01.727 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 13:17:34.422 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:17:34.434 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:18:37.443 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:18:37.454 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:19:39.463 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:19:39.471 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:20:02.447 MainServer::ANN Monitor
2010-06-29 13:20:02.459 adding: Media-Server as a client (events: 0)
2010-06-29 13:20:46.480 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:20:46.488 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:21:51.497 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:21:51.507 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:22:53.516 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:22:53.524 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:24:00.533 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:24:00.541 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:25:04.551 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:25:04.557 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:26:04.566 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:26:04.575 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:26:56.991 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 13:27:07.584 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:27:07.595 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:28:08.604 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:28:08.617 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:29:10.626 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:29:10.660 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:30:01.992 MainServer::ANN Monitor
2010-06-29 13:30:01.999 adding: Media-Server as a client (events: 0)
2010-06-29 13:30:12.665 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:30:12.672 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:31:13.681 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:31:13.694 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:32:14.703 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:32:14.715 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:33:19.724 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:33:19.734 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:34:20.743 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:34:20.756 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:35:24.765 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:35:24.771 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:36:26.780 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:36:26.788 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:37:28.797 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:37:28.805 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:38:29.814 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:38:29.826 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:39:33.835 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:39:33.842 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:40:01.559 MainServer::ANN Monitor
2010-06-29 13:40:01.566 adding: Media-Server as a client (events: 0)
2010-06-29 13:40:40.851 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:40:40.859 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:41:46.868 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:41:46.881 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:41:57.055 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 13:42:50.891 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:42:50.897 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:43:53.906 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:43:53.917 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:45:00.926 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:45:00.935 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:46:07.944 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:46:07.952 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:47:07.961 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:47:07.970 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:48:13.980 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:48:13.993 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:49:21.002 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:49:21.010 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:50:02.111 MainServer::ANN Monitor
2010-06-29 13:50:02.119 adding: Media-Server as a client (events: 0)
2010-06-29 13:50:24.019 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:50:24.030 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:51:26.040 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:51:26.047 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:52:31.075 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:52:31.083 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:53:31.092 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:53:31.101 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:54:32.110 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:54:32.122 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:55:36.131 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:55:36.138 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:56:42.147 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:56:42.160 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:56:57.112 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 13:57:47.169 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:57:47.179 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:58:47.188 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:58:47.197 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 13:59:52.206 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 13:59:52.216 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:00:01.672 MainServer::ANN Monitor
2010-06-29 14:00:01.678 adding: Media-Server as a client (events: 0)
2010-06-29 14:00:58.225 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:00:58.238 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:02:00.247 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:02:00.255 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:03:01.264 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:03:01.276 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:04:04.285 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:04:04.296 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:05:10.306 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:05:10.319 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:06:16.328 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:06:16.341 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:07:19.350 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:07:19.361 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:08:24.370 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:08:24.380 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:09:25.389 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:09:25.402 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:10:02.248 MainServer::ANN Monitor
2010-06-29 14:10:02.257 adding: Media-Server as a client (events: 0)
2010-06-29 14:10:32.411 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:10:32.419 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:11:38.428 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:11:38.442 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:11:57.169 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 14:12:40.451 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:12:40.458 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:13:40.467 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:13:40.476 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:14:45.485 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:14:45.495 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:15:50.519 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:15:50.531 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:16:56.540 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:16:56.553 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:17:01.559 MainServer::ANN Monitor
2010-06-29 14:17:01.601 adding: Media-Server as a client (events: 0)
2010-06-29 14:17:01.752 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 14:17:01.763 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 14:17:01.770 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 14:18:00.562 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:18:00.568 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:19:03.578 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:19:03.589 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:20:01.919 MainServer::ANN Monitor
2010-06-29 14:20:01.931 adding: Media-Server as a client (events: 0)
2010-06-29 14:20:07.598 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:20:07.604 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:21:10.613 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:21:10.624 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:22:10.633 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:22:10.642 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:23:16.651 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:23:16.665 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:24:23.674 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:24:23.682 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:25:26.691 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:25:26.702 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:26:32.712 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:26:32.725 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:26:57.218 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 14:27:35.734 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:27:35.745 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:28:38.754 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:28:38.765 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:29:44.774 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:29:44.787 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:30:01.475 MainServer::ANN Monitor
2010-06-29 14:30:01.481 adding: Media-Server as a client (events: 0)
2010-06-29 14:30:46.797 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:30:46.804 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:31:49.813 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:31:49.824 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:32:49.833 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:32:49.842 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:33:52.852 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:33:52.863 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:34:59.872 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:34:59.880 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:35:59.902 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:35:59.915 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:37:06.924 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:37:06.932 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:38:09.941 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:38:09.953 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:39:14.962 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:39:14.971 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:40:02.040 MainServer::ANN Monitor
2010-06-29 14:40:02.052 adding: Media-Server as a client (events: 0)
2010-06-29 14:40:14.981 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:40:14.989 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:41:20.999 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:41:21.012 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:41:57.278 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 14:42:24.021 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:42:24.032 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:43:24.041 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:43:24.050 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:44:25.059 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:44:25.072 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:45:28.081 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:45:28.092 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:46:35.101 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:46:35.109 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:47:39.118 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:47:39.125 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:48:44.134 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:48:44.144 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:49:47.153 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:49:47.164 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:50:01.577 MainServer::ANN Monitor
2010-06-29 14:50:01.585 adding: Media-Server as a client (events: 0)
2010-06-29 14:50:51.173 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:50:51.179 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:51:51.189 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:51:51.197 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:52:51.206 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:52:51.215 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:53:51.225 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:53:51.233 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:54:52.243 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:54:52.255 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:55:52.264 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:55:52.273 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:56:57.333 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 14:56:59.282 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:56:59.291 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:58:05.300 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:58:05.330 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 14:59:09.339 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 14:59:09.345 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:00:02.148 MainServer::ANN Monitor
2010-06-29 15:00:02.156 adding: Media-Server as a client (events: 0)
2010-06-29 15:00:11.354 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:00:11.362 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:01:13.371 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:01:13.378 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:02:20.387 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:02:20.396 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:03:22.405 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:03:22.413 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:04:23.422 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:04:23.434 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:05:25.443 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:05:25.451 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:06:25.460 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:06:25.469 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:07:32.478 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:07:32.486 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:08:32.496 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:08:32.505 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:09:37.514 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:09:37.523 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:10:01.712 MainServer::ANN Monitor
2010-06-29 15:10:01.723 adding: Media-Server as a client (events: 0)
2010-06-29 15:10:37.533 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:10:37.541 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:11:41.551 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:11:41.557 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:11:57.388 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 15:12:43.566 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:12:43.574 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:13:50.583 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:13:50.591 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:14:54.600 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:14:54.606 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:15:59.616 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:15:59.625 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:17:02.010 MainServer::ANN Monitor
2010-06-29 15:17:02.040 adding: Media-Server as a client (events: 0)
2010-06-29 15:17:02.186 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 15:17:02.191 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 15:17:02.199 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 15:17:02.635 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:17:02.637 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:18:08.646 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:18:08.674 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:19:12.685 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:19:12.692 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:20:02.134 MainServer::ANN Monitor
2010-06-29 15:20:02.144 adding: Media-Server as a client (events: 0)
2010-06-29 15:20:16.701 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:20:16.707 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:21:16.716 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:21:16.725 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:22:22.734 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:22:22.747 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:23:29.757 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:23:29.765 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:24:34.774 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:24:34.784 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:25:41.793 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:25:41.801 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:26:43.811 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:26:43.818 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:26:57.444 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 15:27:49.827 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:27:49.840 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:28:56.850 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:28:56.858 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:30:01.681 MainServer::ANN Monitor
2010-06-29 15:30:01.694 adding: Media-Server as a client (events: 0)
2010-06-29 15:30:01.867 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:30:01.877 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:31:03.886 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:31:03.894 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:32:09.903 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:32:09.916 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:33:16.925 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:33:16.934 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:34:17.943 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:34:17.955 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:35:22.964 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:35:22.974 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:36:24.983 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:36:24.991 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:37:30.000 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:37:30.010 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:38:33.019 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:38:33.030 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:39:39.039 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:39:39.052 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:40:02.251 MainServer::ANN Monitor
2010-06-29 15:40:02.265 adding: Media-Server as a client (events: 0)
2010-06-29 15:40:45.061 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:40:45.075 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:41:49.084 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:41:49.109 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:41:57.499 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 15:42:53.116 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:42:53.122 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:43:56.131 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:43:56.142 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:45:02.151 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:45:02.165 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:46:04.174 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:46:04.181 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:47:11.191 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:47:11.199 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:48:12.208 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:48:12.220 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:49:15.230 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:49:15.241 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:50:01.812 MainServer::ANN Monitor
2010-06-29 15:50:01.823 adding: Media-Server as a client (events: 0)
2010-06-29 15:50:21.250 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:50:21.263 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:51:21.272 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:51:21.281 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:52:24.290 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:52:24.301 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:53:28.310 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:53:28.317 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:54:30.326 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:54:30.333 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:55:33.342 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:55:33.353 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:56:37.363 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:56:37.369 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:56:57.553 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 15:57:43.378 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:57:43.391 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:58:48.400 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:58:48.410 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 15:59:50.419 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 15:59:50.427 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:00:02.371 MainServer::ANN Monitor
2010-06-29 16:00:02.377 adding: Media-Server as a client (events: 0)
2010-06-29 16:00:54.436 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:00:54.442 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:01:55.451 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:01:55.464 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:02:59.473 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:02:59.479 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:03:59.488 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:03:59.497 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:05:06.506 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:05:06.531 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:06:08.541 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:06:08.548 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:07:08.557 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:07:08.566 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:08:08.575 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:08:08.584 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:09:13.593 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:09:13.603 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:10:01.926 MainServer::ANN Monitor
2010-06-29 16:10:01.936 adding: Media-Server as a client (events: 0)
2010-06-29 16:10:16.612 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:10:16.623 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:11:20.632 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:11:20.639 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:11:57.613 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 16:12:20.648 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:12:20.657 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:13:26.666 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:13:26.679 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:14:32.688 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:14:32.702 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:15:37.711 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:15:37.720 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:16:39.730 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:16:39.737 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:17:01.247 MainServer::ANN Monitor
2010-06-29 16:17:01.258 adding: Media-Server as a client (events: 0)
2010-06-29 16:17:01.395 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 16:17:01.400 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 16:17:01.409 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 16:17:42.746 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:17:42.757 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:18:47.767 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:18:47.776 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:19:49.785 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:19:49.793 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:20:02.014 MainServer::ANN Monitor
2010-06-29 16:20:02.042 adding: Media-Server as a client (events: 0)
2010-06-29 16:20:52.802 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:20:52.813 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:21:57.822 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:21:57.832 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:22:59.841 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:22:59.849 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:23:59.858 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:23:59.867 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:24:59.876 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:24:59.898 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:25:59.911 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:25:59.920 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:26:57.663 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 16:27:01.929 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:27:01.937 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:28:04.946 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:28:04.957 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:29:11.966 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:29:11.974 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:30:01.583 MainServer::ANN Monitor
2010-06-29 16:30:01.592 adding: Media-Server as a client (events: 0)
2010-06-29 16:30:14.983 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:30:14.994 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:31:15.004 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:31:15.013 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:32:17.022 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:32:17.045 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:33:23.055 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:33:23.068 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:34:30.077 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:34:30.086 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:35:36.095 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:35:36.108 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:36:42.117 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:36:42.131 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:37:47.140 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:37:47.149 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:38:48.159 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:38:48.171 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:39:48.180 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:39:48.189 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:40:02.158 MainServer::ANN Monitor
2010-06-29 16:40:02.171 adding: Media-Server as a client (events: 0)
2010-06-29 16:40:52.198 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:40:52.205 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:41:54.214 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:41:54.221 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:41:57.720 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 16:42:59.231 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:42:59.240 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:44:03.249 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:44:03.256 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:45:08.265 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:45:08.275 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:46:10.284 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:46:10.291 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:47:12.300 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:47:12.308 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:48:16.335 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:48:16.348 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:49:17.358 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:49:17.370 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:50:01.706 MainServer::ANN Monitor
2010-06-29 16:50:01.714 adding: Media-Server as a client (events: 0)
2010-06-29 16:50:23.379 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:50:23.392 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:51:26.401 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:51:26.413 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:52:32.422 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:52:32.435 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:53:36.444 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:53:36.450 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:54:40.459 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:54:40.466 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:55:43.475 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:55:43.486 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:56:50.495 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:56:50.503 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:56:57.776 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 16:57:54.513 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:57:54.519 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 16:58:55.528 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 16:58:55.541 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:00:00.550 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:00:00.559 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:00:02.264 MainServer::ANN Monitor
2010-06-29 17:00:02.276 adding: Media-Server as a client (events: 0)
2010-06-29 17:01:04.569 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:01:04.575 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:02:07.584 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:02:07.595 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:03:07.604 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:03:07.613 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:04:08.622 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:04:08.635 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:05:08.644 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:05:08.653 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:06:11.662 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:06:11.673 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:07:18.682 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:07:18.691 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:08:20.700 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:08:20.707 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:09:24.716 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:09:24.723 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:10:01.833 MainServer::ANN Monitor
2010-06-29 17:10:01.843 adding: Media-Server as a client (events: 0)
2010-06-29 17:10:29.732 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:10:29.742 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:11:33.765 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:11:33.774 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:11:57.834 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 17:12:34.783 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:12:34.795 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:13:35.804 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:13:35.817 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:14:42.826 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:14:42.834 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:15:44.843 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:15:44.851 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:16:49.860 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:16:49.870 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:17:02.126 MainServer::ANN Monitor
2010-06-29 17:17:02.135 adding: Media-Server as a client (events: 0)
2010-06-29 17:17:02.282 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 17:17:02.287 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 17:17:02.295 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 17:17:53.879 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:17:53.885 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:18:58.894 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:18:58.904 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:20:02.219 MainServer::ANN Monitor
2010-06-29 17:20:02.231 adding: Media-Server as a client (events: 0)
2010-06-29 17:20:03.913 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:20:03.923 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:21:04.932 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:21:04.945 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:22:08.954 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:22:08.960 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:23:12.969 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:23:12.975 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:24:17.985 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:24:17.994 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:25:23.003 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:25:23.013 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:26:27.022 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:26:27.037 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:26:57.886 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 17:27:30.046 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:27:30.057 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:28:31.066 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:28:31.079 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:29:38.088 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:29:38.096 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:30:01.755 MainServer::ANN Monitor
2010-06-29 17:30:01.765 adding: Media-Server as a client (events: 0)
2010-06-29 17:30:39.105 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:30:39.129 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:31:44.135 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:31:44.145 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:32:45.154 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:32:45.167 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:33:52.176 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:33:52.184 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:34:56.193 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:34:56.199 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:35:59.208 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:35:59.220 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:36:59.229 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:36:59.238 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:38:03.247 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:38:03.253 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:39:08.262 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:39:08.272 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:40:02.326 MainServer::ANN Monitor
2010-06-29 17:40:02.335 adding: Media-Server as a client (events: 0)
2010-06-29 17:40:14.281 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:40:14.294 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:41:19.304 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:41:19.313 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:41:57.944 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 17:42:23.323 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:42:23.329 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:43:27.338 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:43:27.344 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:44:33.353 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:44:33.367 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:45:37.376 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:45:37.382 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:46:41.391 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:46:41.397 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:47:44.407 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:47:44.418 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:48:49.427 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:48:49.436 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:49:56.446 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:49:56.454 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:50:01.868 MainServer::ANN Monitor
2010-06-29 17:50:01.892 adding: Media-Server as a client (events: 0)
2010-06-29 17:51:02.463 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:51:02.476 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:52:02.486 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:52:02.494 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:53:06.504 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:53:06.510 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:54:11.519 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:54:11.544 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:55:17.555 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:55:17.568 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:56:21.577 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:56:21.583 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:56:57.996 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 17:57:27.592 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:57:27.606 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:58:34.615 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:58:34.623 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 17:59:35.632 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 17:59:35.645 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:00:01.440 MainServer::ANN Monitor
2010-06-29 18:00:01.453 adding: Media-Server as a client (events: 0)
2010-06-29 18:00:42.654 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:00:42.662 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:01:49.671 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:01:49.680 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:02:55.689 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:02:55.702 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:03:55.711 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:03:55.720 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:05:00.729 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:05:00.739 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:06:02.748 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:06:02.756 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:07:02.765 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:07:02.774 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:08:06.783 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:08:06.789 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:09:06.799 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:09:06.827 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:10:02.011 MainServer::ANN Monitor
2010-06-29 18:10:02.043 adding: Media-Server as a client (events: 0)
2010-06-29 18:10:13.842 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:10:13.850 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:11:16.859 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:11:16.870 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:11:58.054 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 18:12:21.879 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:12:21.889 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:13:21.899 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:13:21.907 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:14:21.916 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:14:21.925 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:15:21.934 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:15:21.943 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:16:24.952 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:16:24.964 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:17:01.321 MainServer::ANN Monitor
2010-06-29 18:17:01.367 adding: Media-Server as a client (events: 0)
2010-06-29 18:17:01.513 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 18:17:01.521 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 18:17:01.529 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 18:17:28.973 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:17:28.979 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:18:32.988 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:18:32.994 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:19:36.004 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:19:36.015 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:20:02.108 MainServer::ANN Monitor
2010-06-29 18:20:02.113 adding: Media-Server as a client (events: 0)
2010-06-29 18:20:43.024 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:20:43.032 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:21:45.041 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:21:45.049 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:22:51.058 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:22:51.071 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:23:58.081 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:23:58.089 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:25:03.098 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:25:03.108 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:26:06.117 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:26:06.128 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:26:58.110 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 18:27:07.137 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:27:07.150 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:28:13.159 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:28:13.172 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:29:16.181 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:29:16.192 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:30:01.647 MainServer::ANN Monitor
2010-06-29 18:30:01.656 adding: Media-Server as a client (events: 0)
2010-06-29 18:30:17.202 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:30:17.214 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:31:18.223 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:31:18.236 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:32:18.245 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:32:18.254 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:33:19.263 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:33:19.275 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:34:21.285 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:34:21.292 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:35:21.301 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:35:21.310 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:36:25.319 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:36:25.326 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:37:27.335 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:37:27.360 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:38:31.368 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:38:31.374 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:39:32.384 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:39:32.396 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:40:02.208 MainServer::ANN Monitor
2010-06-29 18:40:02.218 adding: Media-Server as a client (events: 0)
2010-06-29 18:40:33.405 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:40:33.417 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:41:35.427 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:41:35.434 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:41:58.165 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 18:42:39.443 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:42:39.450 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:43:39.459 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:43:39.468 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:44:40.477 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:44:40.489 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:45:46.498 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:45:46.512 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:46:47.521 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:46:47.533 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:47:52.542 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:47:52.552 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:48:59.561 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:48:59.570 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:50:01.771 MainServer::ANN Monitor
2010-06-29 18:50:01.777 adding: Media-Server as a client (events: 0)
2010-06-29 18:50:05.579 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:50:05.592 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:51:08.601 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:51:08.612 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:52:11.621 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:52:11.633 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:53:17.642 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:53:17.655 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:54:23.664 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:54:23.677 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:55:28.686 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:55:28.696 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:56:34.705 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:56:34.719 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:56:58.220 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 18:57:41.728 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:57:41.736 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:58:44.745 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:58:44.756 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 18:59:50.766 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 18:59:50.779 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:00:02.318 MainServer::ANN Monitor
2010-06-29 19:00:02.363 adding: Media-Server as a client (events: 0)
2010-06-29 19:00:55.788 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:00:55.798 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:02:00.807 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:02:00.817 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:03:04.826 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:03:04.832 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:04:09.841 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:04:09.851 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:05:15.860 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:05:15.873 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:06:17.883 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:06:17.890 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:07:23.899 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:07:23.904 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:08:29.913 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:08:29.927 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:09:30.936 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:09:30.948 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:10:01.924 MainServer::ANN Monitor
2010-06-29 19:10:01.931 adding: Media-Server as a client (events: 0)
2010-06-29 19:10:37.957 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:10:37.966 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:11:38.975 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:11:38.987 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:11:58.277 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 19:12:43.996 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:12:44.006 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:13:46.015 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:13:46.023 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:14:47.032 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:14:47.045 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:15:49.054 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:15:49.061 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:16:50.070 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:16:50.083 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:17:01.240 MainServer::ANN Monitor
2010-06-29 19:17:01.245 adding: Media-Server as a client (events: 0)
2010-06-29 19:17:01.400 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 19:17:01.404 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 19:17:01.413 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 19:17:53.092 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:17:53.103 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:18:58.112 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:18:58.122 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:19:58.131 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:19:58.140 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:20:01.804 MainServer::ANN Monitor
2010-06-29 19:20:01.842 adding: Media-Server as a client (events: 0)
2010-06-29 19:21:00.149 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:21:00.157 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:22:06.166 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:22:06.171 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:23:08.180 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:23:08.188 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:24:09.197 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:24:09.209 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:25:14.219 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:25:14.228 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:26:16.237 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:26:16.245 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:26:58.333 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 19:27:21.254 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:27:21.264 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:28:28.273 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:28:28.281 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:29:33.291 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:29:33.300 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:30:02.397 MainServer::ANN Monitor
2010-06-29 19:30:02.409 adding: Media-Server as a client (events: 0)
2010-06-29 19:30:39.309 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:30:39.323 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:31:42.332 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:31:42.343 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:32:46.352 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:32:46.358 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:33:50.368 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:33:50.374 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:34:50.383 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:34:50.392 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:35:56.401 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:35:56.414 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:37:01.423 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:37:01.433 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:38:02.442 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:38:02.455 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:39:04.464 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:39:04.471 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:40:01.966 MainServer::ANN Monitor
2010-06-29 19:40:01.976 adding: Media-Server as a client (events: 0)
2010-06-29 19:40:07.481 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:40:07.492 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:41:10.501 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:41:10.512 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:41:58.388 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 19:42:10.521 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:42:10.530 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:43:14.539 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:43:14.563 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:44:15.571 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:44:15.584 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:45:22.593 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:45:22.601 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:46:25.610 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:46:25.621 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:47:28.631 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:47:28.642 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:48:34.651 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:48:34.664 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:49:39.673 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:49:39.683 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:50:01.510 MainServer::ANN Monitor
2010-06-29 19:50:01.519 adding: Media-Server as a client (events: 0)
2010-06-29 19:50:43.692 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:50:43.698 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:51:47.708 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:51:47.714 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:52:49.723 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:52:49.731 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:53:51.740 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:53:51.747 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:54:52.756 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:54:52.769 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:55:56.778 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:55:56.784 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:56:58.444 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 19:57:03.794 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:57:03.813 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:58:09.828 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:58:09.841 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 19:59:10.850 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 19:59:10.862 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:00:02.061 MainServer::ANN Monitor
2010-06-29 20:00:02.073 adding: Media-Server as a client (events: 0)
2010-06-29 20:00:17.872 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:00:17.880 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:01:20.889 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:01:20.900 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:02:25.909 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:02:25.919 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:03:28.928 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:03:28.939 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:04:35.949 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:04:35.957 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:05:35.966 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:05:35.975 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:06:41.984 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:06:41.997 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:07:44.022 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:07:44.031 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:08:48.040 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:08:48.046 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:09:51.055 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:09:51.066 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:10:01.638 MainServer::ANN Monitor
2010-06-29 20:10:01.648 adding: Media-Server as a client (events: 0)
2010-06-29 20:10:56.076 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:10:56.085 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:11:56.094 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:11:56.103 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:11:58.500 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 20:13:03.113 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:13:03.121 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:14:07.130 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:14:07.136 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:15:14.146 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:15:14.154 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:16:20.163 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:16:20.176 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:17:01.933 MainServer::ANN Monitor
2010-06-29 20:17:01.941 adding: Media-Server as a client (events: 0)
2010-06-29 20:17:02.085 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 20:17:02.092 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 20:17:02.099 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 20:17:22.186 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:17:22.193 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:18:26.202 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:18:26.209 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:19:33.218 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:19:33.226 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:20:01.618 MainServer::ANN Monitor
2010-06-29 20:20:01.630 adding: Media-Server as a client (events: 0)
2010-06-29 20:20:37.235 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:20:37.242 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:21:43.251 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:21:43.264 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:22:48.273 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:22:48.283 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:23:53.292 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:23:53.302 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:24:57.311 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:24:57.317 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:25:58.326 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:25:58.339 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:26:58.554 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 20:27:01.348 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:27:01.372 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:28:02.385 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:28:02.397 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:29:07.406 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:29:07.416 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:30:02.172 MainServer::ANN Monitor
2010-06-29 20:30:02.184 adding: Media-Server as a client (events: 0)
2010-06-29 20:30:12.425 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:30:12.435 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:31:19.444 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:31:19.453 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:32:22.462 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:32:22.473 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:33:27.482 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:33:27.492 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:34:27.501 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:34:27.510 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:35:33.519 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:35:33.532 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:36:37.541 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:36:37.547 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:37:39.557 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:37:39.564 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:38:46.574 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:38:46.582 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:39:49.591 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:39:49.602 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:40:01.738 MainServer::ANN Monitor
2010-06-29 20:40:01.751 adding: Media-Server as a client (events: 0)
2010-06-29 20:40:53.611 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:40:53.617 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:41:58.609 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 20:41:58.626 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:41:58.636 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:43:00.645 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:43:00.653 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:44:02.662 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:44:02.670 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:45:04.679 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:45:04.687 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:46:07.696 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:46:07.707 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:47:13.716 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:47:13.729 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:48:19.738 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:48:19.752 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:49:19.761 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:49:19.770 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:50:02.286 MainServer::ANN Monitor
2010-06-29 20:50:02.297 adding: Media-Server as a client (events: 0)
2010-06-29 20:50:19.779 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:50:19.788 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:51:20.797 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:51:20.809 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:52:23.818 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:52:23.829 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:53:26.839 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:53:26.850 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:54:31.859 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:54:31.869 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:55:38.878 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:55:38.886 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:56:45.895 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:56:45.904 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:56:58.665 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 20:57:48.913 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:57:48.924 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:58:51.933 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:58:51.944 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 20:59:55.953 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 20:59:55.960 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:00:01.877 MainServer::ANN Monitor
2010-06-29 21:00:01.889 adding: Media-Server as a client (events: 0)
2010-06-29 21:01:00.969 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:01:00.979 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:02:05.988 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:02:05.997 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:03:13.007 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:03:13.015 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:04:17.024 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:04:17.039 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:05:20.048 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:05:20.059 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:06:22.068 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:06:22.076 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:07:25.085 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:07:25.096 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:08:26.105 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:08:26.117 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:09:30.127 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:09:30.133 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:10:01.449 MainServer::ANN Monitor
2010-06-29 21:10:01.456 adding: Media-Server as a client (events: 0)
2010-06-29 21:10:37.142 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:10:37.150 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:11:38.160 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:11:38.172 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:11:58.717 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 21:12:41.181 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:12:41.211 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:13:42.218 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:13:42.230 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:14:48.239 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:14:48.252 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:15:52.262 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:15:52.268 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:16:56.277 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:16:56.283 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:17:01.765 MainServer::ANN Monitor
2010-06-29 21:17:01.773 adding: Media-Server as a client (events: 0)
2010-06-29 21:17:01.920 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 21:17:01.924 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 21:17:01.933 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 21:17:56.293 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:17:56.301 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:19:00.311 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:19:00.317 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:20:02.948 MainServer::ANN Monitor
2010-06-29 21:20:02.955 adding: Media-Server as a client (events: 0)
2010-06-29 21:20:07.326 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:20:07.334 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:21:12.343 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:21:12.353 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:22:12.362 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:22:12.371 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:23:13.380 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:23:13.393 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:24:14.402 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:24:14.414 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:25:19.423 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:25:19.433 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:26:25.442 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:26:25.456 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:26:58.775 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 21:27:27.465 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:27:27.472 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:28:31.481 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:28:31.488 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:29:36.497 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:29:36.507 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:30:01.557 MainServer::ANN Monitor
2010-06-29 21:30:01.568 adding: Media-Server as a client (events: 0)
2010-06-29 21:30:37.516 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:30:37.528 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:31:40.537 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:31:40.548 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:32:45.557 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:32:45.584 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:33:46.593 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:33:46.605 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:34:48.615 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:34:48.622 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:35:53.631 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:35:53.641 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:37:00.650 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:37:00.658 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:38:00.668 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:38:00.677 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:39:03.686 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:39:03.697 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:40:02.122 MainServer::ANN Monitor
2010-06-29 21:40:02.131 adding: Media-Server as a client (events: 0)
2010-06-29 21:40:07.706 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:40:07.712 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:41:14.721 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:41:14.730 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:41:58.832 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 21:42:14.739 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:42:14.748 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:43:20.757 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:43:20.770 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:44:26.779 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:44:26.793 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:45:33.802 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:45:33.810 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:46:39.819 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:46:39.832 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:47:39.842 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:47:39.850 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:48:41.860 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:48:41.867 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:49:48.876 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:49:48.885 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:50:01.666 MainServer::ANN Monitor
2010-06-29 21:50:01.673 adding: Media-Server as a client (events: 0)
2010-06-29 21:50:52.894 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:50:52.900 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:51:56.909 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:51:56.916 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:53:00.925 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:53:00.931 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:54:03.940 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:54:03.951 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:55:09.960 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:55:09.974 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:56:09.983 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:56:09.992 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:56:58.887 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 21:57:14.015 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:57:14.023 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:58:20.033 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:58:20.046 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 21:59:25.055 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 21:59:25.065 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:00:02.215 MainServer::ANN Monitor
2010-06-29 22:00:02.226 adding: Media-Server as a client (events: 0)
2010-06-29 22:00:31.074 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:00:31.087 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:01:36.096 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:01:36.105 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:02:42.115 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:02:42.119 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:03:48.129 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:03:48.142 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:04:49.151 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:04:49.155 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:05:51.164 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:05:51.171 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:06:53.181 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:06:53.199 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:07:53.214 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:07:53.223 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:08:54.232 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:08:54.244 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:09:59.253 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:09:59.263 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:10:01.771 MainServer::ANN Monitor
2010-06-29 22:10:01.775 adding: Media-Server as a client (events: 0)
2010-06-29 22:11:03.272 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:11:03.278 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:11:58.941 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 22:12:04.287 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:12:04.308 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:13:05.317 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:13:05.329 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:14:10.338 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:14:10.348 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:15:13.357 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:15:13.359 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:16:17.369 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:16:17.375 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:17:02.063 MainServer::ANN Monitor
2010-06-29 22:17:02.075 adding: Media-Server as a client (events: 0)
2010-06-29 22:17:02.220 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 22:17:02.225 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 22:17:02.234 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.
2010-06-29 22:17:20.384 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:17:20.395 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:18:20.404 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:18:20.413 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:19:22.422 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:19:22.429 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:20:01.993 MainServer::ANN Monitor
2010-06-29 22:20:02.004 adding: Media-Server as a client (events: 0)
2010-06-29 22:20:28.438 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:20:28.451 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:21:30.460 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:21:30.468 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:22:34.477 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:22:34.483 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:23:35.492 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:23:35.504 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:24:37.513 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:24:37.521 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:25:41.530 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:25:41.536 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:26:43.545 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:26:43.552 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:26:58.993 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 22:27:50.562 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:27:50.570 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:28:55.579 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:28:55.588 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:29:58.598 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:29:58.600 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:30:01.530 MainServer::ANN Monitor
2010-06-29 22:30:01.536 adding: Media-Server as a client (events: 0)
2010-06-29 22:30:58.609 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:30:58.618 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:32:01.627 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:32:01.630 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:33:01.639 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:33:01.648 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:34:05.657 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:34:05.664 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:35:10.673 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:35:10.683 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:36:15.692 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:36:15.702 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:37:15.711 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:37:15.720 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:38:19.729 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:38:19.743 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:39:19.753 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:39:19.761 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:40:02.096 MainServer::ANN Monitor
2010-06-29 22:40:02.106 adding: Media-Server as a client (events: 0)
2010-06-29 22:40:19.790 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:40:19.796 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:41:26.805 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:41:26.814 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:41:59.046 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 22:42:27.823 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:42:27.835 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:43:31.844 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:43:31.851 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:44:33.860 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:44:33.867 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:45:34.877 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:45:34.889 UPnpMedia: BuildMediaMap Done. Found 0 objects
2010-06-29 22:49:01.941 mythbackend version: branches/release-0-23-fixes [25154] www.mythtv.org
2010-06-29 22:49:01.942 Using runtime prefix = /usr
2010-06-29 22:49:01.954 Using configuration directory = /home/mythtv/.mythtv
2010-06-29 22:49:01.963 Empty LocalHostName.
2010-06-29 22:49:01.970 Using localhost value of Media-Server
2010-06-29 22:49:01.989 New DB connection, total: 1
2010-06-29 22:49:02.000 Connected to database 'mythconverg' at host: localhost
2010-06-29 22:49:02.004 Closing DB connection named 'DBManager0'
2010-06-29 22:49:02.013 Connected to database 'mythconverg' at host: localhost
2010-06-29 22:49:02.025 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-29 22:49:02.030 MythBackend: Starting up as the master server.
2010-06-29 22:49:02.041 mythbackend: MythBackend started as master server
2010-06-29 22:49:02.050 New DB connection, total: 2
2010-06-29 22:49:02.054 Connected to database 'mythconverg' at host: localhost
2010-06-29 22:49:02.356 New DB connection, total: 3
2010-06-29 22:49:02.369 Connected to database 'mythconverg' at host: localhost
2010-06-29 22:49:03.653 FireDev(001CEA1B2AB40000): The Scientific Atlanta 4250 HDC is not supported 
			by any MythTV Firewire channel changer.At the moment you must use an IR blaster.
2010-06-29 22:49:03.675 SetLastChannel(2): cleared: no
2010-06-29 22:49:03.680 New DB scheduler connection
2010-06-29 22:49:03.688 Connected to database 'mythconverg' at host: localhost
2010-06-29 22:49:03.732 Enabling Upnpmedia rebuild thread.
2010-06-29 22:49:04.948 Main::Registering HttpStatus Extension
2010-06-29 22:49:04.956 Enabled verbose msgs:  important general
2010-06-29 22:49:04.966 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-29 22:49:06.700 Reschedule requested for id -1.
2010-06-29 22:49:06.900 Scheduled 116 items in 0.2 = 0.04 match + 0.15 place
2010-06-29 22:49:06.907 scheduler: Scheduled items: Scheduled 116 items in 0.2 = 0.04 match + 0.15 place
2010-06-29 22:49:06.916 Seem to be woken up by USER
2010-06-29 22:49:13.700 mythbackend: Running housekeeping thread
2010-06-29 22:49:13.747 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2010-06-29 22:49:13.756 UPnpMedia: BuildMediaMap Done. Found 0 objects
```

---

### Post by Lepy on 2010-06-30
At first I saw many of these references:

```
2010-06-29 11:17:02.173 ProgramInfo(3301_20100627173000.mpg), Error: GetPlaybackURL: '3301_20100627173000.mpg' should be local, but it can not be found.
2010-06-29 11:17:02.181 ProgramInfo(3038_20100628230500.mpg), Error: GetPlaybackURL: '3038_20100628230500.mpg' should be local, but it can not be found.
2010-06-29 11:17:02.239 ProgramInfo(3304_20100629032000.mpg), Error: GetPlaybackURL: '3304_20100629032000.mpg' should be local, but it can not be found.

```

and it made me think there could be some sort of fstab problem.

However, reaching the bottom of the log seems to reveal the true problem:
```

FireDev(001CEA1B2AB40000): The Scientific Atlanta 4250 HDC is not supported by any MythTV Firewire channel changer.At the moment you must use an IR blaster.
```

So, it seems you can record over firewire, just not change the channels, which may explain why the first recording worked. Now, your options seem to be either wait, write some channel changer code for your box, or use an IR blaster, which you would also need if you went the HDPVR route.

---

### Post by LowSky on 2010-07-01
> **Lepy said:**
> 

So, it seems you can record over firewire, just not change the channels, which may explain why the first recording worked. Now, your options seem to be either wait, write some channel changer code for your box, or use an IR blaster, which you would also need if you went the HDPVR route.

No it changes channels just fine, I watched it change the channel 3 times last night with no problem..._ but it will not record anything._

when the first recording I tried worked I recorded something off Comedy central to see if it was possible. The next three attempts were NBC, FOX, and HBO. I expected only HBO to fail but all three did.

---

