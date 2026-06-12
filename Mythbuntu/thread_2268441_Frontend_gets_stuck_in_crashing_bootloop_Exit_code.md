---
title: "Frontend gets stuck in crashing bootloop Exit code 130"
date: 2015-03-08
forum: Mythbuntu
---

### Post by Doug_Simms on 2015-03-08
I'm running a 64bit gigabyte mother board with an Intel I3 processor.  I'm running 12.04LTS and Mythbuntu v.27

I'm a newbie, so anyhelp would be appreciated.  I ran sudo apt-get update for ubuntu, mythbuntu, and mythtv updates.  Everything seemed fine until I rebooted my machine and now when it starts the frontend the screen is flashing and the frontend non stops crashing saying exit code 130.   I can't even get out of the crash loop.  I can barely get to the Power menu to shut it down.  Typing on terminal isn't almost impossible.  Not sure what is going on.  It was working fine until then.

---

### Post by MoebusNet on 2015-03-13
I had a similar situation recently. You can try unplugging the ethernet cable from your HTPC before booting it (it seemed to have something to do with my problem) before booting up.

If you still have the boot-loop issue with mythfrontend, you can attempt to close it by changing to a different virtual terminal (Ctl-Alt-F1 through Ctl-Alt-F6) then
```
sudo killall mythfrontend
sudo killall mythfrontend.real
```

You can change back to the GUI with Ctl-Alt-F7

I've disabled the autostart for mythfrontend in Mythbuntu Control Center for my system.

---

### Post by gregb492 on 2015-03-17
I've a similar problem, on bootup, on a new mythtv install, in that I'm stuck in mythfrontend.real. Each time I try to enter my country settings, I just go round and round in a loop.```
sudo killall mythfrontend 
sudo killall mythfrontend.real
```appear to have no effect at all.

---

### Post by MoebusNet on 2015-03-17
@Doug_Simms - I'm a mythbuntu newbie myself, so others may have better advice; that said I am under the impression that Mythbuntu is always based on the latest *buntu LTS release. In this case, 14.04.2 is the latest release; 12.04 has been depracated for a year+ (I believe). The current Mythbuntu iso uses ubuntu 14.04 and mythtv 0.27, so that may be the direction you want to look in.

@gregb492 - It sounds like your issue is a bit different. I suggest you start a new thread and include information like backend-only, frontend-only or combined backend/frontend, ubuntu version (eg. 14.04) and mythtv version (eg. 0.27) as well as info on hardware. The more information we have, the more likely someone can help.

---

### Post by gregb492 on 2015-03-17
I've tried completely removing all mythtv components in synaptic then running ```
sudo apt-get -f install 
sudo dpkg --configure -a 
sudo apt-get update
sudo apt-get upgrade
```Then installing mythbuntu, but end up with exactly the same problem because myth cannot connect to the database. I've tried installing mythbuntu as a clean system. That works fine, but I've issues trying to install other packages and getting my printer to work, so ubuntu mate seems a better option to me. 
(I am assuming that the problem that [**[COLOR=#000000]MoebusNet[/COLOR]**]("http://ubuntuforums.org/member.php?u=150834") has is a similar database one)

[SIZE=1]Ubuntu mate 14.04[/SIZE]

---

### Post by gregb492 on 2015-03-17
Thanks[**[COLOR=#000000] MoebusNet[/COLOR]**]("http://ubuntuforums.org/member.php?u=150834") 	 . I missed your update. I'll try and find an appropriate thread.

---

