---
title: "Dang this is hard - what I've learned so far"
date: 2008-05-28
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2008-05-28
I have a Mythbuntu 7.10 system that works great.  All tweaked and configured and just humming along.  Wasn't that hard to get going.

I pull the hard drive and put in a bigger one.  Do a fresh install of Mythbuntu 8.04 - and the learning starts.  Here is what I've learned:

1)  I was lucky on the 7.10 install.  I should have been greatful and just left it alone.  Good thing I got it's hard drive.

2)  When you install do not say you have a remote and it's custom. that will crash the mythbuntu install.

3)  The syslog (/var/log/syslog - if I remember right) has lots of good stuff in it when things crash.  Same with logs in /var/log/mythtv/

4)  If you use the Envy script to get your video drivers all shiney-like then you are in for trouble with 8.04.  Summary: follow his directions but do a 

sudo apt-get remove envyng-core 

before you do the 

rm -R /usr/share/envy 

he has you do.  Then just do sudo apt-get install envyng-core and sudo envyng -t to get all that video goodness.

5) It's the details that count: The directory permissions need to be 775, I keep typing 755.  Brain damage.  It's mythtv:mythtv.  You now set the recordings directory by giving editing the "Default" storage location.

6)  XvMC is a pain.  With 7.10/myth 0.20 my hardware shows 20-40% cpu when watching tv.  In 8.04/0.21 with XvMC it's 10-20% but it sometimes goes to 90% and starts stuttering.  CPU++ helped but it still seems unstable.  (hardware runs memtest real solid like and 7.10 is solid as granite 3mo uptime with no trouble).

7)  Something seems disconnected in the audio control.  I can't control the volume in 8.04/0.21.

8)  Mythtv seems to be forgetting my tv channel connections.  It'll work for a day or so and then wham - I go into Watch TV and nothing happens, it just pops back to the main menu with Watch TV highlighted.  Going in to the channel config and re-doing all that stuff will make it work for another day or two.   Nothing in the logs.

9)  It creeps me out that ATSC was removed from the menus in the channel config stuff.  Seems wrong.'

10)  There seems to be a lot of flakey problems in 0.21.  So many I cant keep track or even form a decent bug report.  They are the hard to repro - yet reoccuring kind of bugs.  Memory usage going bonkers, cpu usage bonkers.  Hmmm.

11) I'm throwing in the towel on 0.21.  To many problems.

12)  If it aint broke dont fix it.

---

### Post by KillerKiwi on 2008-05-28
> Mythtv seems to be forgetting my tv channel connections. It'll work for a day or so and then wham - I go into Watch TV and nothing happens, it just pops back to the main menu with Watch TV highlighted. Going in to the channel config and re-doing all that stuff will make it work for another day or two. Nothing in the logs.

If you have more than one video device they may be swapping /dev/video* slots on boot...

> 12) If it aint broke dont fix it. 
So true....

---

### Post by agamotto on 2008-06-03
> **Dewey_Oxberger said:**
> 
1)  I was lucky on the 7.10 install.  I should have been greatful and just left it alone.  Good thing I got it's hard drive.

***Given my own interesting experience with DVD burning and 8.04, you have my sympathies.***


5) It's the details that count: The directory permissions need to be 775, I keep typing 755.  Brain damage.  It's mythtv:mythtv.  You now set the recordings directory by giving editing the "Default" storage location.

[B][I]Ahhh, yes, the joys of frustration dyslexia...
[/I][/B]

7)  Something seems disconnected in the audio control.  I can't control the volume in 8.04/0.21.

***This seems to be fixable by choosing the ALSA mixer as your sound stuff in the Myth Backend Setup under General, if memory serves...***

10)  There seems to be a lot of flakey problems in 0.21.  So many I cant keep track or even form a decent bug report.  They are the hard to repro - yet reoccuring kind of bugs.  Memory usage going bonkers, cpu usage bonkers.  Hmmm.

[B][I]Yep, it only seems to work on systems that were a clean install of 8.04.  My Mum's Mythbox was a clean install, and I didn't have anywhere near the problems that most people who upgraded had.  The Hauppauge 1800 card works well, but I am still trying to find an antenna that works well in our area.  The ones I have tried so far for DTV make everything look like bad DVDs.
[/I][/B]

12)  If it aint broke dont fix it.

Yep, that is what I learned from upgrading my Mythbox.  I went back to 7.10, and everything went back to working.

---

### Post by Caps18 on 2008-06-03
I think this is what a lot of open source projects need to work on.  They shouldn't be cramming in more and more stuff, they need to get what exists to a hospital/military/space/nuclear grade of fail-safe software.  I have done nothing except restart my machine a few times and watched a bunch of TV shows & movies, but it has broken itself.  (resolution changed for some reason and now the backend isn't starting...)

I'm not complaining about Mythbuntu, 98% of the time it is perfect and great, but it is the 2% that keeps me from being able to set it up for my parents or anybody else.

---

### Post by blackoper on 2008-06-03
that's what ssh is for so you can set it up at your parents and then backdoor in to fix things.

---

