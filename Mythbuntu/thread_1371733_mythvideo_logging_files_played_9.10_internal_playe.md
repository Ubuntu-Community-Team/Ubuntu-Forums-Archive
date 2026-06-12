---
title: "mythvideo logging files played 9.10 internal player"
date: 2010-01-03
forum: Mythbuntu
---

### Post by frego on 2010-01-03
Back when I was running previous versions of mythbuntu, I setup mplayer as my default player.  I could ssh into the mythbox and grep for 'Playing' in the mythfrontend.log to find what is being played in mythvideo.  

Now, I am now running Mythbuntu 9.10 from a fresh install using the INTERNAL player for videos.  Now it doesn't log what is being played from mythvideo.  Any way to get that back while still retaining the internal player?  I tried starting the frontend with verbose playback and it still hasn't enabling logging of videos played through mythvideo and the internal player.

---

### Post by frego on 2010-01-05
Found the solution after some trial and error. When starting mythfrontend, give the verbose flag, "file" to log files and then you can grep the log for the string, "RemoteFile" and you will see what files are being played in mythvideo.  You must pass the -l parameter with the log file name or mythfrontend won't log.  I also changed ownership and permissions on the log file.

Start front end with:
```
/usr/bin/mythfrontend -l "/var/log/mythtv/mythfrontend.log" -v "file"
```

then search the log file for RemoteFile"
```
grep RemoteFile /var/log/mythtv/mythfrontend.log
```

---

