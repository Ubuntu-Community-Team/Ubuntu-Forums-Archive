---
title: "problem playing video"
date: 2012-02-04
forum: Multimedia Software
---

### Post by shortmort37 on 2012-02-04
I recently upgraded to Ocelot (11.10).  It seems to me that video was playing - but somewhere along the way, it's been disabled.  wmv, avi, flv, mpeg - I get audio but no video.  It doesn't matter which app - mplayer, totem, vlc, or any of my video editors.  But, I can play YouTube videos...

How do I start with a diagnosis?

Thanks
Dan

---

### Post by shortmort37 on 2012-02-05
> **shortmort37 said:**
> I recently upgraded to Ocelot (11.10). It seems to me that video was playing - but somewhere along the way, it's been disabled. wmv, avi, flv, mpeg - I get audio but no video. It doesn't matter which app - mplayer, totem, vlc, or any of my video editors. But, I can play YouTube videos...
 
How do I start with a diagnosis?
 
Thanks
Dan
 
*Bump*.  Any ideas on how I start to Dx?

---

### Post by inobe on 2012-02-05
whatever ppa's you've used need to be done over again, they get disabled purposely during full distribution upgrades.

---

### Post by shortmort37 on 2012-02-05
> **inobe said:**
> whatever ppa's you've used need to be done over again, they get disabled purposely during full distribution upgrades.
 
I don't know what a "ppa" is.  Please describe how to do what you suggest...
 
Sorry.  I should have posted this as a "newbie" request.
 
Dan

---

### Post by inobe on 2012-02-05
ppa is a software source you add to sources in your package manager.

maybe in the past to get certain codecs, you needed to add certain sources to your system, if you don't recall doing so, you may want to backtrack on what you've done to get video working, a guide you followed perhaps?

check your package managers sources list to see which is disabled..

google has a lot on it.

[https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ppa+disabled+after+upgrade#sclient=psy-ab&hl=en&source=hp&q=disabled+ppa+after+upgrade&pbx=1&oq=disabled+ppa+after+upgrade&aq=f&aqi=&aql=&gs_sm=e&gs_upl=11525l19520l0l19718l26l25l0l1l1l0l182l2320l15.10l26l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=87ca30d929c15988&biw=1920&bih=963](https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ppa+disabled+after+upgrade#sclient=psy-ab&hl=en&source=hp&q=disabled+ppa+after+upgrade&pbx=1&oq=disabled+ppa+after+upgrade&aq=f&aqi=&aql=&gs_sm=e&gs_upl=11525l19520l0l19718l26l25l0l1l1l0l182l2320l15.10l26l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=87ca30d929c15988&biw=1920&bih=963)

[https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ppa+disabled+after+upgrade#hl=en&sa=X&ei=Di0vT7HeB-Pm0QHa_LHdCg&ved=0CBsQBSgA&q=can't+play+video+after+ubuntu+upgrade&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=87ca30d929c15988&biw=1920&bih=963](https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ppa+disabled+after+upgrade#hl=en&sa=X&ei=Di0vT7HeB-Pm0QHa_LHdCg&ved=0CBsQBSgA&q=can't+play+video+after+ubuntu+upgrade&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=87ca30d929c15988&biw=1920&bih=963)

---

### Post by shortmort37 on 2012-02-06
> **inobe said:**
> ppa is a software source you add to sources in your package manager.

maybe in the past to get certain codecs, you needed to add certain sources to your system, if you don't recall doing so, you may want to backtrack on what you've done to get video working, a guide you followed perhaps?

I can't backtrack, I don't know what I did to *break* the video.  I just upgraded.

> **inobe said:**
> 
check your package managers sources list to see which is disabled..


Which what is disabled?  I don't know what I'm looking for.  
A search of the package manager for ppa indicates pnm3ppa is installed, but I don't see anything related uninstalled.

> **inobe said:**
> 
google has a lot on it.  
[https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ppa+disabled+after+upgrade#sclient=psy-ab&hl=en&source=hp&q=disabled+ppa+after+upgrade&pbx=1&oq=disabled+ppa+after+upgrade&aq=f&aqi=&aql=&gs_sm=e&gs_upl=11525l19520l0l19718l26l25l0l1l1l0l182l2320l15.10l26l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=87ca30d929c15988&biw=1920&bih=963](https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ppa+disabled+after+upgrade#sclient=psy-ab&hl=en&source=hp&q=disabled+ppa+after+upgrade&pbx=1&oq=disabled+ppa+after+upgrade&aq=f&aqi=&aql=&gs_sm=e&gs_upl=11525l19520l0l19718l26l25l0l1l1l0l182l2320l15.10l26l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=87ca30d929c15988&biw=1920&bih=963)

[https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ppa+disabled+after+upgrade#hl=en&sa=X&ei=Di0vT7HeB-Pm0QHa_LHdCg&ved=0CBsQBSgA&q=can't+play+video+after+ubuntu+upgrade&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=87ca30d929c15988&biw=1920&bih=963](https://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ppa+disabled+after+upgrade#hl=en&sa=X&ei=Di0vT7HeB-Pm0QHa_LHdCg&ved=0CBsQBSgA&q=can't+play+video+after+ubuntu+upgrade&spell=1&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=87ca30d929c15988&biw=1920&bih=963)

I tried some of these refs, one was this:
[http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html](http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html)

But many of the packages were obsolete.  I tried deinstalling mplayer, vlc, etc. and reinstalling, but to no avail.

I am really at a loss as to how to proceed.

Dan

---

