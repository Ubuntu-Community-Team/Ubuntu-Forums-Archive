---
title: "unknown load in intervals"
date: 2008-07-15
forum: Multimedia Software
---

### Post by ikarusX3 on 2008-07-15
Hi,

just about to complete configuration of my ubuntu system. last thing was getting x264 media playback working. under windows with coreAVC i could play 720p movies really smooth so i tried different players and ended up with mplayer. i am happy with that, as it plays just fine and without dropped frames or delays. 

but one big problem i am noticing is really low performance in regular intervals. when watching a movie, from time to time, about every 5 minutes the movie kinda stops like when some other application is drawing alot of performance for itself. this is just one moment but really annoying since its highly noticeable. unfortunately i wasnt able to detect which program could cause such problems and tried stopping everything thats unneeded. (background programs like IM, mail, connection daemons like bluetooth and network manager). that didnt solve the problem. 

is there any possibility to get like a cpu usage history per process? under windows, there was a tool named process explorer which offered exactly that, making it easy to identify disturbing processes. i just know several tools which show the cpu usage per process, but that would need a history so i could let it run while watching.

if any more input is needed, such as process list or logs, let me know.

appreciate your help!

---

### Post by Jean__ on 2008-07-15
I always type 'top' into a terminal.
If you fancy a gui, try control-escape which brings up the ProcessTable from Ksysguard, it's also in the K-menu.

---

### Post by ikarusX3 on 2008-07-15
> **Jean__ said:**
> I always type 'top' into a terminal.
If you fancy a gui, try control-escape which brings up the ProcessTable from Ksysguard, it's also in the K-menu.

top just gives the current cpu usage, but since the load just lasts about a half second its nearly impossible (i tried!) to find this one process.

i would need sth that gives me a history per process, like that:
[IMG]http://i.technet.microsoft.com/bb896653.ProcessExplorer(en-us,MSDN.10).jpg[/IMG]

---

