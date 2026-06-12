---
title: "Play music over network"
date: 2008-12-04
forum: Multimedia Software
---

### Post by ernstblaauw on 2008-12-04
I'm running Ubuntu 8.10 on my laptop. If I'm at home, I play music from my home computer. The home computer is running Windows and shares the music using Samba over the network. On my laptop, I use smbfs to mount the share automatically if it is available.

Now the problem: a lot of players can't get on with this sometimes not availabe music. Rhythmbox always is scanning for a couple of minutes if the state of the share changes. I couldn't get Banshee to use the share, and Amarok also takes a lot of time to update the collection. Songbird isn't even able to play the music without hiccups. 

How should I do this? I like to have a library function, which easily sees if the data is available or not, and according to this state update the library.
Any ideas?

---

### Post by Pete N. on 2008-12-04
If you are only trying to share music within the local network, try Tangerine ([http://snorp.net/tangerine/](http://snorp.net/tangerine/))

---

