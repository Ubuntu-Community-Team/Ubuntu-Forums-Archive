---
title: "Video flickering w/ ATI x1250"
date: 2008-11-26
forum: Multimedia Software
---

### Post by ECas123 on 2008-11-26
I'm running 8.10 and my notebook's got an ATI x1250. When all desktop effects are turned off video plays fine but when it's on I see alot of video flickering. Anyone know how I can fix this issue? I tried downloading the video driver from ATI's site but the flickering is still there.

---

### Post by ECas123 on 2008-11-26
bump plz.

---

### Post by wudsta on 2008-11-26
Hi there,

Just solved this issue myself. You need to change your video player to output via X11.

I did this using by doing the following in VLC.

Settings>Preferences>Video

Select "Output modules" and change to "X11 video output".

I assume this would work for any video player that allows you to change its output.

Hope that helps.

:)

---

### Post by ECas123 on 2008-11-26
> **wudsta said:**
> Hi there,

Just solved this issue myself. You need to change your video player to output via X11.

I did this using by doing the following in VLC.

Settings>Preferences>Video

Select "Output modules" and change to "X11 video output".

I assume this would work for any video player that allows you to change its output.

Hope that helps.

:)

Yay! It works. Thanks a ton dude.

---

### Post by wudsta on 2008-11-26
No probs mate - happy to help. :)

---

### Post by Zaraphrax on 2008-11-26
> **wudsta said:**
> Hi there,

Just solved this issue myself. You need to change your video player to output via X11.

I did this using by doing the following in VLC.

Settings>Preferences>Video

Select "Output modules" and change to "X11 video output".

I assume this would work for any video player that allows you to change its output.

Hope that helps.

:)

Hey mate,

I was having the same trouble on my X1300 Pro, and was just about to post in here and this thread showed up. What a coincidence!

Anyhow, that worked here too. Thanks a bunch!

---

### Post by 5BallJuggler on 2008-11-26
Thanks very much for this, I was using Totem and getting nowhere fast, VLC seems much better and more user friendly

Cheers :)

---

### Post by cnschulz on 2008-12-08
just updating the title to solved so it gets reflected in the search results

thanks for your help!

c.

---

### Post by ramblin' wreck on 2008-12-10
Thanks! I have tried so much (in the interested of furthering my learning) to no avail. 

I appreciate your solution, it works great.

---

### Post by mknarr on 2008-12-11
i just had the same problem Thanks man

i dont no how to offically thx u show it shows up as you were thanked

---

### Post by marsmissionaries on 2008-12-11
Newest ATI driver helps a lot here.

Fullscreen still has SOME issues, but otherwise it's amazing.

Catalyst 8.12 is the version.

---

