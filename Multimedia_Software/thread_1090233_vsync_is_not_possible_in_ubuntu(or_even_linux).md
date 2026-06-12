---
title: "vsync is not possible in ubuntu(or even linux)"
date: 2009-03-08
forum: Multimedia Software
---

### Post by Prometheus28 on 2009-03-08
vsync is not possible in ubuntu. 

[http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png](http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png)


To test for yourself:: move a dark window against a light background rapidly, at the same time attempt a screenshot.

Tearing is always occuring even with compiz off, but it is far less obvious. When you turn compiz on any existing tearing gets severly exaggerated. Tearing also occurs with the open source nv drivers. something must be done.

[http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png](http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png)


Freedesktop.org: the people who make xorg-server (which both kde and gnome use) don't even know what vsync is or why anyone wants it.

[http://www.freedesktop.org/wiki/FindPage?action=fullsearch&context=180&value=vsync&fullsearch=Text](http://www.freedesktop.org/wiki/FindPage?action=fullsearch&context=180&value=vsync&fullsearch=Text)
> 
Your search query "vsync" didn't return any results. Please change some terms and refer to HelpOnSearching for more information.

---

### Post by yzsi on 2009-03-22
Video tearing is the only reason i still keep windows on my laptop. When i want to see a movie i have to switch to win. Hate this... 
BTW, I am using Hardy. And i have a X3100 graphic card.

---

### Post by steefjeqv on 2009-03-22
Hi,

The opensource ati driver (as of version 6.9) has an "EXAVsync" option wich will deliver tear free video. 
You still have to disable "composite" (so no desktop effects).

It works perfectly on my HTPC (VDR) using an ATI X550.

Greetings,
Steven

---

### Post by Mister_Joshua on 2009-03-22
> **steefjeqv said:**
> Hi,

The opensource ati driver (as of version 6.9) has an "EXAVsync" option wich will deliver tear free video. 
You still have to disable "composite" (so no desktop effects).

It works perfectly on my HTPC (VDR) using an ATI X550.

Greetings,
Steven

A variant of this solution helped solve the video playback problem I was having!  The variant was that I went and turned off all desktop effects and the problem was solved.

Thank you!

---

### Post by Shadow_Fi on 2010-10-22
> **Prometheus28 said:**
> vsync is not possible in ubuntu. 

[http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png](http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png)


To test for yourself:: move a dark window against a light background rapidly, at the same time attempt a screenshot.

Tearing is always occuring even with compiz off, but it is far less obvious. When you turn compiz on any existing tearing gets severly exaggerated. Tearing also occurs with the open source nv drivers. something must be done.

[http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png](http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png)


Freedesktop.org: the people who make xorg-server (which both kde and gnome use) don't even know what vsync is or why anyone wants it.

[http://www.freedesktop.org/wiki/FindPage?action=fullsearch&context=180&value=vsync&fullsearch=Text](http://www.freedesktop.org/wiki/FindPage?action=fullsearch&context=180&value=vsync&fullsearch=Text)

Lol. Just tested brand new "perfect" super duper linux distro, ubuntu 10.10. I was laughing my a** off, when there was STILL no vsync. Looks like thouse programmers who write gnome, kde, or anything else, use old CRT monitors, and never use graphic interface.

No really guys, whats the matter? Why vsync works everywhere but not in linux. I mean, i tried hackintosh or windows, no problem there. I have linux based mobile phone, android. Looks like everything ok there with vsync. 

BUT it newer works in linux. That is maybe biggest and the last problem why i cant use linux.

---

### Post by swatkins on 2011-02-20
glxgears can do it, even in a window, but SDL_Flip() doesn't seem to (on my Intel graphics netbook).  So I'm going to have a play with SDL+GL for my smooth animation needs.

---

### Post by aeiah on 2011-02-20
nvidia users can set similar things with nvidia-settings (sync to vblank). and ive never had a problem with my netbook and its intel graphics chip.

---

### Post by henslok on 2011-08-14
I have my Ubuntu comp for a while. Recently my mb packed-up due to age :) I decided to upgrade my old 1GHz 2GB Ram 500GB HDD server to 3GHz Quatro with 8GB RAM and 1TB HDD accelerated with nVidia graphic card. I've been working on upgrade in living room and somehow gradually I start using my linux server as a media player as well. Everything works great apart of one pain in back - vsync or tearing. I tried to turn on/off all kind of options and everywhere I play movie (vlc, Moovida, totem etc). I heard the switching compiz off helps but I like all animations on my gdm. Getting really upset now.:cry:

---

