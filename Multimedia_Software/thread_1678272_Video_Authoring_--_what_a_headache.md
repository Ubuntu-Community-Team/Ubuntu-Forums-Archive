---
title: "Video Authoring -- what a headache"
date: 2011-01-30
forum: Multimedia Software
---

### Post by tropdoug on 2011-01-30
I have a serious headache! what is up with the Linux world and multi media? I have been trying for the last six hours to get various video editing programs to work on the clean install of maverick (mind I have not had any success on previous versions either) 

So here is the deal:- I have video downloaded from my camcorder using Kino. That part works. However using Pitivi editor -- crashes out _every_ time I try to open it. So I uninstalled it. Then I installed qdvdauthor - all the net tells me how wonderful it is -- Hmmm I can't get it to load any clips at all, no matter what the file extension - .avi, mpeg, .mov, .dv I can get to a screen that shows me clips but as soon as I ask it to load them -- cabooshka crash out _every_ time, not just occasionally but every single time. So I Uninstalled it. 

I then spent hours trolling the net trying to find a repository that would work to get Cineralla - finally after repeatedly trying various ways to enable the akarid repository and failing I found 

[I][http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu](http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu) maverick main
[http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu](http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu) maverick main source code[/I]

so I duly installed the repositories, reloaded the indexes and found Cineralla in synaptic -- Yahooo! Installed them including the development files and thought "OK here I go"

Started the program from the menu and it opens. Looks lovely -- does nothing! Nada, sits there looking at me like a dumb pig! (sorry to the pigs) Click 'file' nothing happens click 'settings' nothing happens its dead! 

All I want to do is take video I have recorded and author it into a menu dvd with professional transitions, some sub titles where approriate and burn it to a DVD that will play on a PAL system, Is that really too hard? 

Any help Pleeeeeese would be welcomed with open arms -- stop me going nuts, help me!

---

### Post by slooksterpsv on 2011-01-30
A few questions:

1. Have you installed the Ubuntu-restricted-extras for like video codecs and that?

2. Can you play the video and watch it in gnome-mplayer or that?

3. Have you tried anything else like DeVeDe or Bombono? - [https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring)

If you need to edit videos, I strongly recommend Kdenlive - I have too many issues with PiTiVi. I will use, if I need to convert, like Avidemux.

So try those out and let me know if any of those work - btw Bombono, you create your menu.

---

### Post by tropdoug on 2011-01-30
1) - I believe so, I ticked the option to do so and had already set up my internet connection to allow that to happen. Just in case - how do I check?

2) - Yes no problem in playing it in VLC or Movie player etc.

3) - Hadn't heard of Bombono so I will try that. DeVeDe - tried that a year or so ago and did not get a good result but might be worth another try. 

If I use kdenlive - because it's a kde app does that load up the OS with heaps of files I will never have a need or except to run kdenlive? 

I recently tried the 64bit Kubuntu 10.10 but couldn't get to grips with the plasmoids and stuff. I think I have been Gnome spoilt

---

### Post by slooksterpsv on 2011-01-30
> **tropdoug said:**
> 1) - I believe so, I ticked the option to do so and had already set up my internet connection to allow that to happen. Just in case - how do I check?

2) - Yes no problem in playing it in VLC or Movie player etc.

3) - Hadn't heard of Bombono so I will try that. DeVeDe - tried that a year or so ago and did not get a good result but might be worth another try. 

If I use kdenlive - because it's a kde app does that load up the OS with heaps of files I will never have a need or except to run kdenlive? 

I recently tried the 64bit Kubuntu 10.10 but couldn't get to grips with the plasmoids and stuff. I think I have been Gnome spoilt

Yes, but it won't interfere with Gnome or the use of any other Apps, and if you ever want to remove it, you can just do (in terminal): sudo apt-get remove kdenlive && sudo apt-get autoremove 

and that will clear out it's dependencies as well.

---

