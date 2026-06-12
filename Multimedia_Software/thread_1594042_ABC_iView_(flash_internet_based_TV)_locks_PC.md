---
title: "ABC iView (flash internet based TV) locks PC"
date: 2010-10-11
forum: Multimedia Software
---

### Post by GROwen on 2010-10-11
Hi all,

My PC completely freezes after viewing any program on ABC's (Australian Broadcasting Corporation) iView service. The time at which it occurs varies but it completely locks the PC.

I'm running 10.04.1 and have an Nvidia 6200 card, I'm running the propriety drivers. 

Could this be an issue with my graphics card? I updated it a couple of months ago and can't think of any other changes that have been made.

I have the latest version of Flash.

My biggest problem has been coming across someone else who has experienced the problem so how should I be going about trying to debug it?

Thanks in advance for your help, really hoping I can get this sorted because I love the service.

---

### Post by Rodney9 on 2011-07-20
Same here on Xubuntu 10.10

---

### Post by Rodney9 on 2011-07-20
Can anyone use this -  

[http://www.abc.net.au/iview/]("http://www.abc.net.au/iview/") ???


Rodney

---

### Post by drdos2006 on 2011-07-20
I found I needed to uninstall the nvidia drivers.
I am running Flash-Aid in Firefox on Ubuntu 10.4 64bit.

You may need to install startupmanager with :-
sudo apt-get install startupmanager
before you reboot.

Launch the Startup Manager from "System -> Administration -> Startup-Manager"
In the "Boot options" tab, change the resolution to something your monitor can handle (1024x768 is usually enough for the boot screen to look nice).
Change the color depth to "24 bits" and Press the "Close" button. Follow with a reboot.

regards

---

### Post by Rodney9 on 2011-07-21
Thank You drdos2006 Flash-Aid in Firefox fix it.

---

### Post by aiming0420 on 2011-07-21
Well, yeah, you are probably right.:guitar:

---

