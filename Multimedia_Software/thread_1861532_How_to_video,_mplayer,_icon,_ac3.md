---
title: "How to: video, mplayer, icon, ac3"
date: 2011-10-15
forum: Multimedia Software
---

### Post by Claus7 on 2011-10-15
Hello,

for ubuntu geeks, this might not be something new, yet, while searching the net, I was not able to find the solution to my problems, that's why I'm posting this thread.

What we want to do: we want to play movies with audio and video, and do it easily.

**Problem 1:**
if someone wants to play a movie that needs ac3 (or acc) way of playing things, then the result would be that:
background sound will be working ok,
yet there will be no voice coming from the actors while speaking.

**Solution:**
install mplayer from synaptic

if that is not do the job, then this site 
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)
will solve the problems

I did not check mplayer from synaptic to see if it solves alone the problem, as I upgraded to the launchpad's version, installing some libraries that it proposed, and then downgraded back again to the version proposed by ubuntu without removing the additional libraries.

**Problem2:** 
Right clicking a movie so as to be able to play it with mplayer without using the terminal. 
There is no icon available for mplayer, so terminal is the only way:
mplayer name_of_movie.avi

**Solution:**
Install gnome-mplayer from synaptic
that way any movie will open like a charm.

smplayer on the other hand, refused to play with compiz enabled, as a result gnome-mplayer was a nice alternative.
Just to mention that vlc was not doing the job (about ac3).
All the other files was handled ok by all the programs mentioned here.

All these things took place in ubuntu maverick 10.10!

Regards!

---

### Post by Claus7 on 2011-10-15
Hello,

**Probem 1:**
get rid of the vdpau message

**Solution:**
put vo=xv into your ~/.mplayer/config

**Problem 2:**
how to have the right configuration for sound

**Solution:**
i)  the sound option should be to stereo, not to surround
ii) no passing to s/pdif option ticked

Regards!

---

