---
title: "Can only play audio from one source at a time"
date: 2008-06-18
forum: Multimedia Software
---

### Post by otheracco on 2008-06-18
and whatever application starts using audio first wins.

Let me elaborate.
I can start Amarok and hit play and hear music, but if I start Firefox and try to listen to anything off of Youtube there is not sound (except, of course, the sound coming for Amarok).

Is anyone else having this problem?

---

### Post by tree6foot6 on 2008-06-18
I am having the same exact problem. I thought I could deal with it but after awhile it is just plain annoying. I have no idea how to go about solving this problem so any help would be great. Thanks

-Andrew-

---

### Post by markbuntu on 2008-06-18
There is about a dozen threads on this problem open already, please try finding one of those.

Opening a zillion threads on the same problem is unhelpful as information becomes too scattered for people to find. Please use the search feature first before opening a new thread.

---

### Post by otheracco on 2008-06-19
> **markbuntu said:**
> There is about a dozen threads on this problem open already, please try finding one of those.

Opening a zillion threads on the same problem is unhelpful as information becomes too scattered for people to find. Please use the search feature first before opening a new thread.

I'm sorry, but I looked first.  Please, links.

---

### Post by markbuntu on 2008-06-19
OK, If this is just a problem with flash it is not fixable with flash9 and is fixed in flash 10b which will be avialable soon. If it is a  more general problem then you can try this:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

or this

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

which may work for you. Please follow the directions exactly as missing even one step can make your sound problems infinitely worse.

One thing you need to play sound in more than one app at a time is:

libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

You can get it with Synaptic, search:

libesd-alsa

If none of this helps. Come back here and we will try to help you figure it out.

---

### Post by db9s on 2008-06-19
> **markbuntu said:**
> 

libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

You can get it with Synaptic, search:

libesd-alsa
.

Already have it libesd-alsa.

Isn't there something that I can kill without restarting the app. The conflict is between Firefox (flash) and Totem/Vlc. i.e. going between YouTube and Songs on totem.

---

### Post by otheracco on 2008-06-20
It is not just a problem with Flash.
The problem is that whatever process uses audio first locks it in such a way that Nothing else can use it, whether it be flash, amarok, totem, etc......

Only after I close the app that hogs the sound can another process use the sound card.

I don't have this problem on this computer when using Knoppix Live CD.

I have the library you mentioned.

---

### Post by tjwallace on 2008-06-27
I have this problem as well. I tried reinstalling the libesd-alsa package but the problem still occurs. I can get Amarok and flash to work at the same time but I had to set Amarok to specifically use alsa.

---

