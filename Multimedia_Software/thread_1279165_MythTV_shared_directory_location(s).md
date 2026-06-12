---
title: "MythTV shared directory location(s)?"
date: 2009-09-30
forum: Multimedia Software
---

### Post by RichJacot on 2009-09-30
Hopefully a quick question, however a not so quick google hasn't helped...

Where is the config file that mythtv uses to tell it where your movies are?

I have no capture card nor will I have one.  I just want to use mythtv for UPnP to my PS3 and I can't find the config file that I can change to point it to my movies directory.

TIA

---

### Post by dphirschler on 2009-10-23
I don't think it's as easy as a config file.  But I think the setting you are looking for is accessible through the MythTV frontend (Utilities/Setup > Setup > Media Settings > Videos Settings > General Settings).  Mine was set as /ver/lib/mythtv/videos.  I wanted it to find my videos directory on my server, so I left that setting alone and make a link like so:

```
ln -s /mnt/server1/videos server
```

Now when I got to videos in MythTV, I see a 'server' directory which is my server.


Darryl

---

