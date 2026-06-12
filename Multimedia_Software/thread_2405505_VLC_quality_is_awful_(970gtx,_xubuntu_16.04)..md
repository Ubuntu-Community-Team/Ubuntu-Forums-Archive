---
title: "VLC quality is awful (970gtx, xubuntu 16.04)."
date: 2018-11-06
forum: Multimedia Software
---

### Post by ludwig00 on 2018-11-06
I've used VLC on windows for more than a decade now, never had a single problem with it. On xubuntu though, the quality is awful with my settings. 

I have 4670k processor and a 970gtx, it should be perfectly fine but it isn't. My movies are "blocky" and there are big pixels in the image when the scene is moving, it's really disturbing. 

There are probably a solution since I didn't find any people with the same problems as mine on internet. What setting should I mess with ?

---

### Post by Autodave on 2018-11-07
What, if any, drivers did you install for the graphics card?  If you haven't installed any, go to Settings -> Additional Drivers and install the recommended one.

Also, some info on your machine may help.

---

### Post by ludwig00 on 2018-11-08
The setting doesn't recommand me any drivers. There's just a list of Nvidia drivers (open and proprietary). I have the 394.54 installed. 

Like I said, my machine use a 970gtx GPU, an Intel 4670K with Xubuntu 16.04 installed on it. Should be plenty enough for viewing movies in VLC.

---

### Post by mc4man on 2018-11-08
> **ludwig00 said:**
> The setting doesn't recommand me any drivers. There's just a list of Nvidia drivers (open and proprietary). I have the 394.54 installed. 

Like I said, my machine use a 970gtx GPU, an Intel 4670K with Xubuntu 16.04 installed on it. Should be plenty enough for viewing movies in VLC.

What do you mean by playing movies? If DVD movies then try turning off hardware acceleration in vlc
Tools > Preferences > Input/Codecs > 1st option > Disable > click Save button

---

### Post by ludwig00 on 2018-11-09
Not physical version of movies, digital one, like divx, mp4, H.264 and HEVC.

---

### Post by mc4man on 2018-11-10
Well try disabling hardware acceleration anyway & see if things improve.

---

### Post by ludwig00 on 2018-11-10
I tried, it didn't solve anything unfortunately. What should I try next ?

---

### Post by mc4man on 2018-11-10
> **ludwig00 said:**
> I tried, it didn't solve anything unfortunately. What should I try next ?

Have you tried any other players?

---

### Post by nik.charles on 2018-12-20
VLC was my favourite player on Windows too, but was never happy with video quality on Linux

The large number of settings in VLC Preferences make it very difficult to find the correct combination of options to work well

Suggest you try some alternative players with simpler settings options, might make it easier to work out better settings for VLC
I tried out a few alternatives with intention to return to fix VLC, but I never did

I found SMPlayer worked better
Best feature (for me) of SMPlayer is it can resume video playback from time it was previously closed
VLC claims to be able to do that too but I never worked it out, and online comments are only from people who fail to get it working

---

