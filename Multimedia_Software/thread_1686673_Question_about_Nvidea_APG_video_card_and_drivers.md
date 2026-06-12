---
title: "Question about Nvidea APG video card and drivers"
date: 2011-02-12
forum: Multimedia Software
---

### Post by Jon Anderson on 2011-02-12
I have just downloaded Ubuntu 10.10 and my VIA/s3g unichrome pro k8m800 APG in my Emachine T3104 freezes and I have to reboot to start Ubuntu over again(gets old). I can get a Nvideo Geforce4 mx440 APG for real cheap. When I put it in, will Ubuntu 10.10 have the drivers that will automatically install(I want it easy). Or if they don't, will Nvidia have them? If I get them from Nvidea, will they automatically install if I download them? One more question I see code in boxes in linux comment groups, do you copy and paste them to the terminal, is that what program you use and is that what is considered the command line. If you have two different boxes  with code, do you enter the first box in terminal then push enter then put the second box of code in terminal and push enter again. Sorry for the simple questions, You might of guessed that I'm new to this. I&#539;ll take any and all advice
Thank you
Jon

---

### Post by cascade9 on 2011-02-13
There isnt really an automatic install for the nvidia cards. You always need to click something, or use jockey (system-> administration-> hardware drivers). 

For the Geforce 4 cards, system-> administration-> hardware drivers wont work. You will need to add a PPA (personal package archive) or install the drivers manually. 

When d/l the drivers from nvidia, to get them working would have to do for a manual install, which involves dropping out of the desktop, running a few commands, then restarting. Its not that hard, but it can cause issues (if you get a new kernel you will lose your drivers, etc). 

Its probably a lot easier to use a PPA, if you end up getting a GF4MX. But it would be a lot easier to find a AGP 6XXX card, they will work with jockey without problems. 

I really wish that canonical would fix jockey with the geforce2-4 (96.xx) drivers.

---

