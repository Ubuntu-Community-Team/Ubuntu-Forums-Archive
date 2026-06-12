---
title: "Problem with defining channels"
date: 2009-01-14
forum: Mythbuntu
---

### Post by satellite_72 on 2009-01-14
I just installed Mythbuntu and when i go to run mythtv-setup i get the following error:

2009-01-14 21:25:56.047 New DB connection, total: 1
2009-01-14 21:25:56.100 Connected to database 'mythconverg' at host: localhost
2009-01-14 21:25:56.102 Closing DB connection named 'DBManager0'
2009-01-14 21:25:56.118 Connected to database 'mythconverg' at host: localhost
2009-01-14 21:25:56.123 There are no channel sources defined, did you run the setup program?
2009-01-14 21:25:56.123 DataDirect: Deleting temporary files

So the question is how do I define my initial channels? 

I am new to linux, so go easy on me, thanks.

---

### Post by ian dobson on 2009-01-14
Hi,

Firstly you need to define a video source, then add your tuner card and link it to the video source and if you have a DVB-(cst) card the just to a channel scan. If you have am analog card then you need to manually add the channels/frequencies.

Regards
Ian Dobson

---

### Post by satellite_72 on 2009-01-15
Ok, can I do all of that outside of mythtv-setup? That error keeps me getting to the part of mythtv-setup that configures those things.

---

