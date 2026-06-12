---
title: "Ardour GTK2 sound static crackle"
date: 2008-10-09
forum: Multimedia Software
---

### Post by efeurich on 2008-10-09
I have recorded some tracks on my Tascam DP-02CF and want to listen to them and maybe already edit them in Ardour :-)
But when I play the tracks in Ardour i hear a noise in the tracks.
A sort of static, crackling noise.
When i play the tracks with an other application like audacious everything sounds fine.

Anyone have an idea on this one and where to start searching?

Thanks in advanced,

EIF

---

### Post by markbuntu on 2008-10-09
Sounds like a sampling rate problem to me. Make sure ardour and jack are set to the same sample rate as the recordings. Audacious and other applications will resample through the sound server but ardour does not like to do that for quality reasons.

---

### Post by efeurich on 2008-10-09
Thanks for the suggestion. But i am recording on a Tascam DP-02CF. This is a home studio recorder and it records on a flash disc. The tracks I record a copy to Ardour via USB interface.
I guess I have to figure out what sample rate the recorder has.

I have also noticed that when i fiddle around with the lattency in Ardour through <jack><lattency> menu. the crackling gets less or more.
Also in the Jack Audio connection Kit setup, there is a parameter called Frames/Period that makes some difference, but doesn't solve the problem.

Can you say anything about those options?

EIF

---

### Post by markbuntu on 2008-10-09
You can start here to learn more about jack:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

---

### Post by efeurich on 2008-10-10
Hi Markbuntu,

Thanks for the websites. I had found them already. 
You get directed to them when you start searching the web.
Seems that these sites are the prominent ones on the web and with the best information.

I will read them through and hopefully learn learn learn.

Ones again thanks,

---

### Post by markbuntu on 2008-10-10
You can also try increasing the Periods/Buffer and/or Frames/Period in the jackcontrol setup. This has helped remove cracking for some people. What you want to do is find the best combination of those that gives you the lowest latency without any problems like crackling, skipping and xruns.

---

