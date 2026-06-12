---
title: "Xorg version: 1.6.0 where to expext 7.x ... confusion"
date: 2009-05-19
forum: Multimedia Software
---

### Post by bernd.juchems on 2009-05-19
Hi folks ...

I have some major problems with my damn ATI Mobility Radeon X1900 in my Fujitsu Siemens Amilo Xi 1554, which is not supported by FSC, AMD/ATI or any other vendor I tried in countless hours of frustrating search at all.

Anyway, with accepting some trade-offs I'm able to work with my NB and Ubuntu (not mentioning watching movies or something like this).

But:
For some survey from AMD for my user experience (hell, their ears will ring), I am asked for my Xorg-Version I am currently using (lately switched to Jaunty).

So, searching for answers I find: "Xorg -version".
This gives me:
> X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ju-augustus 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.


All right ... 1.6.0 ...

And how does this fit with all the "Version 7.4", "Version 6.9" and so on, all the other Xorg users are talking about? That survey has a DropDownbox with Xorg versions from 6.7 to 7.4.

How does my 1.6.0 fit in?

Besides: in the examples for "Xorg -version" all the other people are getting "6.9" and so on.

What do I do wrong?

Please help ...

Bernd

---

### Post by adam_kimber on 2009-05-19
> **bernd.juchems said:**
> 
So, searching for answers I find: "Xorg -version".
This gives me:


All right ... 1.6.0 ...

And how does this fit with all the "Version 7.4", "Version 6.9" and so on,

Right first up. You seem to have confused X-org with X-Server. In a vague attempt to summarise this [wiki page]("http://en.wikipedia.org/wiki/X.Org_Server") and this [wiki page]("http://en.wikipedia.org/wiki/X_Window_System"), the x-server is part of the X windows system. Think of the X Windows system as the complete package of drivers, xserver etc and the xserver is one component, albeit probably one of the most important parts. 

Currently the Xorg implementation of the X Windows system is at X11R7.5 (X11 is the name of the X windows system). And the version of the x-server within that project is 1.6.1.

So like with most of GNU/Linux setup, it is comprised of lots of little programs, so theoretically you could swap out your xserver version and use a completely different xserver version, though it might break stuff unexpectedly. 

Have a look at [http://www.x.org/wiki/Releases/7.4](http://www.x.org/wiki/Releases/7.4) as it explains what came out when the overall release was first issued, it then contained xserver 1.5!

---

