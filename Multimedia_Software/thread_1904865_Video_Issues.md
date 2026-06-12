---
title: "Video Issues"
date: 2012-01-05
forum: Multimedia Software
---

### Post by Ampi on 2012-01-05
Recently I bought a video camera and now I want to do some video editing. 

1. After checking I-don't-even-remember-how-many linux video editing programs, I'm quite happy with OpenShot. 
The one thing I don't like is the slowness of it and how it slows down the rest of the computer. I have to wait sometimes up to a minute before my mouse click is carried out! Quite annoying!
2. I also seem to have issues with my apparently not installed MLT. Which I don't really know what that is and I don't seem to be able to install.
3. I also understood that with my built-in video card (see my PC signature) there is a problem with 3D/2D accelerator.  

Because I seem to have several video issues, that I don't understand, I wonder if buying a video card makes any sense? Would that solve ANY of my issues?

---

### Post by inobe on 2012-01-05
i assure you, with an nvidia card, you will have a much better experience.

i have a EVGA gtx 460 SE 2gb card, its an awesome card for video editing, not bad for games too, though i would recommend another card for gaming if you plan on doing crysis or something similar.

not saying to get a gtx 460, just that it has to be nvidia, and you must do research for the model that works for what you do all the time :D

---

### Post by Ampi on 2012-01-06
Okay thanks!

I understand nVidia and Quadro are the best, does it make a difference which one? I mean, can any computer system handle any brand?

If I would get a video card, can I just 'plug' it into my motherboard or do I need to do something in the BIOS or so? Like turning off the onboard video card? 

A new video card should help with the stuttering and stuff while editing, right?

---

### Post by inobe on 2012-01-06
well, i don't want to get into detail, but i'll make it simple....

adobe CSS requires an nvidia GTX470/570+ or a quadro 2000/4000 card, which of course is a lot of cuda cores.

take openshot for an example uses vdpau, it's like purevideo found on windows platform from nvidia.

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)


[http://en.wikipedia.org/wiki/Video_Acceleration_API](http://en.wikipedia.org/wiki/Video_Acceleration_API)

when it comes to certain hardware, most of us may not be able to afford, we can however purchase budget cards and get pretty decent results.

i can't really recommend a specific card, it just depends on what type of video editing you do, if it's clips for home movies, any gtx card would do, if it's 1080p and hours long, you may want to invest in something more powerful.


for the installation of the hardware, you need to go to the pc's manufacturing website to get the system specs, you need at least one pci-e slot, also gtx cards are big and it must fit in your computer case, you must know the dimensions.

---

### Post by Ampi on 2012-01-07
Thanks, very useful reply! 
I'll have a look. Because I build my PC myself the 'box' is a bit smaller than the typical tower, so good point! Completely forgot about the size :).
I had a look and the cards are indeed expensive, luckily I edit at most 30 minutes of film, but mostly it's 5/10 minutes, so I don't per sé need the best of the best.
Thanks again! :)

---

### Post by cotcot on 2012-01-07
You need to make a difference between video editing and video play back. Rendering a video is a matter of CPU , not a matter of video card. The video card only receives a low quality render preview. Play back video is a graphics card issue. Do you have a slow down only during play back ? What does a CPU monitor tells you when you have to wait for the next mouse click ? Is the video you edit HD (.mts or so ?)
Do you have this speed issue with all the editors you tried ?
I edited once (when my ATI radeon PCI broke down) video with an onboard ATI X1250 and had no problems.
Have you installed Kdenlive before ? It is good to uninstall it completely before using Openshot.

---

### Post by Ampi on 2012-01-07
Thanks!

Okay, so my issues with rendering won't be solved with a new video card. 

OpenShot itself is very very very slow and shuts (=crashes?) all the time. While editing it has an extremely slow preview (is this also rendering?) and even after exporting the video, the video (e.g. as *.avi) shows stutter in video and audio. Other avis play just fine. Yes, most videos are HD and MTS (small videos though). I just really like their interface :(.

I have KDenlive still installed. I will give KDenlive another try just even if it is to remember what annoyed me so much about it. And then I'll try OpenShot again with KDenlive completely uninstalled. I'll check other editor again :).

---

### Post by inobe on 2012-01-07
a good graphics card looks to be all you need!

you may want to look at some tutorials on how to configure your system for various libs and such, this are also important.


> Rendering a video is a matter of CPU

:^o

---

### Post by inobe on 2012-01-07
> **cotcot said:**
> Rendering a video is a matter of CPU , not a matter of video card. The video card only receives a low quality render preview.

gpu-accelerated video encoding in your face.

[http://www.youtube.com/watch?v=6rWcvcdy_sk](http://www.youtube.com/watch?v=6rWcvcdy_sk)

either you are using ancient software and hardware, or you've been locked in some cave for the past decade:P

---

### Post by Ampi on 2012-01-10
Hmmm :)

Well, I noticed now that the exported video DOES work perfectly. For the first export I apparently chose the wrong encoding options (there are just too many for a newbie :/) so that is solved.

Still OpenShot is speedwise a real pain in the a**. But this week I'll give KDenLive a try to see if there is any improvement at all. 

I'll also look into the whole libraries stuff. So there will be more coming from me! :)

A graphics card might be a good idea anyway with the whole HD movies and such, but I want to make sure what is going on with what before deciding and buying :).

Thanks anyway for all the input :)

---

### Post by Ampi on 2012-01-11
Okay, after a couple of days of plain misery to try and get KDenLive installed, I finally did it! Hooray to this beautiful simple forum post I found :)
Anyhow, I have way less problems with KDenLive. No stuttering during preview and reacting on mouse click within a normal amount of time. For my n00bie video editing this will do for now.
I will still buy a new video card, I'll just take my time to see what I need and what there is out there.
Thanks again!

---

### Post by inobe on 2012-01-11
yes, my evga gtx 460 se 2gb card is bare bottom, under 300$ it gets the job done, the encoding process is much more faster compared to the old 9800.. i was lucky to get 70fps on 2pass with it, now i get 160+, huge difference.

as for libs, you may want to read some multimedia howto tutorials to get what applies to you, the configuration process can be tricky at first, it really depends on what you need... everyone has different needs, therefor lots of different stuff is out there, so try things keeping track of the changes, this way you won't make the same mistakes twice.

---

