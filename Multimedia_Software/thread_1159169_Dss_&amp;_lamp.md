---
title: "Dss &amp; lamp"
date: 2009-05-14
forum: Multimedia Software
---

### Post by tkdiamond08 on 2009-05-14
Hey all, I recently installed LAMP on my server which is currently running Darwin Streaming Server (using port 80), however after I did this no other computer other than itself were able to access it's streams. 

It would just hang at connecting every where else I tried. So I figured this was because apache uses port 80, so I went into all the config files and changed every entry of port 80 to port 1234, and then restarted apache, and that made no difference. 

So I'm not sure what else in LAMP would be causing interference on port 80. Do you guys know, or is there anyway to check if something other than DSS is using port 80?

thanks.

---

