---
title: "xorg spikes CPU"
date: 2008-12-23
forum: Multimedia Software
---

### Post by Cliff283 on 2008-12-23
A friend of mine and I recently switched from Windows XP to Ubuntu. We got everything switched over and working properly. We downloaded compiz and switched on a bunch of the cool 3D effects and they worked fine. 

A few days later my friends goes "app happy" and grabs a bunch of apps including an "ATI catalyst Control Center". 

A few days later he gets back on and notices if he tries to move a window it lags. After a few hours of research we discover that xorg is eating up 75-100 of bandwidth if anything on the screen moves. (This includes just having system monitor open). 

If I have him disable all of the compiz effects xorg drops to about 10-35 percent and the machine is usable again but even then it's eating up too many resources. 

On my machine it hovers between 1-5 percent which I'm guessing is where it should be. 

I've done research online and noticed lots of other people with a similar issue but not exactly the same (mostly NV cards). We've edited the xorg.config file a few different times and ways to no avail. 

I know he's got the system resources to handle advanced desktop effects because it was working fine earlier. I'm convinced the ATI catalyst app changed some setting that removing it did not fix. 

Any ideas?

Thanks,
Cliff

---

### Post by markbuntu on 2008-12-23
Well, you should only be using the Catalyst Control Center with the proprietary fglrx driver from ati and that driver is very easy to misinstall which you have done.

So, a little more information and we can try to get this straightened out. 
What distribution are you using?
What ati card are you trying to use?
Where did you get the driver from?
What version is it?
How did you install it?
Please post your Xorg.0.log file which you can find with System/Adminstration/System Log

---

