---
title: "no sound after running Smplayer"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by danielvasas on 2008-01-19
Hi,

I have this weird problem with Smplayer. Whenever I have Amarok running and I start a movie with SMplayer, Amarok gets muted, which would be all right even convenient, but after I quit Smpleyer Amarok  keeps being mute. I started Rhythmbox too but that gave no sound either. I takes several reinstalls for the sound to come back on. It's pretty annoying so any help would be much appreciated. 

D

---

### Post by jeffus_il on 2008-01-19
Which desktop and sound system/daemon are you using?

---

### Post by danielvasas on 2008-01-19
I use Ubuntu 7.10.

I don't know about the sound system/deamon, I started using Linux a week ago so frankly I don't know the first thing about it.

---

### Post by arkangel on 2008-01-19
you can try  typing in a console :

 > 
% /etc/init.d/alsasound restart 

this will restart  the alsa driver, could have  been blocked and see if U have recovered sound

---

### Post by jeffus_il on 2008-01-19
Find the settings section of the player, look for the sound device and choose esound.

---

### Post by danielvasas on 2008-01-19
> **arkangel said:**
> you can try  typing in a console :

 
this will restart  the alsa driver, could have  been blocked and see if U have recovered sound

Thanks I'll try it next time when it happens.

---

### Post by danielvasas on 2008-01-19
> **jeffus_il said:**
> Find the settings section of the player, look for the sound device and choose esound.

In the configure engine window in the sound system section the drop down menu contains xine Engine only. I'm not sure if this is where esound is supposed to be.

---

### Post by jeffus_il on 2008-01-19
Try get the sound working first with gmplayer (mplayer), player that smplayer is based on. I suggested esound , the sound system that gnome uses because it can deal with more than one sound input at a time. You problem seems to be connected to multiple accesses to a sound device.

Running gmplayer from a terminal, I go into settings (a wrench symbol) and under the audio tab, I have a list of sound drivers to choose from. If esound is not there, try to install it,

---

### Post by danielvasas on 2008-01-19
It works!
Thanks a lot!

---

