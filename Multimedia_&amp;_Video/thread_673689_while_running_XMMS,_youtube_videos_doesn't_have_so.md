---
title: "while running XMMS, youtube videos doesn't have sound"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by pacsum on 2008-01-20
When I'm watching a video on youtube I can't use XMMS, it says that the sound card is being used or check your sound driver and when I'm using XMMS and I try to view a youtube video, the video doesn't have sound. **What could it be?**

---

### Post by daengbo on 2008-01-20
They are both trying to access the raw sound card at the same time. Make sure the Enlightenment Sound Daemon (ESD) is running (System -> Preferences -> Sound on the second tab. Set XMMS to use ESD in the preferences.

Last time I saw, the Flash plugin checks for these one of two files -- if they exists, Flash will use ESD:
 1. /tmp/.esd/socket
 2. /usr/lib/libesd.so.1

---

### Post by pacsum on 2008-01-21
Ok, I changed the output plugin in XMMS from OSS to ALSA. It works now, thx.

---

