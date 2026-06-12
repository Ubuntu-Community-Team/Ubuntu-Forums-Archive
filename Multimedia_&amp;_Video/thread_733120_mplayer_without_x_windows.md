---
title: "mplayer without x windows"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by tonyg_2 on 2008-03-23
Hi guys,

I'm trying to install mplayer on a server system without X.  I've done this in the past with gentoo, so I know that it's possible to remove X dependancy, but I'm not sure if the deb packages allow for it.  I'd rather not compile from scratch, as mplayer is a dependancy nightmare, so I was hoping for some apt-get arguments if some exist.

Has anyone here successfully installed mplayer without any X Window support in ubuntu?  How?

Thanks a bunch
Tony

---

### Post by wolfen69 on 2008-03-23
i don't have an answer about mplayer, but there is cplay  [http://kmandla.wordpress.com/2007/05/01/howto-use-cplay-like-a-pro/](http://kmandla.wordpress.com/2007/05/01/howto-use-cplay-like-a-pro/) 

also, see this: A Day Without X  [http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/](http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/)

---

### Post by tonyg_2 on 2008-03-24
Hi

Thanks for the advice.  Unfortunately cplay doesn't meet my needs.  Very specifically, I'm trying to get the dimensions and length (in time or frames) of a divx movie and save jpg screenshots from it via command line.  My knowledge is limited, but as far as I know, mplayer is the only utility that will do that in linux.  

If you know of something else that will do this, I'm all ears.

Thanks.

PS  A day without X is awesome.  I'm in love with terminal applications.  I often use my computer remotely and remote X, VNC, and NX are often too bandwidth-heavy across the internet.  Also they aren't as state-friendly as screen, so it's hard to queue up tasks and check up on them later.  More software should be built independent of a UI so that UI developers can connect to the functionality, regardless of platform.

---

