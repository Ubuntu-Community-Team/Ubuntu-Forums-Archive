---
title: "Trying to Installed plex media server, and it wont start."
date: 2012-07-17
forum: Multimedia Software
---

### Post by CptanPanic on 2012-07-17
I just installed plex media server via the software center, and when I try to start it I get 

```
initctl: Unknown job: plexmediaserver
```  

How can I debug this issue?

---

### Post by CptanPanic on 2012-07-17
So I did some other stuff, and am wondering if the packages are messed up.   At first I couldn't get upstart to start service and I found that the files /etc/default/plexmediaserver and /etc/init/plexmediaserver.conf were not actually installed. I did see these files in the deb file, so I copied them over manually. I had to change PLEX_MEDIA_SERVER_APPLICAITON_SUPPORT to be /opt/plexmediaserver, but still plex fails to start because it is looking for stuff in /opt/plexmediaserver/Plex Media Server. So is it me, or is the package not working?

Thanks,
CP

---

### Post by Bucky Ball on 2012-07-17
Can't help with your prob, but were you aware of this and will it be an issue for you?

> &#8226; N.B. Flash and Silverlight video playback is not supported on Linux.

From their site. ;)

---

### Post by CptanPanic on 2012-07-17
> **Bucky Ball said:**
> Can't help with your prob, but were you aware of this and will it be an issue for you?



From their site. ;)

Will not be a problem for me as I am using this only for a server to stream to my mobile and appletv.

---

