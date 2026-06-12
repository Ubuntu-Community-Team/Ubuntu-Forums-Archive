---
title: "[SOLVED] Mythdora vs Ubuntu - choppy playback"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by jordanius on 2007-09-12
Good people of the Ubuntu forum, howdy.

I'm in desperate need of a suggestion after many hours spent on forums to no avail. 

The problem is this;

With a Celeron 2.8 / 1 gig ddr 400 / Nvidia 6200 128mb AGP / Leadtek 2000h CX88 I can't get decent playback with Mythtv. 

I used a default install from the Ubuntu Fesity CD, the Envy script to automate the nvidia driver install and followed the parker mythtv ubunutu guide to a T. Everything is fine application wise until it comes time for the playback then things chug. I'm talking choppy / stuttery action and a fairly inconsistant framerate. There will be bursts of playback when 3-4 seconds will be ok but it seems whenever the drive is accessed it will pause and lose a frame. SD is sometimes watchable but HD is horrible.. there was a minor improvement when I swapped over to open gl rendering and enabled xvmc in the mythtv options but it's still far from great.

I've confirmed it's running the latest nvidia drivers and open gl is working (glxgears apx 1400fps). Running at 1024x768 x 24 bit I was sure there should be more than enough grunt in my system to render basic SD. 

In a fit of frustration I decided before going back to windows I would give mythdora a crack. Miraculously after a completely painless install I fired up the front end and I have HD playback in a silky 25 FPS without a pause to speak of. !!

I've spent loads of time with ubuntu/debian distros and dont want to throw in the towel for the competition, can any suggest something I can try ?

---

### Post by tgm4883 on 2007-09-12
Yep.

Don't use ENVY, and use this guide [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV).  Enable xvmc.  You should be able to get HD playback.  If your trying to watch live tv and it still isn't playing back smoothly, turn off comm flagging.  If that still doesn't work, then try playing back something in HD when you are not recording.

Also, follow the above linked guide from start to finish (use the cd it suggests) as it will install a lighter desktop env.

---

### Post by jordanius on 2007-09-12
Thanks for the detailed and quick response TGM.

Ok.. so I reinstalled from the command line build following the instructions as per the link below. In comparison I would say there's been an improvement on the SD playback but HD is still pretty poor. it's less stuttery but every time the drive is accessed the action will pause for a few frames. 

The front end seems to be a bit more responsive with the lessened overhead but I can't help but feel like there's lots of room for improvement.. are there any system logs that might be worth reviewing? I'm guessing there's a bottle neck somewhere but don't know where I should be looking..

Cheers

---

### Post by tgm4883 on 2007-09-12
> **jordanius said:**
> Thanks for the detailed and quick response TGM.

Ok.. so I reinstalled from the command line build following the instructions as per the link below. In comparison I would say there's been an improvement on the SD playback but HD is still pretty poor. it's less stuttery but every time the drive is accessed the action will pause for a few frames. 

The front end seems to be a bit more responsive with the lessened overhead but I can't help but feel like there's lots of room for improvement.. are there any system logs that might be worth reviewing? I'm guessing there's a bottle neck somewhere but don't know where I should be looking..

Cheers

Did you install the proprietary video driver (not using envy) and what video card?  Also, did you enable xvmc?

---

### Post by jordanius on 2007-09-12
Bingo! I followed the guide for the nvidia drivers but overlooked updating the line in the XvMC config to refer to nvidia. 

SD is now silky smooth and HD is only very occasionally clips on audio which i'm sure I can nut out. 

Thanks muchos for your help tgm!!

---

### Post by tgm4883 on 2007-09-12
np, can you mark as resolved for anyone else that has the same problem

---

