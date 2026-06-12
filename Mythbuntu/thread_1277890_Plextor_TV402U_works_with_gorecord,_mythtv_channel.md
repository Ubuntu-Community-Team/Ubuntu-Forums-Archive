---
title: "Plextor TV402U works with gorecord, mythtv channel scan failed to open card"
date: 2009-09-28
forum: Mythbuntu
---

### Post by ronklob on 2009-09-28
Hi all, 

Mythbuntu install (9.04 kernel 2.6.28-11). I used all of the tools (nikosapi, etc) to get the drivers loaded, and everything seems to work fine with gorecord. I can record from the composite and antenna connections. 

When I attempt to scan for channels in MythTV, it gives the 'failed to open card' error. I have not been able to find a fix for this. I have an installed Avermedia card which will perform the channel scan. 

Can anyone help? Still a little green with Linux, so be gentle please.  :) 

TIA

---

### Post by ronklob on 2009-10-01
bump?

---

### Post by trubacca on 2009-10-02
psh, yeah I am in the same boat you are my friend. I just installed the new 9.10 alpha (liking it) and Jelle's 9.8-5 driver update, and I can get recordings with gorecord, but am vainly trying to configure mythtv to record my damn telecourses :-)
I should also point out that I was having this same problem this spring with the same setup you seem to be using now, so while my current setup was easier to get installed (no patches so far) it didn't fix the problem. I am a little green still myself, so it could be incorrect configuration or a missed step in the installation. 
I suppose I could write a script so that gorecord grabs my telecourses at the right time..but I think that is what mythtv is there for, so I am going to continue to try and figure this out. Post here if you figure it out, and I will do in kind.

---

### Post by ronklob on 2009-10-03
Thanks Trubacca, will do.  I just can't believe no one else has had the same problem.  I'm thinking it has to be an easy fix, but I'm just not seeing it.

---

### Post by trubacca on 2009-10-04
OK I have made some progress, but I am not yet where I need to be. We are not using the exact same setup, but it is close, so no promises. if you go to [http://go7007.imploder.org]("http://go7007.imploder.net") you will find that some progress has been made with the newer kernels. I am currently testing on the 9.10 alpha6.. that will soon change to beta and final, but I am trying to get a working setup before I break it again :-)
The new kernels change how the driver works, so much of the information that is available on this hardware is obsolete, and I am trying to figure out exactly what is still required and what were fixes for old kernels.
I have discovered that the plextor tuner cannot actually scan channels, which is why we are having difficulties when we tell it to do so. You will have to go to the channel editor and either manually enter the data for the channels you want, or subscribe to one of the xml feeds that provides channel info. How pricey that is depends on where you are, but I haven't been able to find one for the US that doesn't charge. Since I am only planning on using this to record my college telecourses, I only need one channel. Be sure that you enter the channel frequency when you fill the channel details.
Next, you will need to fill out the details for the recording profile in the front-end. Go to Utilities/Setup->Setup->TV Settings->Recording Profile (or something) and setup a recording profile for the unit. Failure to properly set that up will give you a weird garbled green-screen instead of tasty video when you try to record.
At this point, you SHOULD be able to try and watch live tv. If you have configured your mythtv setup better than me, than you will have live video and sound. Myself? I have not been able to get Mythtv to give me audio with my video. I have tried several configurations, but am still having problems, so let me know how your setup is working, and I will tell you if I have figured out my audio problems yet. Also, I cannot change channels while watching live tv, but that might be a limitation of the tuner, not my config. Regardless, it isn't working now I need it, so I will need to play with it some more. Or stick with gorecord, which seems to work fine.
I hope my progress is helpful for you. Good luck, and let me know how it works.

---

