---
title: "Cannot play videos after mythtv fixes 23565 upgrade"
date: 2010-02-18
forum: Mythbuntu
---

### Post by williammanda on 2010-02-18
I just updated to the most recent mythtv 22 fixes 23565. I went to watch a video and got kicked back out to the video menu. I'm using storage groups. Not sure what's wrong but here are my front / backend logs:

Frontend log

```
2010-02-18 19:14:25.844 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-02-18 19:14:25.878 Loading menu theme from /usr/share/mythtv/videomenu.xml
2010-02-18 19:14:27.187 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-02-18 19:14:29.342 TV: Attempting to change from None to Watching Video
2010-02-18 19:14:29.624 TV: StartPlayer(0, Watching Video, main) -- begin
2010-02-18 19:14:30.125 AFD Error: Could not find codec parameters. file was "myth://Videos@192.168.1.100:6543/(500) Days of Summer.mkv".
2010-02-18 19:14:30.125 Couldn't open decoder for: myth://Videos@192.168.1.100:6543/(500) Days of Summer.mkv
2010-02-18 19:14:30.125 TV: StartPlayer(0, Watching Video, main) -- end error
2010-02-18 19:14:56.325 AudioPulseUtil: Resume Success
2010-02-18 19:14:56.325 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
```

Backend log

```
2010-02-18 19:14:27.525 MainServer::ANN Playback
2010-02-18 19:14:27.603 adding: C2Q as a client (events: 0)
2010-02-18 19:14:27.653 MainServer::HandleAnnounce FileTransfer
2010-02-18 19:14:27.686 adding: C2Q as a remote file transfer
2010-02-18 19:14:29.342 MainServer::ANN Playback
2010-02-18 19:14:29.378 adding: C2Q as a client (events: 0)
2010-02-18 19:14:29.412 MainServer::HandleAnnounce FileTransfer
2010-02-18 19:14:29.444 adding: C2Q as a remote file transfer
2010-02-18 19:14:29.704 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:14:29.796 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:14:29.888 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:14:30.186 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:14:30.279 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:14:30.371 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:14:30.604 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:14:30.704 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:14:30.796 RingBuf(/var/lib/mythtv/videos//(500) Days of Summer.mkv) Error: File I/O problem in 'safe_read()'
			eno: Input/output error (5)
2010-02-18 19:16:29.552 MainServer::ANN Monitor
2010-02-18 19:16:29.643 adding: PIV3G as a client (events: 0)
2010-02-18 19:17:02.006 MainServer::ANN Monitor
2010-02-18 19:17:02.146 adding: C2D as a client (events: 0)
2010-02-18 19:17:02.214 MainServer::ANN Monitor
2010-02-18 19:17:02.246 adding: C2Q as a client (events: 0)
2010-02-18 19:20:25.563 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
```

I tried several files that I had just recently used but got the same result.

---

### Post by williammanda on 2010-02-18
Well maybe it isn't mythtv. I just tried to play some videos in other media players and they wouldn't play there either. I went to where the files are stored and the some of my directores are missing. The path for the videos is on another drive:

/media/sdb1/var/lib/mythtv/videos

but the only directories that show up are:

/media/sdb1/var

What is also interesting is that storage capacity is still reflecting that the video files are still there. The videos are on a 500 GB drive and I have only 100 GB left and that is what it is saying now with the missing directories.
Another piece on jnfo. I just copied some videos to the above path about 3 hours ago. After setting up the metadata in mythvideo I checked to make sure the videos worked ok and they did. So now 3 hours later the directory path is missing and I can't access the videos. Any ideas?

---

### Post by williammanda on 2010-02-19
Well after much searching I found that I had a partition problem on the drive. I used testdisk to fix the problem.

---

