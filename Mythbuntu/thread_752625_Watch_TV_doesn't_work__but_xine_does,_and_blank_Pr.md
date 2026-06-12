---
title: "Watch TV doesn't work  but xine does, and blank Programme Guide"
date: 2008-04-11
forum: Mythbuntu
---

### Post by jurgenthor on 2008-04-11
Hi, 
I've finally, after much fiddling, got mytbuntu up and running on my new dedicated box. My first real foray into Linux as a desktop since Uni (7 years ago! eep) and it's come a long way. 

But, I'm having a problem: 
I can watch tv fine with my hauppage wintv nova-t-500 on xine, and mplayer (using dvb://<CHANNEL CALLSIGN> but when I use 'Watch Tv' the screen goes black, and then returns immediately, nothing is logged in the mythfrontend log at that time. 
Also, the program guide is empty, but from the recordings menu I can see that things are populated. 
I presume I've missed a step somewhere? I know I had to cp the channels.conf about to get xine workng, do I have to do similar for the mythtv frontend? 
I'm using the xmltv uk rt grabber.
And I've tried turning on EIT for some channels.
Thanks in advance,
L

---

### Post by pseudo-random on 2008-04-11
Best guide I've seen for mythtv is over at parker1.co.uk
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
I gave up on Mythtv eventually since I never record stuff and just made some mplayer dvb:// scripts instead which are quicker and have a much smaller footprint on the system.
Plus if I really need to record something I can always output it to a file > out.mpg

---

### Post by laga on 2008-04-12
> **jurgenthor said:**
> 
I presume I've missed a step somewhere? I


You probably forgot to connect your video source to your TV card in mythtv-setup. Also check the link in my signature to find out how to provide logs.

---

### Post by jurgenthor on 2008-04-14
Seems it was two things - 1 I hadn't set the sources, the other was something to do with a misconfiguration of xmltv. I am just using EIT right now on both tuners, though the info doesn't seem as good, so will look at that later. 
 Now working on getting the remote to work properly, only a few buttons are functioning.

---

