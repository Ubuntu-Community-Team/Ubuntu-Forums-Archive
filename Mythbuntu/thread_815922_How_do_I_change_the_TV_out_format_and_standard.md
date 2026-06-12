---
title: "How do I change the TV out format and standard?"
date: 2008-06-02
forum: Mythbuntu
---

### Post by RTucker on 2008-06-02
Hi all,
 
I have just installed MythBuntu 8.04 on a test system and during the install set the TV out settings to Component and HD576i.
 
This dosen't work very well on the TV I have (stretched, not centred) which is the TV's fault not mythbuntu's. So I'd like to change to Composite PAL-B (Australian TV).
 
When ever I change the TVStandard in xorg.conf to PAL-B, I get a black screen once X starts (display is perfect until then). When I change TVOutFormat to COMPOSITE, I get a blue screen when X starts (ie. no signal getting to the TV) and again, its perfect while booting.
 
I HAVE been able to change TVStandard to HD480i with no trouble.
 
The system is a P4 530 3GHz, Intel 915P based MB, and nVidia 6600GT.
 
Any help would be greatly appriciated.

---

### Post by agamotto on 2008-06-03
Call me insane, but shouldn't you be changing your PAL settings in Myth Backend Setup, not in the xorg.conf file?

---

### Post by RTucker on 2008-06-03
Probably...
 
But after having no luck getting any combination of settings other than COMPONENT and either HD480i or HD576i to work, I formatted the system and selected COMPOSITE and PAL in the initial setup. And guess what? Same Problem. Once X starts the screen goes blue as the TV is recieving no signal.
 
But if I start up to a consoe and change xorg.conf back to component and HD480i, I get display after a restart.
 
...I really hate TV Out
 
It always works perfectly until you get to an operating system (I've now found this in windows AND linux). Why is it that I can go buy any DVD player and plug it in via composite or component and it works with no problems and no setup? It fills the screen, no stretching, no problems. But from a pc its always a nightmare.
 
Anyway... thats my little rant.
 
Thanks for any further advice.

---

### Post by s_g_robertson on 2008-06-04
> **RTucker said:**
> Probably...
 
But after having no luck getting any combination of settings other than COMPONENT and either HD480i or HD576i to work, I formatted the system and selected COMPOSITE and PAL in the initial setup. And guess what? Same Problem. Once X starts the screen goes blue as the TV is recieving no signal.
 
But if I start up to a consoe and change xorg.conf back to component and HD480i, I get display after a restart.
 
...I really hate TV Out
 
It always works perfectly until you get to an operating system (I've now found this in windows AND linux). Why is it that I can go buy any DVD player and plug it in via composite or component and it works with no problems and no setup? It fills the screen, no stretching, no problems. But from a pc its always a nightmare.
 
Anyway... thats my little rant.
 
Thanks for any further advice.

Are you using the Nvidia Driver (Restricted, proprietary or whatever they call it?)  If so there is a utility nvidia-settings that looks as though it should do what you want to do but I couldn't get it to!  But I at least like it in that I have managed to fiddle around with settings without irrecoverably breaking things like I have in the past.

I have also found this [http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/README/README.txt](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/README/README.txt) which is very extensive and quite clear documentation on the contents of etc/X11/xorg.conf

I found that by adding the "PAL-I" option (I'm in the UK) then the nvidia settings application gave me a different list of resolutions.

Not sure if this is really of any help but there may be something in this application or documentation that may help.

I'll follow this thread with interest in the hope that someone can come along and give a simple rundown on all this!

Cheers
Stephen

---

### Post by peakshysteria on 2008-06-04
Are you sure the Nvidia driver is running? Sounds like the a driver issue. Not that I know my way around Nvidia troubles...

---

