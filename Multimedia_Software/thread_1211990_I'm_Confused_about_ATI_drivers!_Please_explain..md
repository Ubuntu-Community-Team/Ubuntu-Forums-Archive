---
title: "I'm Confused about ATI drivers! Please explain."
date: 2009-07-13
forum: Multimedia Software
---

### Post by oxf on 2009-07-13
I have some minor problems with graphics. Mostly no problem but freezes displaying some large intense PDF's and some freezing on video play. I was told a few weeks ago I should install a different driver and thats where I get confused. Sorry if these are silly questions!

First my details: Compaq Presario M2000 Laptop running Jaunty 9.04 (32bit)
AMD Turion 64 processor, 
ATI Radeon Express 200M graphics card
1GB Ram

I've been reading around here and find all sort of ATI compatibility issues discussed and ATI dropping support for Jaunty. What exactly does this mean? 

I have not added any additional drivers since I installed 9.04. Does that mean I have the "catalyst driver" installed now by default?

Looking under System>Administration>Hardware Drivers it say I have no  proprietary drivers installed.

How do I remove the catalystdriver?

And what should I install instead to improve performance? The ATI open source driver?
Where do I install that from?

What about this FGLRX driver thing? What is it and it seems to me there are some problems installing that to 9.04.

If some of you can explain all this to me and sort me out. I'm sure I'll have some more questions. ....Thanks...!

---

### Post by csabo2 on 2009-07-13
From what I've been told.  The version of Xorg that ships with 9.04 is not supported by ATI's drivers.  However, I did find this from the end of April.  Enjoy!

[http://news.softpedia.com/news/Latest-ATI-Linux-Driver-Introduces-Support-for-Ubuntu-9-04-109720.shtml](http://news.softpedia.com/news/Latest-ATI-Linux-Driver-Introduces-Support-for-Ubuntu-9-04-109720.shtml)

---

### Post by cozmicharlie on 2009-07-13
> Sorry if these are silly questions!
Not silly at all - ATI drivers are not easy to install.

> I've been reading around here and find all sort of ATI compatibility issues discussed and ATI dropping support for Jaunty. What exactly does this mean? 
ATI is supported in Jaunty but only the newer versions of Catalyst work with the version of xorg in Jaunty.  Many of the older cards were dropped and now fall under the legacy drivers.

> I have not added any additional drivers since I installed 9.04. Does that mean I have the "catalyst driver" installed now by default?
No - it is not installed.  FYI - Catalyst is proprietary.  Ubuntu does not install proprietary drivers out of the box.

> Looking under System>Administration>Hardware Drivers it say I have no  proprietary drivers installed.
Do you have any driver listed when you open this?

> How do I remove the catalystdriver?
it is not installed.

> And what should I install instead to improve performance? The ATI open source driver?
Where do I install that from?
Yes - you will get better performance from the ATI driver.  But, which driver you install depends on what you want to do.  If you need 3d graphics or graphics intensive projects then you need the ATI driver.  However, I assume since you only have 1 gb of memory you are not doing anything too demanding. The open source driver should work for basic video and editing pdf's.  

> What about this FGLRX driver thing? What is it and it seems to me there are some problems installing that to 9.04.
Catalyst is the ATI driver control.  FGLRX is the 3D accelerator.  Linux is different than windows - the drivers are in the kernel so if you want to install the ATI drivers you need Catalyst, FGLRX and FGLRX kernel.

If some of you can explain all this to me and sort me out. I'm sure I'll have some more questions. ....Thanks...!

If you don't need 3D then go with the Radeon drivers.  If you need more intensive 3D or video then you need the FGLRX drivers (ATI proprietary).  However, you have an older card and only 1 gb of RAM so even with the drivers, you are not going to be able to play 3D intensive games or watch HD video (which I assume is not your goal). I suspect the pdf you mentioned has images in it.  In those cases the ATI driver should help.  They definitely improve video performance in my experience.

If drivers are listed when you go to System>Administration>Hardware Drivers, the easiest method to install them is to activate them.  I have never been able to get the ATI drivers to work this way but you could try.  If no drivers are listed, then you have to install them manually.

I would try this first (see post #4) [http://ubuntuforums.org/showthread.php?t=1009978&highlight=ATI+Radeon+Express+200M+](http://ubuntuforums.org/showthread.php?t=1009978&highlight=ATI+Radeon+Express+200M+) 
It is easy.  If this does not work then post back and I can help you install it manually.

hope this helps.

---

### Post by oxf on 2009-07-14
> **cozmicharlie said:**
> 
If you don't need 3D then go with the Radeon drivers.  If you need more intensive 3D or video then you need the FGLRX drivers (ATI proprietary).  However, you have an older card and only 1 gb of RAM so even with the drivers, you are not going to be able to play 3D intensive games or watch HD video (which I assume is not your goal). I suspect the pdf you mentioned has images in it.  In those cases the ATI driver should help.  They definitely improve video performance in my experience.

If drivers are listed when you go to System>Administration>Hardware Drivers, the easiest method to install them is to activate them.  I have never been able to get the ATI drivers to work this way but you could try.  If no drivers are listed, then you have to install them manually.

I would try this first (see post #4) [http://ubuntuforums.org/showthread.php?t=1009978&highlight=ATI+Radeon+Express+200M+](http://ubuntuforums.org/showthread.php?t=1009978&highlight=ATI+Radeon+Express+200M+) 
It is easy.  If this does not work then post back and I can help you install it manually.

hope this helps.

Yes that helps quite a lot, Thanks.

When I go to System>Administration>Hardwaredrivers the only drivers listed is the B43 for my wireless card. So I will brave up and try the manual route!

I'm not bothered about 3D games at this point. The PDF's I had trouble with were dowloaded maps. Quite detailed graphics but the file sizes were large, around 12-14 MB each. They actually displayed just fine but after scrolling around a few time it froze my PC up completely and I had to crash it. 

I also noticed that some DVD videos were jerky at times, parts would run slow, and fast forward could cause it to freeze on occasions.

Someone previously told me I needed to install XF86-video-ATI. Looking in synaptic I see a lot of XF86 instaled.

---

### Post by oxf on 2009-07-14
Hmmm?   Synaptic indicates I have the following installed:

xserver-xorg-video-radeon
xserver-xorg-video-ati
radeontool


I have just tried the sugestion in post 4 you sugested. i.e removing and reinstalling the drivers. However, result is the same, they do not show up in Systen>Admin> Hardwardrivers!

---

### Post by cozmicharlie on 2009-07-14
> **oxf said:**
> Hmmm?   Synaptic indicates I have the following installed:

xserver-xorg-video-radeon
xserver-xorg-video-ati
radeontool


I have just tried the sugestion in post 4 you sugested. i.e removing and reinstalling the drivers. However, result is the same, they do not show up in Systen>Admin> Hardwardrivers!

That is because you have an older card which is now supported by the legacy drivers (i.e. the radeon drivers).  Ubuntu installed these by default.  The radeon driver is the open source version of the ATI driver.  If you want to use the proprietary drivers then you will have to install them manually.  Did you have Windows on this before you loaded Ubuntu and if so were you able to do all the tasks in windows you are trying to do in Ubuntu?  If so then adding the proprietary drivers probably will make a difference since they were most likely installed in Windows.

Let me know if you want to give it a shot and install the proprietary drivers and I will walk you through the installation.  It is a little tricky because only the newer versions of ATI's drivers work with xorg in Jaunty but it is doable and the worst that can happen is we have to uninstall the ATI drivers and reinstall the radeon drivers.

---

### Post by mcduck on 2009-07-14
> **oxf said:**
> Hmmm?   Synaptic indicates I have the following installed:

xserver-xorg-video-radeon
xserver-xorg-video-ati
radeontool


I have just tried the sugestion in post 4 you sugested. i.e removing and reinstalling the drivers. However, result is the same, they do not show up in Systen>Admin> Hardwardrivers!

System/Administration/Hardware Drivers only shows proprietary drivers. Ati/radeon driver is opensource and is used by default for all Ati cards on 9.10. 

And yes, this is the best possible driver for all Ati cards apart from the ones supported by fglrx (the cards with R600 or later GPU).

edit: The opensource ati driver in 9.10 works great with Radeon Express 200M, so you shouldn't have to worry about it. If you use fglrx or some other driver in 9.04 you may want to make a fresh install of 9.10 instead of upgrading, just to get completely rid of old drivers and xorg configurations.

---

### Post by markbuntu on 2009-07-14
Do not use the proprietary fglrx driver with the xpress200m. It is not supported by any driver that will work with 9.04 or 9.10.

---

### Post by oxf on 2009-07-14
> **cozmicharlie said:**
> 
Let me know if you want to give it a shot and install the proprietary drivers and I will walk you through the installation.  It is a little tricky because only the newer versions of ATI's drivers work with xorg in Jaunty but it is doable and the worst that can happen is we have to uninstall the ATI drivers and reinstall the radeon drivers.

Let me think about this overnight. I'm a tad concerned given the last comment by markbuntu. Yes I previously had a Windows XP (still do on the other partition) and experienced no video problems.
Thanks

---

### Post by triplesquarednine on 2009-07-14
> **oxf said:**
> Let me think about this overnight. I'm a tad concerned given the last comment by markbuntu. Yes I previously had a Windows XP (still do on the other partition) and experienced no video problems.
Thanks

as a rule of thumb, you should not be comparing how video handles, winXP vs. Ubuntu.
windows has alot more support(and experience) with these companies and cards, in comparision to linux. openGL performs very poorly (especially when Compiz is present).

it sounds to me mike, that you need the radeon opensource driver...on my old dell-laptop i had a similar card to yours, although slightly newer(can't remember the model, maybe an rv250?). maybe a model or two up from yours.

i myself highly doubt the fglx ati-driver will work, although if it doesn't, you can start in safe graphics mode, and remove it....i would stick with open-source. better perfomance... there is a tutorial in the forums - ATI specific, that explains the differences in drivers and the installation process, google it or look in the forums.   "ati opensource driver + ubuntu 9.10" or ati drivers + ubuntu 9.10"
                                                          (jaunty)

after you get it setup there are ways of tweaking performance out of the driver, at the commandline - you may have to do a bit of reading on that, in the manual for the driver...  and also other system tweaks that will improve video/audio/multimedia...

cheers, and happy trouble-shooting!

---

### Post by oldrocker99 on 2009-07-14
The surest way I have found to completely hose a Jaunty setup IS to install the 9.03 drivers. As previously posted, they can be removed from the command prompt in safe mode, but it's best to not even try.

I'm currently rocking Intrepid WITH the 9.03 drivers and everything works just fine.):P It does appear that the solution is being worked on, whether by Canonical (this is a VERY well-known problem), or by the Xorg developers (and they also are well aware of the problem).

So, either stay with the admittedly much-improved open-source radeon drivers, or do what I did and go back to 8.10.

Or, you can wait.

:guitar:

---

### Post by oxf on 2009-07-15
> **cozmicharlie said:**
> That is because you have an older card which is now supported by the legacy drivers (i.e. the radeon drivers).  Ubuntu installed these by default.  The radeon driver is the open source version of the ATI driver.  If you want to use the proprietary drivers then you will have to install them manually.  Did you have Windows on this before you loaded Ubuntu and if so were you able to do all the tasks in windows you are trying to do in Ubuntu?  If so then adding the proprietary drivers probably will make a difference since they were most likely installed in Windows.

Let me know if you want to give it a shot and install the proprietary drivers and I will walk you through the installation.  It is a little tricky because only the newer versions of ATI's drivers work with xorg in Jaunty but it is doable and the worst that can happen is we have to uninstall the ATI drivers and reinstall the radeon drivers.

Well I've thought about the various comments here and since I have the Radeon drivers installed already I'm going to play it safe and stick with them. I appreciate your offer to walk me through it and may take you up on it at some point but not right now.

> **triplesquarednine said:**
> 
it sounds to me mike, that you need the radeon opensource driver...on my old dell-laptop i had a similar card to yours, although slightly newer(can't remember the model, maybe an rv250?). maybe a model or two up from yours.

i myself highly doubt the fglx ati-driver will work, although if it doesn't, you can start in safe graphics mode, and remove it....i would stick with open-source. better perfomance... there is a tutorial in the forums - ATI specific, that explains the differences in drivers and the installation process, google it or look in the forums. "ati opensource driver + ubuntu 9.10" or ati drivers + ubuntu 9.10"
                                                          (jaunty)

after you get it setup there are ways of tweaking performance out of the driver, at the commandline - you may have to do a bit of reading on that, in the manual for the driver... and also other system tweaks that will improve video/audio/multimedia...

cheers, and happy trouble-shooting!

Yes I do have it working reasonably well right now and as I said above I'll stick with what it installed by default, i.e the Radeon drivers. I will though try tweaking things a bit.

---

