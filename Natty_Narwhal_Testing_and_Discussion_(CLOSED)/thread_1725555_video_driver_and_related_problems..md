---
title: "video driver and related problems."
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Duncan Williams on 2011-04-09
video driver and related problems.
Hi, I installed `Natty' a few days back.
Everything went fine as far as installation goes.
When I boot into ubuntu, I just get a black screen.
When I boot into recovery mode, Use fail-safe graphics everything works ok.
On recovery boot it shows errors for Nouveau (nvidia).

I don't feel comfortable to uninstall video drivers and X stuff in case I lose the installation.

I have a nvidia geforce (5200/ I think) 128mb video card.

I want to sort this out so I can get proper access to my video card (and the 128mb onboard it)

I have looked around and got a bit of a lid on the fact that older nvidia cards are not really supported and the drivers are not open-source etc.

What do I do to resolve these issues. I am new to linux and not comfortable with console/terminal based stuff.

It worked ok in ubuntu 10.1 (although the screen resolution changed occasionally)
__________________

---

### Post by cariboo on 2011-04-10
The driver for your video card hasn't been updated to support the latest Xorg-xserver. If you want to try Unity, you'll have to try the 2D version that is in the repositories. I'd suggest, though, that if you aren't comfortable with a terminal, that you wait until Natty is released, as there are still quite a few bugs that need fixing.

---

### Post by Duncan Williams on 2011-04-10
I am very happy with the alpha/beta of natty. I think its in non/unity mode (as per my first post).

I can quite easily live with it as it is, if thats the best solution.

I had a look at nvidia drivers, nouvea was offered as additional drivers.

I don't want to disable say nouvea and install say nvidia and then find out I can't boot up at all.

So is it easy to switch to 2d nvidia drivers and if so, how do I change it over.
Thank you very much for response.

---

### Post by as2000 on 2011-04-19
It's very easy to switch to 2d. Just boot into classic desktop and then run synaptic. Search for Unity and 2d should display into the result. Select and install. Reboot, and you should see 2d as a choice in desktops in the login screen. I want to use 3d too with my punky 7200ls, but I am quite satisfied with 2d. I figure in time, the issues will be worked out and I can use my graphics card "the way it's meant to be played".

---

### Post by Duncan Williams on 2011-04-19
Well took the plunge and followedf your advice, installed unity 2D and associated. 
Nothing changed after install.
rebooted and same options and same desktop (unity with no launcher icons)

---

### Post by ELD on 2011-04-19
> **Duncan Williams said:**
> Well took the plunge and followedf your advice, installed unity 2D and associated. 
Nothing changed after install.
rebooted and same options and same desktop (unity with no launcher icons)
 
May sound stupid, but did you change your session to the 2d one?

---

### Post by Duncan Williams on 2011-04-19
the startup comes up (grub?)
4 options I think:
ubuntu
recovery mode
terminal
windows

The old kernels got cleaned with recent update.

No classic mode, 2D mode, Gnome mode.
that I can seem to see.

---

### Post by cariboo on 2011-04-19
You change your session from the login screen, not at boot.

---

### Post by Duncan Williams on 2011-04-20
OK, a month later someone finally tells me about the settings available on the bottom of the screen before logging into ubuntu.
I knew it must have been something obvious just not that obvious.
So changed it to 2D unity and I have icons, etc.

Nearly 6 weeks since I first tried linux.

---

### Post by VinDSL on 2011-04-20
> **Duncan Williams said:**
> OK, a month later someone finally tells me about the settings available on the bottom of the screen before logging into ubuntu.

I knew it must have been something obvious just not that obvious.

So changed it to 2D unity and I have icons, etc.

Nearly 6 weeks since I first tried linux.
Heh!  We've all been there, so don't feel bad!

When I'm writing code (regex, ajax, etc) I can pick the fly feces out of pepper. 

Other times, I overlook some of the most obvious things, that it's frightening.

My wife half-jokingly calls it "Male Pattern Blindness".  LoL!  :D

---

### Post by Duncan Williams on 2011-04-20
it was a good learning curve.
XP > maverick > natty/unity.
in 3 weeks.
then scratch my head and say to myself 
`this will all make sense when you work it out'
I'm sorta getting there.
Anyway:
Unity > fine but no launcher icons 
unity 2D > Fine
Classic > fine
on nvidia fx5200 video card using nouveau open source and no proprietory drivers.
as at 20/4/11.

-----SOLVED------

---

### Post by Duncan Williams on 2011-04-20
duplicate, sorry

---

### Post by Duncan Williams on 2011-04-21
Well, nvidia driver (173) showed up in `additional drivers' overnight, so I installed it.
If you look at the screenshot below.
you can see that it is not correctly recognised in additional drivers. 
It seems to function correctly in unity 2D but wont bring up normal unity.
I was getting used to and liking unity with no icons in launcher as per my previous drivers. (nouveau).

[http://files.myopera.com/DuncanWilliams/usercss/vide-drivers.png](http://files.myopera.com/DuncanWilliams/usercss/vide-drivers.png)

---

### Post by Duncan Williams on 2011-04-22
I was doing well with the nouveau drivers that offered themselves in `additional drivers' as `experimental 3d drivers for nvidia cards'.
Could boot into unity, the only real issue was `no icons in launcher' at 1920 by 1024 (on 24" aoc monitor).

Then a few days back `nvidia drivers for 3d support' showed up in `additional drivers' so I installed it. 

After a few boots it sorta worked and then would only come up in 640 by 480 mode.

So I removed the nvidia drivers in `additional drivers'.

Now I am (I think) using nouveau drivers, but I can't set my resolution past 1024 by 1080.

How can I get the system to re-read the monitor and video card again or set to original default. or just get the thing to the right resolution (1920 by 1024)

---

