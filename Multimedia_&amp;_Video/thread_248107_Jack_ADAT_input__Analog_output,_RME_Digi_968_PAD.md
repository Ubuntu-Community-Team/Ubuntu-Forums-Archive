---
title: "Jack ADAT input / Analog output, RME Digi 96/8 PAD"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by second_soul on 2006-08-31
Hey guys - first off, what a great project Ubuntu is, I've been looking for a long time to move over to Linux recording, and this wiki is a great source of info, and has helped me no end to get finally up and running. Thanks! 

So now I got a question... Hopefully an easy one. I have an RME digi 96/8 PAD, plus behringer ada8000 8-channel ADAT preamp. When I start up jack using qjackctl, It won't let me choose a combination of ADAT input, and Analog output - I have to choose ADAT output aswell as ADAT input. This causes no problems until I start to add tracks in Ardour: then Jack starts mapping all combinations of 8 inputs to 8 outputs, I get a big mesh of connections, and the CPU% goes way up before doing any recording, plus a bunch of "delay" messages and the odd XRUN. 

When I remove the tracks, it quietens down again as the connections are closed. Maybe I missed something obvious, but how can I start up jack specifying ADAT in, Analog out, without it complaining?

Btw, I've been using Analog in/out with no problems, PC can do 32 tracks of audio plus various plugins, at around 45% CPU... better than my imac+logic! So I'm sure its a config issue somewhere, maybe some alsa mixer settings or something...? 

Thanks!
_________________
AMD Sempron 2800+
1GB RAM
120GB Seagate SATA HD
RME DIGI 96/8 PAD
Ubuntu/Ardour

*"Open Source Opens Doors"*

---

