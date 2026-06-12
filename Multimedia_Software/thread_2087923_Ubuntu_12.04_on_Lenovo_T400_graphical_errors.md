---
title: "Ubuntu 12.04 on Lenovo T400 graphical errors"
date: 2012-11-25
forum: Multimedia Software
---

### Post by Prometheus418 on 2012-11-25
Hello-

My old laptop died a couple of weeks back, and I bought a new (to me- it's actually a refurb) Lenovo T400 to replace it.  At first, I tried to simply pull the SSD from my old Dell d630 and plug it into the new machine, but there were a number of annoying crashes, so I decided to use the holiday weekend to reinstall from scratch.

As I had some extra space, I decided to install openSUSE on a separate partition to check it out, and it runs without any issues that I have been able to see- and the same goes for Linux Mint running off a live CD- this is specifically an Ubuntu problem.

This machine comes with an Intel GMA 4500- not an awe-inspiring card, but it should be relatively solid for normal use- I'm not gaming on this thing, I just need it to be stable with office and task management software.

What I'm getting is as follows:
"Sorry, Ubuntu 12.04 has experienced an internal error."
Executable path:
/usr/share/apport/apport-gpu-error-intel.py
Package:
xserver-xorg-video-intel 2:2.17.0-1ubuntu4.2
ProblemType:
Crash
Title:
[gm45] GPU luckup render.ipehr: 0x78080003
ApportVersion:
2.0.1-0ubuntu15
Archetecture:
amd64
 
<<Snip- apologies for this, the text is too much to type in, and I am entering this on my desktop manually- it's repeatable, if the extra info is required.>>

DuplicateOf
[https://bugs.launchpad.net/bugs/982010](https://bugs.launchpad.net/bugs/982010)

Basically, what happens is that the system kills Cairo-dock, Unity, and the frames around any open windows.  Guake will still work to allow me to reboot, but without a fix for this, it's a system killer for me, and I have to go to another distro.

It doesn't appear that this bug has been fixed, I'm wondering if anyone has any suggestions here- I've tried a number of other OSes, but I like ubuntu the best, and would prefer to stick with it.  It appears that Mint does not have this problem, so that is my fail-safe option here.

Thanks for any help or advice you can offer.  I know there is a command to restart x, but that's a bandaid that will wear thin very quickly.

---

### Post by 2F4U on 2012-11-25
I had the same issue with either 12.04 and 12.10 on a MacBook. However, in my case there were no practical consequences from the error, i. e. Ubuntu was still working, so I decided to just disable error reporting.
In your case it seems to have serious consequences. In my experience, this seems to be problem isolated to Ubuntu with Unity, so if you would like to stay within the Ubuntu family, you could check out either of Kubuntu (resource intensive), Xubuntu or Lubuntu. All of these share the same software base with Ubuntu, but only Kubuntu has the same support period (5 years). Xubuntu has 3 years and Lubuntu is not even LTS, so that in the case of Lubuntu it may be better to install 12.10.

---

### Post by Prometheus418 on 2012-11-25
> **2F4U said:**
> I had the same issue with either 12.04 and 12.10 on a MacBook. However, in my case there were no practical consequences from the error, i. e. Ubuntu was still working, so I decided to just disable error reporting.
In your case it seems to have serious consequences. In my experience, this seems to be problem isolated to Ubuntu with Unity, so if you would like to stay within the Ubuntu family, you could check out either of Kubuntu (resource intensive), Xubuntu or Lubuntu. All of these share the same software base with Ubuntu, but only Kubuntu has the same support period (5 years). Xubuntu has 3 years and Lubuntu is not even LTS, so that in the case of Lubuntu it may be better to install 12.10.

Thanks for the feedback-  I installed ubuntu 12.04 three times, and 12.10 once, with no luck.  Luckily, Mint 12.2 is working like a champ, as is OpenSUSE.  Once I got the GUI configured the way I like it, there is very little difference between Cinnamon and Unity (I hide them both anyhow) and all the same apps work.

I guess I'm going to mark this one solved.  Must be a case of the developers having different hardware to play with- but that's ok, at least I did not have to go back to Windows. 

I don't know if it's just because I stare at Windows all day, or because there really is a difference in the usability of Windows V. Linux, but I'm glad it didn't come to that- the internet connection is my family's entire entertainment budget, so it's nice to be able to enjoy the laptop and not feel like I'm still at work.

At any rate, I still have three Ubuntu machines, so I'll probably have more questions/issues in the future- thanks again for all the hard work you folks put in designing and supporting code.

---

