---
title: "How do I reconfigure the graphics driver?"
date: 2011-10-15
forum: Multimedia Software
---

### Post by KeithLM on 2011-10-15
I've done something and mangled my graphics.  I just updated from 11.04 to 11.10 today and when I started the graphics just didn't seem right and it appeared to me that the nvidia drivers weren't being used.  I went into some drivers app that showed me two different nvidia driver options I could activate, both failed and told me to look at jockey.log which told me nothing.  

As it is now X just doesn't start and X log says that there is no nvidia driver and to look at the system log which tells me that it failed too many times to start GDM and to look at the X log.  

I've tried apt-get install nvidia-current and it runs then I run nvidia-xconfig and it says it's rewriting the xorg conf file, which when I look at it I see some basic settings, although no resolution set, but there's a monitor, device and screen defined, along with input devices.

Is there some other command line app I can run that will just kick off an auto-detect and reconfigure X for me?  I've got a GT 430 in there, it should work fine with the nvidia drivers.  It was working in 11.04 without a hitch.

---

### Post by pme 72 on 2011-10-16
I know this does not necessarily help you but are you supposed to disable any proprietary Nvidia drivers in 11.04 before upgrading to 11.10?

---

### Post by KeithLM on 2011-10-16
Well there were no warnings, and I used the update tool, so I guess there's a good chance there was something like that and they didn't tell me.  It'd be pretty typical of this stuff.

---

### Post by pme 72 on 2011-10-16
There is probably something in place to recommend removing the proprietary driver first if it could cause an issue. I remember reading a recommendation like that a couple of years ago but not recently. I can not remember if it was for ATI or Nvidia or both. The one time I upgraded to a new release I was using an open source Radeon driver which did not cause any problems.

When there is a kernel upgrade do you have to manually reinstall the Nvidia driver? Upgrading to 11.10 would certainly have involved a kernel update.

---

### Post by KeithLM on 2011-10-17
Well I put Ubuntu 11.10 on a USB drive and installed over my existing installation.  Lost some of my installed apps, but I managed to get things running again and have the latest nvidia drivers installed.

---

