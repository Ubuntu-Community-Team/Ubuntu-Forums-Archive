---
title: "my exerpeince with ati catalyst 9.1"
date: 2009-02-06
forum: Multimedia Software
---

### Post by kdreimiller on 2009-02-06
Ok, so I bought a new 22in flat screen to go with my laptop (toshiba satellite l305, 3gigs mem, ati radeon 3100 video).

The screen looks great, but I wanted to hopefully make everything just exactly perfect so I downloaded and installed the new ATI 9.1 driver.

First problem, after uninstalling my old ati prop driver via envy NG my computer shut down and rebooted to the command line prompt.  I freaked (im pretty much a newbie) but remembered the install procedures for the new ati driver.  It worked smoothly.  Yah!

It recognized my two monitors no problem.  And I could save the bigdesktop via system/preferences/screen resolution + click apply.

However, I had some problems getting good video playback.  Totem is a little weird when not in full screen.  The video image overlays the control bar at the bottom of the screen and HD playback on vlc and mplayer was non existent.  Ugh.  

So i tinkered with the xorg.  Big mistake.  Something didnt like that and when i rebooted i got a whole bunch of info that meant nothing to me.  looks like the ati driver didnt like me changing the xorg settings.

i freaked harder!  to restore my system i had to go to grub and go to fix x server.  and then reinstall ati 9.1 all over again.  

however, this time, in this installation, the ati driver pickedup my second monitor and automatically set it for big display right of my laptop monitor.  nice.  

also the catalyst control center is in my apps menu.  i guess somepeople can only bring up its gui using amdccc:le in the terminal?  

however, while i can do any non HD vid on vlc, totem, and mplayer, totem is the only one that i can HD while compiz is running.  with compiz on i can do non hd videos with no flicker (nice!) - but they can be a little jerky a times if im doing anything else, including just surfing the web. 

all in all, i dont know that its a big improvement, but im happy with it.  and in the while of trying to install i got to learn how to tinker with my ubuntu a little more which is mostly what im trying to do.

of note: i dont know how to use xinerama.  it tells me i have only one desktop enabled.  maybe i dont understand the termininolgy, but id assumed that if i have two monitors hooked up that would mean i have to desktops enabled?  im not clear on this.  i can enable it but the road to getting my vid and graphics back to normal has been rocky so i dont feel like rocking the boat at the moment.

anyways, sorry for the rambling, but i thought someone might get something from my experiences installing the new ATI 9.1 driver.

kevin

---

