---
title: "MythTV problems..."
date: 2009-05-10
forum: Multimedia Software
---

### Post by kdx on 2009-05-10
I've had MythTV working just great for a while, but now I'm having some issues.  This is a bit difficult to describe, so please bear with me...

I have no idea if this first portion is relevant, but it's when all of my problems began.  I decided to upgrade the RAM in my HTPC from 2GB to 4GB.  After getting everything back together again and booting up, everything worked fine except my MythTV.  In the frontend, if I select Live TV, the screen goes to black (like normal, just before the TV comes on) and then just takes me back to the menu.  It usually does this when I need to rescan my channels.  So, I exit the frontend, kill the backend, and run the backend setup to scan for channels again.  Once the scan is complete, I run mythfilldatabase, and wait for it to finish.  When I go to start up mythbackend, it tells me that it can't bind port 6543.  This generally happens when the backend is already running, so I go into the system monitor to see if the backend is running...and it says that it's not.  If I start up the frontend and select Live TV, it should tell me that it can't connect to the backend (because it's not running), but it doesn't.  It just flickers and goes back to the menu.  This suggests that the backend IS running.  If I exit the frontend again and "sudo killall mythbackend" in the terminal, it does not report that no process was killed.  If I immediately "sudo killall mythbackend" again, it tells me that no process was killed.  So mythbackend was running, even though it didn't show up in the system monitor.  If I start up mythbackend once again, it shows up in the system monitor.  When I try to watch Live TV, I actually get TV but the picture is all garbled; which tells me that I need to rescan the channels, and the process starts all over again...

I hope my description of the problem is coherent enough, but I'm not sure if I'll be able to describe all of the symptoms well enough because at this point I'm still not sure what's going wrong.

Could anybody give me some help?

---

### Post by kdx on 2009-05-10
I think I may have fixed it somehow.

Apparently, running mythtv-setup as root fixed my issue...at least for now.

I guess it doesn't have to make sense as long as it works. :lol:

---

### Post by kdx on 2009-05-10
Well, I accidentally bumped the power button on my battery backup and shut down my computer.  Once I got it back up and running again I found the same problem, but it appears that running mythtv-setup as root didn't help.

I'm lost again.

---

### Post by MisanthropicOne on 2009-07-05
I too am having this problem after a less than graceful power down. I'd like to add that it's not showing any of my recordings either, even though they are all still there.

---

