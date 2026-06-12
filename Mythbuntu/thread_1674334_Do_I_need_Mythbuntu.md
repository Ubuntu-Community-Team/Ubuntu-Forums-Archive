---
title: "Do I need Mythbuntu?"
date: 2011-01-23
forum: Mythbuntu
---

### Post by allbread on 2011-01-23
What benefits does Mythbuntu offer over Ubuntu outside of tv-capture? 

I've just assembled a box that I intend to replace our old XP media center with:

 Tyan Thunder S2915-E 
2 x Opteron 2378 / 32GB DDR667-RE 
EVGA GeForce 275 GTX / Tuniq 1000W PSU
Crucial 256GB M225 SSD (primary boot partition)
ARC-1120 PCI-X / 3 x 2TB Hitachi 7200 RAID5 (data partition - we'll see if I can get it working)

I intend to use do something akin to **[this]("http://www.youtube.com/watch?v=ZuyPJFhVTxQ")** to stream Netflix (basically virtualbox WinXP for Silverlight) - the build above is still way overkill for a media center but since I've  had the majority of the components laying around for the better part of a year this past  week just decided "what the heck" and threw them all together.

The primary focus of this new media center will be streaming content (our LCD's built in tuner is sufficient for broadcast and since we don't have cable I don't see any real need to record) and possibly sharing it with a couple other desktop/laptops around the house... 

Is Mythbuntu "worth it" or should I just go with Ubuntu 10.10? 

I'm currently playing with an install of Mythbuntu and my immediate impressions are; configuring a remote looks interesting but we've already a bluetooth trackpad/keyboard that's been serving us well until now, secondly, I miss the Ubuntu Software Center (although perhaps there is a way to access this that I haven't yet figured out) and dislike the brevity of the Mythbuntu desktop (although I'm guessing I this is deliberate and an be configured otherwise).

What would I be losing by dumping Mythbuntu and installing Ubuntu 10.10 proper?

---

### Post by nickrout on 2011-01-23
The differences you are seeing is down to the xfce desktop in mythbuntu vs gnome in ubuntu. To save a reinstall you could go:

```
sudo aptitude install ubuntu-desktop
```

OTOH you may like to look at XBMC, mythtv will only get you recording (which you don't want anyway) over XBMC.

---

### Post by allbread on 2011-01-23
> **nickrout said:**
> The differences you are seeing is down to the xfce desktop in mythbuntu vs gnome in ubuntu. To save a reinstall you could go:

```
sudo aptitude install ubuntu-desktop
```OTOH you may like to look at XBMC, mythtv will only get you recording (which you don't want anyway) over XBMC.

Thanks much for the advice.

Will installing ubuntu-desktop give me the equivalent of an Ubuntu 10.10 re-install... in other words, will I get back my Ubuntu Software Center and my Applications/Places/System menus?

What about all of the backend filesharing stuff that Mythbuntu let me install; I intend to use my media center as a central repository for the majority of my music/video files that I share to the other desktops/laptops in my household... will installing ubuntu-desktop over Mythbuntu allow me to retain these configurations (or does it not really matter)?

Are the benefits of XBMC mainly for remote control compatibility - if I end up just sticking with our bluetooth keyboard and filesharing on my HTPC what does XBMC have over plain Ubuntu?

Sorry for the newbie questions...

---

### Post by nickrout on 2011-01-23
> **allbread said:**
> Thanks much for the advice.

Will installing ubuntu-desktop give me the equivalent of an Ubuntu 10.10 re-install... in other words, will I get back my Ubuntu Software Center and my Applications/Places/System menus?I believe so. software-center is in the list of apps to be installed (as you could see if you typed in what i suggested, it gives you a chance to back out)> 

What about all of the backend filesharing stuff that Mythbuntu let me install; I intend to use my media center as a central repository for the majority of my music/video files that I share to the other desktops/laptops in my household... will installing ubuntu-desktop over Mythbuntu allow me to retain these configurations (or does it not really matter)?It's all linux, you don't need mythbuntu to share files

> Are the benefits of XBMC mainly for remote control compatibility - if I end up just sticking with our bluetooth keyboard and filesharing on my HTPC what does XBMC have over plain Ubuntu?

Sorry for the newbie questions...

XBMC is a media viewing program, in the same way that mythfrontend is. It's a nice one, lets you download metadata etc. xbmc.org is the website.

---

### Post by chipppy on 2011-01-24
Good morning

Mythtv is a one stop shop with all the bells and whistles.  If all you want to do is stream videos aroudn your network then go one of the simpler programs (XMBC is good out of interest)
If you want more, videos, tv, record, encode, iptv, web, voip phone etc then mythtv is the place to be.  
I use a lot of the features and it is great, after a huge amount of work setting it up. 
horses for course type thing.
Install the gnome desktop and see what you think as all the sharing of videos (files0 is already there.  If no your cup of tea try something else, if not that then try another.  that is what is so great about linux.

Please also share your ecperience for othjer to read when pondering the same questions

Cheers
Chipppy

---

