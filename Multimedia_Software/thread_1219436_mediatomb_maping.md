---
title: "mediatomb maping ??"
date: 2009-07-21
forum: Multimedia Software
---

### Post by buntunoob on 2009-07-21
im not able to play .vob unless i change Mimetype in the mediatomb webpage from video/mp2p to video/mpeg 
i do have 
<map from="vob" to="video/mpeg"/> under mapings 
i tryed <treat mimetype="video/mp2p" as="mpeg"/> maybe insted of mpeg should be vob ?
where do i go from here 
 
 
TY for any help offered

---

### Post by buntunoob on 2009-07-22
Ok, figured it out.. 
%mediatomb -D is your Friend 
For some reason its not picking up my Config.xml file /home/rc/mediatomb/config.xml 
its creating one when I start mediatomb, I am able to edit that file and get everything working.
I wouild like to get it to use the config in the mediatomb folder thou, any ideas on that ?
 
ty for eaven reading this..

---

