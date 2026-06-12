---
title: "Refresh rate problem - can't get to stay at 50Hz"
date: 2013-06-18
forum: Mythbuntu
---

### Post by Ramrunner on 2013-06-18
I recently ran a heap of updates (about 300 of them) and now I have this problem.

I'm running MythTV. I'm in Australia.

I've found out ages ago I need to set my refresh rate to 50Hz to get judder free video. This is based on the frame rate we use here.

I can go into the display options, set 50Hz, run myhtfrontend and all is well.

The problem is, when I switch off the TV I have attached, then switch it on later (a frequent day to day operation), something in the system must be trying to be helpful now and sets the refresh rate due to what it detects on my TV. It sets it to 60 Hz again. Which means I have to leave mythfrontend, go to display, set 50Hz again, go back to mythfrontend and only then do  get the judder free video. Considering the TV is switched on 3 or 4 times per day, and MythTV is the main use, this is an absolute pain in my backside.

I have in MythTV set it to separate the viewing window from the GUI, and set that to 50Hz. This has always worked, unfortunately now that makes no difference either. It will not switch back to 50Hz automatically.

What is the EASIEST way to get rid of the auto-detection, and simply tell the system to use 50Hz no matter what? I would have thought simply setting 50Hz in the display settings would honour my commands but obviously some piece of code somewhere in my system seems to think it knows best. I don't agree with that, but that's another story.

Best way to do this?

---

### Post by Akriss on 2013-06-29
One of the updates was probably an Nvidia driver update to 304.88.

There are new options for that driver. 

The option that would fix you up is the "UseHotplugEvents" 

Try adding " Option "UseHotplugEvents" "False" " To your xorg.conf, under the "Monitor" section.

Hope it helps

---

### Post by Ramrunner on 2013-11-08
Try adding " Option "UseHotplugEvents" "False" " To your xorg.conf, under the "Monitor" section.

FIRSTLY SORRY FOR THE LATE REPLY. It took me so long and I got so used to getting up, exiting the front end, clicking on 50Hz, starting the front end again I'd given up, until it really bugged me again today and I found this old post with your answer!

You are a clever man!!!

This indeed fixed the problem!

It would be nice if upgrades that make such radical changes DIDN'T just assume I want a new feature switched on by default.

Anyway - this works. Once I've set my TV to 50 HZ, switching on and off the TV makes no difference, the signal stays at 50Hz (YAY!!!).

One more problem I had was now the PC was starting in 60Hz, but adding the 

Option  "TVStandard" "PAL-B"

SEEMS to have fixed that bit.

Thanks for all the help!

---

