---
title: "Kdenlive being jumpy and slow"
date: 2010-08-23
forum: Multimedia Software
---

### Post by draxot on 2010-08-23
Hey there, i have a query about Kdenlive, 
when putting avi. files with audio files like wma. it chugs hard and doesnt play out a smooth rendition of the two.

I only went to Ubuntu because i thought windows movie maker was a joke in regards to its freezes..

I have tryed a few other video editting apps but as far as i can see Kdenlive has all the basics i need except the smooth file use..  


Questions i suppose would be: does my 2gb RAM and 64 AMD 4000+ fit a video editting standard?

What is the best video editting software out there on ubuntu?

Hopefully these questions help someone else, as i couldnt immediately find threads of similar regards.

---

### Post by sicboy on 2010-09-06
Hi, I have the same issue (running AMD 5200 dual core, 4Gb RAM) and using the renice command helps a bit.  I used "ps -e" to find the process ID of kdenlive, then "sudo renice -20 (process ID)".  Renice works on running processes.  You can start a program with the nice command, if you prefer.  FYI, "nice" comes from how nice you're going to be with other users of the machine (as in a server), from-20 to 19, with 19 being really nice and -20 being...not very nice.  As the only user of this box, "nice" isn't really an issue.  Still choppy on quick cuts with effects, but at least I can get the timing right without rendering it over and over to see what it looks like at proper speed.  Anyway, hope that helps.

---

