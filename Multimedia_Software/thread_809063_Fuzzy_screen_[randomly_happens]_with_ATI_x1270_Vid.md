---
title: "Fuzzy screen [randomly happens] with ATI x1270 Video Card"
date: 2008-05-27
forum: Multimedia Software
---

### Post by rookie2008 on 2008-05-27
Hi,

I am very new to the Ubuntu scene, but I am trying to get past the novice stage as soon as possible.  I finally got my wifi online, now I want to fix my video issues.  Every now and then when I boot up into Ubuntu the screen has this scratchy fuzz that goes on all throughout the monitor.  It only happens in Ubuntu and not in Vista.  So I think it is a driver problem.  My laptop is only 2 months old... and has not suffered any physical damage.  My video card is a ATI Radeon 1270 dedicated video is 384mb shared software memory is 575mb.  I was not able to locate a driver via the update manager.  I am going to browse the synaptics tomorrow.  Any pointers in the right direction would be greatly appreciated.  Thank you all in advance.

---

### Post by Kowalski_GT-R on 2008-05-27
Hi,

I am in no position to help unfortunately, I will but summarise the situation, to help you (eventually) make decisions.


Basically, Compiz+ATI aren't exactly best friends, and compiz-fusion is enabled by default in 8.04. If you search the forums, you'll find that people with similar setups (all ATI cards anyway) either run compiz or applications making use of OpenGL (such as games), never both at the same time.

I didn't find any universal solution to that for Hardy Heron.

I am running without graphics acceleration (no restricted drivers enabled) until I find a reliable solution to that (three main ways to solve the problem, namely, a. manual editing of config files b.install latest ATI Linux driver available c. use EnvyNG to install latest ATI driver, didn't work).

I guess this is due to be solved with updates or a new version of Ubuntu (depending on where the real problem is, if it has been spotted and addressed to).
I hope the terminology was enough "rookie-friendly".

Have at you :)

cheers,

Andre



EDIT: my exact same setup (see signature) worked under Ubuntu 7.04

---

### Post by rookie2008 on 2008-06-02
Thanks for the info,

I will look into this compiz business soon.

---

