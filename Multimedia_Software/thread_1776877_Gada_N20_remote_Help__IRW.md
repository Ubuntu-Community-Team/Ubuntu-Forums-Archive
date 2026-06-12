---
title: "Gada N20 remote Help  IRW"
date: 2011-06-06
forum: Multimedia Software
---

### Post by nrune on 2011-06-06
I have a Giada slim-N20 that has a microsoft MCE compatable remote.  I have set up the remote vis mythbuntu settings program and it works great in Boxee and XBMC. 

The problem comes in that I want to reconfigure some of the buttons and I open up irw and I can not see any remote presses at all, but it works fine in boxee xbmc, so what is going on here? 

Thanks for looking. 
Mike

---

### Post by nrune on 2011-06-08
So on the giada N20 there must be some hardware settings that are directly connected with the remote that they send.  I uninstalled lirc, purged every config file and guess what, the remote still works.  My assumption is that the configuration is hard wired. 

Now to install a key logger to really see what is going on. I post this in case it is helpful to some one else. 

Mike

---

### Post by nrune on 2011-06-09
Final remapping solution: 

In order to map the rest of the keys of the remote, do the following.
xev 

in a terminal and on the remote press the key and note the key number. 

Then remap using:

> xmodmap -e “keycode xx=less greater”

the xx is the key number in found xev then the name of the key that you want. In my case the back buttion was not working in boxee so…

xmodmap -e “keycode 166=BackSpace”

rest of the buttons are mappable in the same way.

Enjoy Mike

---

