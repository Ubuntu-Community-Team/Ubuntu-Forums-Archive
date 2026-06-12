---
title: "Quod Libet / GStreamer Error"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by kadath on 2007-06-21
I've installed the Quod Libet audio player, but when I try to run it, I get the following error:

```
Unable to open files

Quod Libet could not find the 'filesrc' GStreamer element. Check your GStreamer installation.
```

I'm fairly certain I have all the necessary GStreamer packages installed. Has anyone else had this problem?

**EDIT:** Woops, stumbled upon the solution. If anyone else gets this error, install the package "gstreamer0.10-gnomevfs" and it will work.

---

