---
title: "problem with noatun"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by Starcrunch on 2007-03-27
id downloaded it and installed it but when i click on it it rings a error message saying  
(connecting/starting aRts soundserver failed. Make sure that artsd is configured properly.)

---

### Post by manishsk on 2008-04-04
I am having the same problem. Need Help. :(

---

### Post by xc3RnbFO8P on 2008-04-04
I found this:
```
[08:19] <mmahmood> I'm trying to run Noatun and it's giving error: connecting/starting aRts soundserver failed. make sre that artsd is configured properly
[08:20] <Logikal`> you got cable in australia
[08:20] <Hobbsee> Logikal`: of course
=== _xavier [n=xavier@249.Red-83-35-13.dynamicIP.rima-tde.net]  has joined #kubuntu
[08:21] <aftertaf> you got electricity too ?? ;)
[08:21] <Hobbsee> aftertaf: nah, we got rid of that...
[08:21] <Hobbsee> :P
[08:21] <aftertaf> :)
[08:21] <aftertaf> ok, brb coffee and cigarette time 
[08:25] <Hobbsee> mmahmood: try googling the error message
[08:26] <aftertaf> mmahmood:  try changing the outpug engine too.
[08:26] <aftertaf> output*
[08:26] <Hobbsee> ah, was that what the solution was, i'd forgotten
[08:26] <mmahmood> k thx
```

In gnome you should be able to change it in: "System" > "Preferences" > "Sound"

And here:  > $ gstreamer-properties

If want to try this out (artsdsp noatun):
> 
If you are running a sound server such as eSound (ESD)  (often used with GNOME) or aRts  (often used with KDE) you will have to disable it before using Audacity. For users with OSS builds of audacity and aRts, you can also use the wrapper provided by aRts and run:
 $   artsdsp audacity

---

