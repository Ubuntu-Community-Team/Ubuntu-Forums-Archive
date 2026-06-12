---
title: "Netgear Stora NAS help"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by shashi1977 on 2013-05-28
Dear all, I have encountered the following issue. 
I have recently purchased a second hand Netgear Stora NAS drive and unfortunately, Linux support is practically non existent, however having visited a few forum I discovered that I can access the NAS drive using Konqueror and entering in the FTP address to the NAS folders. Et voila, I was able to access and transfer documents as I wanted, however, when I try to play video files from the NAS folder, VLC gives me the following errors.

'Network interaction failed:
Your password was rejected.
Your input can't be opened:
VLC is unable to open the MRL.
'ftp://192.168.x.x/home/user/MyComputer/homefolder/VID.mp4'. Check log for details.

I would appreciate it if anyone could point me in the right direction for video / music playback from the NAS drive. Thanks.

---

### Post by zt14427 on 2013-05-28
Just a shot in the dark... from my past FTP experience, this trick is nice for automation.  Instead of entering in your username and password manually, try putting this into VLC in the format of ```
[COLOR=#000000]ftp://user:password@192.168.x.x/home/user/MyComputer/homefolder/VID.mp4
```
or [/COLOR]```
[COLOR=#000000]ftp://user@192.168.x.x/home/user/MyComputer/homefolder/VID.mp4[/COLOR]
```

---

