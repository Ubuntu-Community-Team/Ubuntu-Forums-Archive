---
title: "Flash Hangs on Fullscreen || 32 Bit Natty"
date: 2011-07-06
forum: Multimedia Software
---

### Post by linuxyogi on 2011-07-06
Hi,

When I click on fullscreen (youtube) PC hangs completely. I need to hard reset it. This is happening almost everyday.

Tried deselecting the hardware acceleration but no improvements.

Even in window mode flash is making the system very shaky.

Using FF 5.

---

### Post by An Sanct on 2011-07-06
What is you flash version?

Did you try [Flash AID?]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by linuxyogi on 2011-07-06
> **An Sanct said:**
> What is you flash version?

Did you try [Flash AID?]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

Using flash version 10.3.181.34ubuntu0.11.04.1. Installed it from the repos. 

Haven't tried [Flash AID]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") yet.

---

### Post by An Sanct on 2011-07-06
> **linuxyogi said:**
> Using flash version 10.3.181.34ubuntu0.11.04.1. Installed it from the repos. 

Haven't tried [Flash AID]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") yet.

I have version 10.3 d162 ... Please try Flash AID, [LovingLinux]("http://ubuntuforums.org/member.php?u=649167") puts a lot of time to make it perfect :) ... I cannot praise him enough ...

---

### Post by linuxyogi on 2011-07-06
> **An Sanct said:**
> I have version 10.3 d162 ... Please try Flash AID, [LovingLinux]("http://ubuntuforums.org/member.php?u=649167") puts a lot of time to make it perfect :) ... I cannot praise him enough ...

Just updated flash using Flash Aid. 

But the thing is FF says flash version is still 10.3.181.34, no change. Althoght the Flash Aid wizard offered 2 tweaks. Override GPU validation & Linux Hardware Video decoding (vdpau). 

I tried playing some videos in fullscreen. Good news is that the PC didn't hang. But just to make sure that the problem is really gone I will wait a few days & see how it performs. 

THANKS :D  to you & [LovingLinux]("http://ubuntuforums.org/member.php?u=649167").

---

### Post by linuxyogi on 2011-07-06
I doubt if vdpau is working CPU usage ranges from 40-45 % while playing a 720p video.

^ That's adobe's problem.

---

### Post by Sylos on 2011-07-06
Hello.

Is this happening on your celeron processor? (sure it was you I saw in a thread about old hardware talking about slow browsing etc). Are you getting the stuttery playback issues?

The vdpau will only work with nvidia cars and I think you may need to install a particular driver to enable the support. I looked into it a little when I had issues with not being able to play flash videos properly.

---

### Post by linuxyogi on 2011-07-06
> **Sylos said:**
> Hello.

Is this happening on your celeron processor? (sure it was you I saw in a thread about old hardware talking about slow browsing etc). Are you getting the stuttery playback issues?

The vdpau will only work with nvidia cars and I think you may need to install a particular driver to enable the support. I looked into it a little when I had issues with not being able to play flash videos properly.

No my old Celeron cant handle Natty !!! 

See my sig.

And this problem seems to be over.   

Thanks for replying.

---

### Post by lovinglinux on 2011-07-06
> **An Sanct said:**
> I have version 10.3 d162 ... Please try Flash AID, [LovingLinux]("http://ubuntuforums.org/member.php?u=649167") puts a lot of time to make it perfect :) ... I cannot praise him enough ...

> **linuxyogi said:**
> Just updated flash using Flash Aid. 

But the thing is FF says flash version is still 10.3.181.34, no change. Althoght the Flash Aid wizard offered 2 tweaks. Override GPU validation & Linux Hardware Video decoding (vdpau). 

I tried playing some videos in fullscreen. Good news is that the PC didn't hang. But just to make sure that the problem is really gone I will wait a few days & see how it performs. 

THANKS :D  to you & [LovingLinux]("http://ubuntuforums.org/member.php?u=649167").

Thanks guys. BTW, I just released a new version of Flash-Aid, that can also remove flash installed by sevenmachines and has compatibility with Firefox 8.0a1. This version is not approved by Mozilla yet, so you need to get it from [my site]("http://www.webgapps.org/add-ons/flash-aid").

BTW, YouTube cookies are messing things up again. If you experience problems on YouTube, delete YouTube cookies, clear the cache than block YouTube cookies in Firefox Privacy preferences.

---

### Post by linuxyogi on 2011-07-06
> **lovinglinux said:**
> Thanks guys. BTW, I just released a new version of Flash-Aid, that can also remove flash installed by sevenmachines and has compatibility with Firefox 8.0a1. This version is not approved by Mozilla yet, so you need to get it from [my site]("http://www.webgapps.org/add-ons/flash-aid").


Awesome !! I will install it as soon as I upgrade FF.

> **lovinglinux said:**
> 
BTW, YouTube cookies are messing things up again. If you experience  problems on YouTube, delete YouTube cookies, clear the cache than block  YouTube cookies in Firefox Privacy preferences.

I am using this addon [https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/).

So, do I need to block youtube cookies ? Just wanna confirm.

---

### Post by lovinglinux on 2011-07-06
> **linuxyogi said:**
> Awesome !! I will install it as soon as I upgrade FF.



I am using this addon [https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/).

So, do I need to block youtube cookies ? Just wanna confirm.

You only need to block YouTube cookies if have problems playing YT videos but not anywhere else.

I just created a new [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217").

---

### Post by linuxyogi on 2011-07-16
If using Nvidia, upgrading the driver may improve flash performance. 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) 

The current ver. is 275.19. I just installed it.

> 

  
[LIST]
[*]Added support for the following GPU:   GeForce GT 540M
[*]Fixed memory error and abort reported by glibc when running the application FieldView from Intelligent Light.
[*]Fixed an OpenGL driver bug that caused an application crash when running Altair HyperMesh.
[*]Fixed a performance problem when switching between stereo and monoscopic rendering in the application Smoke.
[*]Fixed poor X driver handling of pixmap out of memory scenarios.
[*]Fixed an interrupt handling deficiency that could lead to  performance and stability problems when many NVIDIA GPUs shared few  IRQs.
[*][COLOR=Red]Fixed bugs in the VDPAU presentation queue that could cause GPU  errors and hangs when destroying a presentation queue. This happens when   exiting applications, and also when toggling to and from full-screen  mode in Adobe Flash.[/COLOR]
[/LIST]
 


---

