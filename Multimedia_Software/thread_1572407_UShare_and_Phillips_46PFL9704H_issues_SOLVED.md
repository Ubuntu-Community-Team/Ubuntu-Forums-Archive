---
title: "UShare and Phillips 46PFL9704H issues SOLVED"
date: 2010-09-11
forum: Multimedia Software
---

### Post by bbrand on 2010-09-11
I wanted to share my detective work, hopefully this will help someone else.

Just bought a Phillips 46PFL9704H, which has the ability to play media from a media center compatible server (wireless and wired). My main Linux server (10.04) was the "of course" candidate to utilize this cool feature so I set up "ushare" on that system. 

The TV recognized my server (you need to turn the TV off and on to reflect any changes in the network btw). Great streaming but the TV would only play 25 - 35 minutes of any video before the internal web client in the TV closed itself. 

I tracked this connection with WireShark and you could actually see the embedded client telling the network that it had received a "close connection" and as such was going bye-bye. The TV had to recycled before the embedded client was up and running again.

Some thought went into this and I realized the Linux server had an out of the box Apache webserver up and running which was not really doing anything. Was this Apache instance sending out a regular "close connection" signal that the embedded client was interpreting as part of the ushare stream? 

Removed that Apache instance and yup, problem solved. All video streamed perfectly. 

What I have not tested to date:
- Same problem if the Apache instance is running on a different server (ie other IP address?
- Same problem if running virtual machines?
- What to tweak in Apache to prevent this "close connection" signal hitting the network?

One problem left now: TV will not play more than exactly 30 secs of ANY mp3 media file that is streamed. This is going to be a tough one.

Have fun all

---

