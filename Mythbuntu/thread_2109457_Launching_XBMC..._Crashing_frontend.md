---
title: "Launching XBMC... Crashing frontend?"
date: 2013-01-27
forum: Mythbuntu
---

### Post by aormond on 2013-01-27
First, some background. I'm running .26-fixes with 12.04. I use MythWelcome to shutdown my system when the frontend is not running and the system is idle.

Some time ago, I added a menu item to launch xbmc from within MythFrontend. It's worked well for almost a year.  Starting a couple of weeks ago, a few minutes after XBMC is launched the system will sometimes shut down.

Here's what I think is going on: It appears that MythFrontend is crashing (in the background) when XBMC is launched. At this point MythWelcome takes control and shuts down the system. It's not completely consistent. I don't think the frontend ALWAYS crashes, but it's been happening quite a bit.

Any ideas? In the meantime I've been manually running "mythshutdown --lock" when I want to use XBMC, but my fiancé isn't happy with that solution, obviously. ;)

Thanks!

---

### Post by el_Paraguayo on 2013-01-29
I have a setup where I'm running Mythbuntu 10.10 as a backend with XBMC as a frontend on the same machine.
 
I wrote a script for XBMC which handles the shutdown (setting the wake time) and checks mythshutdown to make sure the back end is idle. See [here]("http://forum.xbmc.org/showthread.php?tid=105941") for more info.
 
An XBMC developer also posted his solution in the thread.
 
May help you. May not.
 
el_P

---

