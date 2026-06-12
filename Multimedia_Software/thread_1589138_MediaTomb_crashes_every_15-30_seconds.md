---
title: "MediaTomb crashes every 15-30 seconds"
date: 2010-10-06
forum: Multimedia Software
---

### Post by diablo_man5666 on 2010-10-06
I installed from MediaTomb from the universe repo. Using default settings, I accessed the web interface, added the directories I wanted to share through UPnP, and MediaTomb started indexing them. About 90% of the way through, it crashed. I checked the log at /var/log/mediatomb.log, and there was no report of an error or anything like that. I restarted MediaTomb with
```
sudo /etc/init.d/mediatomb restart
```
After that first daemon restart, MediaTomb has crashed within 30 seconds of me restarting the daemon.

I'm running this on an Ubuntu 10.04 64bit machine, 4GB of RAM.

Any thoughts?

EDIT: Turns out MediaTomb crashes when ffmpeg fouls up....removed the video file ffmpeg was having trouble with, and MediaTomb is fine.

---

