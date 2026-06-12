---
title: "Intermittent Shutdown problem"
date: 2008-08-18
forum: Mythbuntu
---

### Post by elja2 on 2008-08-18
I was wondering if someone could help.

I'm having problems getting mythbuntu to shutdown automatically (i.e. when idle). I have a combined frontend and backend.

Sometimes it will shutdown, sometimes it shutdowns in to some strange state in which the computer still has power, but the display wont show anything. I guess it has tried to hibernate but it wont resume. 

I have tried configuring the backend with the following commands:
/sbin/halt -P 
/sbin/shutdown -p now
/sbin/shutdown -p -h now
/usr/share/mythtv/myth-halt.sh

All of which have been added to suders. Each one has displayed the same behavior: 
- I configure a recording to start in 5mins and last 5mins 
- I watch the backend log and I can see it call the above command 
- Myth shuts down and starts at the appropriate time 
- Then after the recording is finished it is anyones guess as to what will happen, it will always call the shutdown command, but whether this results in a proper shutdown or this weird state is fairly random. 

I am at my wits end because everytime I test it, it seems to work, but then when I leave it, might work or it might not.

---

