---
title: "I desire to learn more, then copy and paste!"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Sean-Michael on 2006-06-08
:KS So, I've found these message boards very helpful,  I currently have XGL, Nvidia driver,  widgets, and all the firefox goodies but I've noticed a few things from my experience of migrating from windows that actually feels like a crutch,  I dont really know what Im doing half the time lol, let me explain...

I notice that the posts and help here is so awesome, but it seems that alot of the time the instructions are mainly copy & paste.

Where are some resources I can goto to learn what Im actually doing, I mean I want to get my machine up to its full potential but half the time I dont know if what I'm doing is actually the best for my hardware!

Small example:
I have a Geforce 6800 gs video card & dual monitors.  I installed the nvidia drivers using the automatrix tool and followed a few post on how to enable the twinview but from system to system, I notice one big differnce,  in windows I have a whole controll panel that allows me to quickly enable or disable deferent features of my card like different desktop images for each monitor,  to either display windows over doth monitors or have then contained to one or the other "browsers" "games" ect,  or to simply use one monitor and even the ability to use window transparency on holding the window...  all I know of in linux/ubuntu is the Xorg.conf file where I can do a few things but I dont know how or what options to use.

Where can I learn how to use my linux system in more detail then copy and paste?  Where can I learn to input actual values for my second monitor, and know what they are?

Also, where can I learn about the other hardware of my computer and ways to configure it...

Aopen mother board,
GeForce 6800 GS AGP card,
2gb ram,
P4 2.66 processor,
onboard audio,

I also was wondering... :-D I use a sherwood stereo reviever for my pc via rca cables, the stereo has 5 speakers and a powered subwoofer...  anything to spruce this up,  It works fine and the audio is great but, just want to get the most out of it!

I appreciate any helpful links and thank you in advance,

---

### Post by nanotube on 2006-06-08
[QUOTE=Sean-Michael]:KS So, I've found these message boards very helpful,  I currently have XGL, Nvidia driver,  widgets, and all the firefox goodies but I've noticed a few things from my experience of migrating from windows that actually feels like a crutch,  I dont really know what Im doing half the time lol, let me explain...

I notice that the posts and help here is so awesome, but it seems that alot of the time the instructions are mainly copy & paste.

Where are some resources I can goto to learn what Im actually doing, I mean I want to get my machine up to its full potential but half the time I dont know if what I'm doing is actually the best for my hardware!

Small example:
I have a Geforce 6800 gs video card & dual monitors.  I installed the nvidia drivers using the automatrix tool and followed a few post on how to enable the twinview but from system to system, I notice one big differnce,  in windows I have a whole controll panel that allows me to quickly enable or disable deferent features of my card like different desktop images for each monitor,  to either display windows over doth monitors or have then contained to one or the other "browsers" "games" ect,  or to simply use one monitor and even the ability to use window transparency on holding the window...  all I know of in linux/ubuntu is the Xorg.conf file where I can do a few things but I dont know how or what options to use.

Where can I learn how to use my linux system in more detail then copy and paste?  Where can I learn to input actual values for my second monitor, and know what they are?

Also, where can I learn about the other hardware of my computer and ways to configure it...

Aopen mother board,
GeForce 6800 GS AGP card,
2gb ram,
P4 2.66 processor,
onboard audio,

I also was wondering... :-D I use a sherwood stereo reviever for my pc via rca cables, the stereo has 5 speakers and a powered subwoofer...  anything to spruce this up,  It works fine and the audio is great but, just want to get the most out of it!

I appreciate any helpful links and thank you in advance,[/QUOTE]
your desire to learn stuff is admirable :) 
the easiest way to learn more detail about something is to use the "man" command from the terminal. for example, "man xorg.conf" will tell you about all the options available for xorg.conf.

to find specific configuration options for your video driver,  just run "man nameofyourvideodriver". for example, my driver is radeon, so i can "man radeon" and it tells all the card-specific config options.

have fun :)

---

