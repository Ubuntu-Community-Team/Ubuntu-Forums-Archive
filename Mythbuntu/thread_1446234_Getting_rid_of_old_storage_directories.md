---
title: "Getting rid of old storage directories"
date: 2010-04-03
forum: Mythbuntu
---

### Post by Lepy on 2010-04-03
While troubleshooting some transcoding, I've found that I have some left over storage groups in the databse. When upgrading my master backend a while back, I changed the hostname from xbmc-desktop to just xbmc. 

```
id	groupname	hostname	dirname
1	Default	xbmc-desktop	/var/lib/mythtv/recordings
3	Default	xbmc-desktop	/video/media/
4	Media	xbmc-desktop	/video/media/
13	LiveTV	xbmc-desktop	/video/livetv/
14	LiveTV	xbmc	/video/livetv/
18	LiveTV	xbmc	/var/lib/mythtv/recordings/livetv/
19	Default	xbmc	/var/lib/mythtv/recordings/
17	Default	xbmc	/video/media/

```

I don't think this is causing any problems since the paths are all the same, but for the sake of organization I'd like to fix this. 
I assume it will take some mysql magic since xbmc-desktop is no longer around. 
After googling, I found a script to remove extra hostnames from the mythweb drop-down, which worked very well but have yet to find anything about removing dead storage groups.

Any ideas? Thanks!

---

