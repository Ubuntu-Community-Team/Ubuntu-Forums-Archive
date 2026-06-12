---
title: "mp3's not playing over the network (Edgy)"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by kelbizzle on 2006-11-12
Before upgrading to Edgy from Dapper I was able to browse the network, and listen to music or video without copying it. Now that I have upgraded to Edgy on the Notebook I'm not able to listen through the network anymore. No files play. I have to copy them first. Anyone have any troubleshooting steps? or is it a bug :confused:

*edit*
 I solved this following the directions **[here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")**. 

installed smbfs: 
```
sudo apt-get install smbfs
```

created a directory to mount it too:
```
sudo mkdir /media/mountname
```
then edit /etc/fstab:

```
mount //servername/sharename  /media/mountname  smbfs  username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

```
notice how I have "username-guest, password=" instead of just "guest". I wasn't working until I changed the line.

---

### Post by jeff777 on 2006-11-12
I have the same issue, but unfortunately haven't found a solution yet. See this thread: [http://www.ubuntuforums.org/showthread.php?t=297804](http://www.ubuntuforums.org/showthread.php?t=297804)

---

