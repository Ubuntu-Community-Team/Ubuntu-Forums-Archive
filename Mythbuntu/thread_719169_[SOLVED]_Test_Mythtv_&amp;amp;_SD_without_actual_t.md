---
title: "[SOLVED] Test Mythtv &amp;amp; SD without actual tuner"
date: 2008-03-08
forum: Mythbuntu
---

### Post by heavners on 2008-03-08
Hi!
I am completely new to everything MythTV - linux, Ubuntu, and my own self-built PVR - so forgive my lack of knowledge.  I have successfully installed MythBuntu on an old laptop, as a trial before I buy hardware to put it on.  (I even managed to get a WiFi card & substandard video to work.)  As it is a laptop, all I have is the Muthbuntu install - no actual video capture or video out devices yet.  The question is, is there anyway to do see how the schedules direct interface works without an interface?  I think I've figured out that the SD has to be assigned to a tuner, and you scan channels from there.  But without a tuner to scan, is there anyway to fake it out and make it think there's a tuner so I can see how the guide & scheduler works?  I'm planning on using this only for OTA broadcasts.

Any thoughts or ideas?  Or am I right that I can't see it without a tuner to scan from...

---

### Post by murchball on 2008-03-10
Rather than trying to fake it out, I think your best bet would be to pick up a tuner and just give it a shot. You can always resell on ebay. The HDHomeRun is network based and would work with your laptop as a backend. SchedulesDirect is currently $20 a year and they offer a 7 day free trial.

Good luck!

---

### Post by volkswagner on 2008-03-10
I dont think you will have much luck.  Even with a tuner installed, myth will return to the main menu after a signal is not found.  I may have some opposition here.  Mythtv's strong point is not a beautiful UI.  It does make up for this in function/customization.
I take back my first comment.  You may try setting up your schedules direct account>create a lineup >lie to myth backend setup(create a tuner such as a firewire cable box)>create video source>create input connection(here is where I am not sure) selecting scan for channels.  I cant remember if you have the choice to grab listings here or in video source.  You want to grab your listings from source.>when setup is complete>exit backend setup>run mythfilldatabase (this will take a while)>open mythfrontend>go into manage recordings>guide
I have no idea if it will work.  You have a better chance this way, rather than via live TV.

---

### Post by majoridiot on 2008-03-10
> **volkswagner said:**
> I dont think you will have much luck.  Even with a tuner installed, myth will return to the main menu after a signal is not found.  I may have some opposition here.  Mythtv's strong point is not a beautiful UI.  It does make up for this in function/customization.
I take back my first comment.  You may try setting up your schedules direct account>create a lineup >lie to myth backend setup(create a tuner such as a firewire cable box)>create video source>create input connection(here is where I am not sure) selecting scan for channels.  I cant remember if you have the choice to grab listings here or in video source.  You want to grab your listings from source.>when setup is complete>exit backend setup>run mythfilldatabase (this will take a while)>open mythfrontend>go into manage recordings>guide
I have no idea if it will work.  You have a better chance this way, rather than via live TV.

setting up a firewire tuner a great option, if all you want to do is test your SD data.

first, make sure you have a line-up already configured @ SD.

next, make sure everything in mythtv setup under "1. General" is accurate.

then, set up the firewire tuner by completing steps 2. 3. and 4 in order.  for the tuner settings in step 2, you can use:

Card Type: Firewire cable box

Model:  anything will do here

you can leave the rest of the settings as they are, since you will not actually be using it.  once that is set up, complete step 3 as
volkswagner suggests, but in step 4. you want to **fetch channels from listings source** not scan for channels.

when you have completed those 3 steps, exit setup and you will be prompted to run mythfilldatabase.  when
that is finished, you should be able to check the program listings in the frontend without actually having a tuner.

once you are satisfied, you can delete the tuner from mythtv-setup under the tuner setting and leave
the config info for SD intact.

---

### Post by heavners on 2008-03-10
That is exactly what I wanted to see I'm able to see the program guide for the channels i had configured at SD - thank you!  Now - to demo to the wife and convince her to spend money on a box to run it all.  Shouldn't be too hard a sell with what we pay for cable.  The plan is to go to ATSC broadcast only...  Thanks - I'm sure I'll be back with more questions once I buy some hardware.

---

