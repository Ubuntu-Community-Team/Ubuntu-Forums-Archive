---
title: "Cant get grandr(xrandr) to use my 2 dvi monitors"
date: 2008-10-04
forum: Multimedia Software
---

### Post by zer0efx on 2008-10-04
Evening Folks,
 fairly new to Ubuntu, but can handle myself alright.

I have a 9800GX2 vid card that has 2 DVI slots and 1 HDMI slot. I am having a hard time getting both my monitors to work using grandr(xrandr). 

When I ```
sudo grandr
``` the app only shows 1 monitor in it's display. I've also added both monitor resolutions to my xorg.conf file:
```
Display "1440x900" "1440x900"
Virtual 2880 900 
```

But when I used the nvidia-settings I am able to get both monitors to work while using xinerama. But when I do this, I lose my desktop effects.

I've been googling, reading and trying to find a solution, but it seems most of the threads/articles I find are talking about setting up a dual VGA/DVI monitors. Can't seem to find some good info for dual DVI setup while using grandr to extend onto my second monitor, and keep my desktop effects. I found a thread where a guy did 6 monitors, but he doesnt talk about how he got it setup except for mentioning **"xserver-xgl"**

Has anyone had this problem, know of an article, or link where someone has had this similar problem? I searched the forums for 9800 GX2 but didnt find anything. 

Thanks for any insight or help! :D

---

