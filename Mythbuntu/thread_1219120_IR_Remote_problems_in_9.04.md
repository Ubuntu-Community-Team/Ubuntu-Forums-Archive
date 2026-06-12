---
title: "IR Remote problems in 9.04"
date: 2009-07-21
forum: Mythbuntu
---

### Post by hoyer801 on 2009-07-21
I'm having two problems with mythbuntu that are driving me (and my family) nuts. 

At random times, the IR remote stops working. It will not accept any signals at all, even though my IR receiver flashes a red light, signaling that it is receiving the signal from the remote. The only way that I have found to fix this is to VNC into the machine (no keyboard or mouse) close the front end, open up mythbuntu-control-centre, remove the remote and transmitter (directv serial port), add them back, and then start the front end back up.

The other problem is that on occasion, when the system turns off the display to save power, the remote will not wake it. I have to vnc into the machine and wake it that way. Usually, the remote works just fine when I do this. 

These problems did not happen under 8.10 and I'm starting to wish I hadn't upgraded. I'm getting tired of my family asking me to come and fix these issues so they can watch tv.

Any suggestions would be most appreciated.

---

### Post by rubrboots on 2009-07-28
I have had a similar problem with the remote freezing, which I fixed by changing the TV Settings -> Playback Settings to SLIM, I think it is set at CPU+ as default. Not sure about the wakeup problem, mine is either on or off. Jaunty, has many issues. I prefer 8.10 or 8.04.1 Good Luck :D

---

