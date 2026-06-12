---
title: "Running QjackCtl breaks normal playback."
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by xl_cheese on 2007-11-24
Can someone help?  I can play mp3's and such just fine after a fresh restart of my system.  Once I start Qjackctl to do recording I loose the ability to play mp3's.  

I'm getting the hang of setting up qjackctl to record in Ardour with the mic and Hydrogen drum machine.  That stuff seems to work, but regular music playback quits working.

Thanks.

---

### Post by xl_cheese on 2007-11-24
I've gotten closer to making things work.

To make mp3/wav playback work I have to go to qjackctl settings and change output device from default to hw1,0.

I have to restart jack.  However ardour/hydrogen is then broken.

How can I get all of it to work at the same time?

---

### Post by xl_cheese on 2007-11-25
anyone?

---

