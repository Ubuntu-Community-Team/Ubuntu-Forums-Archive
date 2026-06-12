---
title: "Took the Cabel Box out of the Loop and my Channels Changed"
date: 2007-11-28
forum: Mythbuntu
---

### Post by spinlock99 on 2007-11-28
Hi everyone,

Last night I tried to record a program and found out that only Channel 3 would record.  The reason for this was that I was running the TV input through the cable box to MythTV had to be tuned to Channel 3 to get the signal.  

To fix the above problem, I cut the cable box out of the loop and plugged the cable directly from the wall into MythTV.  I rescanned for channels and things are almost working.  The problem is that all of the channels are different now.  For instance, channel 45 used to be Comedy Central but now its the Home Shopping Network.  

Anyone have any ideas on how to fix this?

Thanks,
Andy

---

### Post by superm1 on 2007-11-28
From your other thread, I saw you were using Schedules Direct.  You should be getting the entire channel listing from there.

Be sure that you choose the correct location here:
[http://ubuntuforums.org/attachment.php?attachmentid=51401&d=1196033144](http://ubuntuforums.org/attachment.php?attachmentid=51401&d=1196033144)

And then you should be able to "fetch channel listings"

---

### Post by spinlock99 on 2007-11-28
OK, I don't think I'm explaining the problem very well.  I had been running the cable sygnal through the set top box that Comcast provided and into my MythTV.  For live TV this was fine.  I just had to make sure that MythTV was set to channel 3 and use the set top box to change the channel.

Then, I tried to record a show.  I open up the schedule recordings screen and all of the TV listings are there (pulled from Schedules Direct) and they all match what I see when I press "guide" on the remote to the set top box.  I tried to record channel 45 -- Comedy Central -- but only got static.  I then tried to record channel 3 and that recorded whatever the set top box was set to.

I figured that the problem was MythTV was setting the channel on the tuner card to 45 and picking up static in my first test and that it was setting the channel on the tuner card to 3 and picking up whatever the set top box was feeding it in the second test.  It looked to me like the set top box was the problem so I took it out of the equation.  Now I run the cable right out of the wall into my MythTV.  No set top box at all.

Here's the issue with this setup: the channels are no longer the same.  I still have a complete listing from Schedules Direct that tells me that channel 45 is Comedy Central but, when I turn to channel 45, it's the Home Shopping Network.  What I think I need to do is reconfigure what Schedules Direct is sending me so that it knows I'm not using a set top box.

Hope that clears up the problem.

Thanks,
Andy

---

### Post by newlinux on 2007-11-28
> **spinlock99 said:**
> OK, I don't think I'm explaining the problem very well.  I had been running the cable sygnal through the set top box that Comcast provided and into my MythTV.  For live TV this was fine.  I just had to make sure that MythTV was set to channel 3 and use the set top box to change the channel.

Then, I tried to record a show.  I open up the schedule recordings screen and all of the TV listings are there (pulled from Schedules Direct) and they all match what I see when I press "guide" on the remote to the set top box.  I tried to record channel 45 -- Comedy Central -- but only got static.  I then tried to record channel 3 and that recorded whatever the set top box was set to.

I figured that the problem was MythTV was setting the channel on the tuner card to 45 and picking up static in my first test and that it was setting the channel on the tuner card to 3 and picking up whatever the set top box was feeding it in the second test.  It looked to me like the set top box was the problem so I took it out of the equation.  Now I run the cable right out of the wall into my MythTV.  No set top box at all.
 

Is this a PVR-150 you are using? You can configure myth to keep the tuner at channel 3 and change the channel on the set top box if you like, but you'll need a firewire, serial or IR blaster setup to change the channels on your set top box 

> 
Here's the issue with this setup: the channels are no longer the same.  I still have a complete listing from Schedules Direct that tells me that channel 45 is Comedy Central but, when I turn to channel 45, it's the Home Shopping Network.  What I think I need to do is reconfigure what Schedules Direct is sending me so that it knows I'm not using a set top box.

Hope that clears up the problem.

Thanks,
Andy

Your set top box was probably tuning digital stations and you are now tuning analog stations. These set of stations can differ. You are right. What you need to do is create a different lineup in Schedules direct that corresponds to this analog cable lineup, and associate a video source with this lineup, and then associate the tuner cards input with this video source.

As a side note. I have a PVR-150. I use the coax in to allow it the PVR-150 to tune stations independent of the cable box. I also have the cable box connected via S-video to my PVR-150, so I can record stations only my cable box can get as well (I use firewire to change channels on the cable box). If there are channels on your cable box that you want and can't get via a direct coax connection you might want to consider this setup.

---

### Post by spinlock99 on 2007-11-28
That sounds like exactly what is going on.  Is there anyway to get the digital cabel signal directly into MythTV or will I always need the set top box?  (I have an Hauppague WinTV PCI card right now)  I think the setup I want is to run MythTV on channel 3 and install an IR Blaster to change the station on the set top box.

Thanks for the feedback.

---

### Post by timcredible on 2007-11-28
cable companies put channels wherever they want on the cable, then the cable box re-maps them to the channels you are familiar with.  this is common.  you're going to just have to check the channels and make your own tv guide of what channel is what.

example:  say that cbs is channel 8 when broadcasted over the air, but it's channel 15 when riding on the cable, well, then you're going to have to remember that cbs is channel 15, not 8.

---

### Post by pasta514 on 2007-11-28
> **spinlock99 said:**
> That sounds like exactly what is going on.  Is there anyway to get the digital cabel signal directly into MythTV or will I always need the set top box?  

If your cable provider sends unencrypted QAM you can get a digital receiver card.

A good list can be found here ([http://www.linuxtv.org/wiki/index.php/ATSC_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_Devices)) (paying attention to the entries supporting QAM).

---

### Post by newlinux on 2007-11-28
> **timcredible said:**
> cable companies put channels wherever they want on the cable, then the cable box re-maps them to the channels you are familiar with.  this is common.  you're going to just have to check the channels and make your own tv guide of what channel is what.

example:  say that cbs is channel 8 when broadcasted over the air, but it's channel 15 when riding on the cable, well, then you're going to have to remember that cbs is channel 15, not 8.

Cable companies publish their analog lineup, so hopefully Schedules direct will have an updated guide information for analog cable reception in your area and you won't need to manually assign them.

If you want the digital stations, as mentioned, you'll need a QAM tuner, but you'll only get whatever the cable company sends unencrypted, which is usually your local channels and your local channels in HD, and little else. Or you could try capturing channels from your cable box via firewire. Cable companies have control over what stations have 5c encryption turned on in these channels too, so what is available to you is unknown. Basically without a cable box or cable card, your chances of getting all of your stations digitally are very slim.

---

