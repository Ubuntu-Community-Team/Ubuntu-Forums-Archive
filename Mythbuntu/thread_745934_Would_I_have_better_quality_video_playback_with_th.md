---
title: "Would I have better quality video playback with this solution?"
date: 2008-04-05
forum: Mythbuntu
---

### Post by dafreak on 2008-04-05
Helllo folks,

First I would like to thank the folks that steered me a bit in getting my mythbuntu box working properly. So far I'm pretty happy with it although I'm still working on DVD playback, lots of DVDs won't even play even though I've removed mythdvd and I'm using mythvideo and yes I've loaded libdvdcss. But that's not the main question I have although if you have an answer that'd be great. 

What I'd like to know is if I could improve the quality of my TV playback if I was to use my XBox as a frontend and use the current mythbuntu frontend/backend as a backend only. I'm not sure how well the xbox will do at video processing. Normally I'd just test it out but the Xbox is kindof buried in storage at the moment so if its not worth my while I don't mind avoiding it. I also wouldn't mind advice on how to improve the picture quality (TV wise) on my setup. Rough stats on the two:

PC (current frontend & backend)
P4 1.6 Ghz
768MB RAM
Matrox G450Max with DVI


XBox
Latest version of XBMC
Standard XBox setup (no hardware tinkering)
HD component output box with optical out

---

### Post by tamoneya on 2008-04-05
first of all both of those have plenty of processing to run the video and audio without a problem so i would be most concerned with the connect to the TV.  Since the xbox has a better output i would go with that.

---

### Post by volkswagner on 2008-04-05
I am greedy.  I would use both.  I would try to get better output with the current setup.  I would then dig out the x box for a second fe location.  What tv tuner are you using?  You may be able to tweak your settings.

---

### Post by majoridiot on 2008-04-05
> **dafreak said:**
> Helllo folks,

First I would like to thank the folks that steered me a bit in getting my mythbuntu box working properly. So far I'm pretty happy with it although I'm still working on DVD playback, lots of DVDs won't even play even though I've removed mythdvd and I'm using mythvideo and yes I've loaded libdvdcss. But that's not the main question I have although if you have an answer that'd be great. 

What I'd like to know is if I could improve the quality of my TV playback if I was to use my XBox as a frontend and use the current mythbuntu frontend/backend as a backend only. I'm not sure how well the xbox will do at video processing. Normally I'd just test it out but the Xbox is kindof buried in storage at the moment so if its not worth my while I don't mind avoiding it. I also wouldn't mind advice on how to improve the picture quality (TV wise) on my setup. Rough stats on the two:

PC (current frontend & backend)
P4 1.6 Ghz
768MB RAM
Matrox G450Max with DVI


XBox
Latest version of XBMC
Standard XBox setup (no hardware tinkering)
HD component output box with optical out

you didn't state what tuner/capture device you are using, but i recommend you check the 
recording profiles in frontend setup to see what resolution it is capturing at.

in my case, install defaults to the lowest resolution possible for my pvr-150s.  bumping it up to
720x480 and increasing the bitrate a bit (at the expense of larger filesizes(!)) made all of the
difference in the world for livetv and recording quality.

and although i have no personal experience with it, i've heard excellent things about 
xbox frontends- so i'd sure give the spare a try.

---

### Post by dafreak on 2008-04-05
I'm using a pair of ATi TV Wonder cards. I have thought about getting a pair of digital HDTV cards but I don't think my backend would be up to spec for recording the signal. I'll take a look at the setup for the frontend and see what the capture resolution is set to.

---

