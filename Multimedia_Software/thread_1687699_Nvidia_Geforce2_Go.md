---
title: "Nvidia Geforce2 Go"
date: 2011-02-14
forum: Multimedia Software
---

### Post by corwashere on 2011-02-14
I am simply posting this so that the next person that searches for any help about this video driver finds this useful.

To make a long story short. I had blank screen issues and driver installs that would render my laptop inoperable. The laptop had an Nvidia Geforce2 Go adapter in it.

At first I tried using the "96 driver" from the package manager, but I had problems with X just not starting up at all and I was stuck using the "standard driver" for some time until I started researching the problem again.

I FINALLY got it working by simply doing this:

1. I got the OFFICIAL nVidia driver from here:
[http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html)

2. I booted to a console and executed the file downloaded from the link. DO NOT execute this from within any X session. X must NOT be running and the install will not work at all.

3. After the installation completed, I restarted and everything is fine. GL graphics are working, no error message about glx being missing or anything. 

Using the proprietary drivers did not work for me. Simply installing the driver provided by nVidia was the solution. 

I've seen a bunch of post about how the Geforce2 Go is too slow to do anything, but all of my GL screensavers run smooth as glass. Sure, it's not going to be running high end games or anything like that but at least now I've been able to resurrect an old laptop to something useful.

Hopefully this post will help someone else who is having a hard time installing this driver.

-cor-

---

