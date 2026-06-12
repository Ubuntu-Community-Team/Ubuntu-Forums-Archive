---
title: "Help with random hard crash"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by tp241303 on 2007-03-01
On my instllation of 64bit edgy I am experiecing random hard crashes, the screen completely locks and I can do nothing to get out of it except to turn of the machine. I have and amd athlon 64 x2 4600+ with a Nvidia 7800 gt oc graphics card on an asus A8R32-MVP Deluxe motherboard.  Any suggestions on why this is happening and how to rectify it?  I think it might have something to do with the graphics card not wanting to play nice with the motherboard because of the ATI chipsets on the motherboard but I do not know for sure. I have tried every way I can think of to install the graphics driver for the nvidia card and have updated to the latest kernel in hopes of the hardware being supported with no luck.  Any suggestions would be appreciated. I have run this same setup in Suse 10.1 64bit and did not experience this problem.

---

### Post by DrMega on 2007-03-01
Have you installed the package "NVIDIA-GLX"? from Synaptic? That contains the proper nVidia driver. If you can't see it you will have to enable the universe and multiverse repositories (in Synaptic go to Settings->Repositories).

Install that via Synaptic and if you're lucky it will configure it all up for you (it worked for me).

---

### Post by tp241303 on 2007-03-01
Thanks for your suggestion I have tried that.  I have the nvidia driver installed and the 3d acceleration works fine and everything the problem is that the computer will randomly freeze and the only way to get out of it is to hit the power button.

---

### Post by atonello on 2007-05-19
Hi, tp241303
Did you solve your problems?

I'm writing beacuse I have the same motherboard with an Nvidia 7300 and the only way for me to use Ubuntu (no matter if 6.06, 6.10 and now 7.04 - either i386 or 64bit version) is to stay with the "nv" graphic driver. 
Using the proprietary drivers by Nvidia, inevitably causes hard locks of the machine (only remedy is hitting reset button). 
There are others, with this problem, that posted here:
[http://www.nvnews.net/vbulletin/showthread.php?t=87918](http://www.nvnews.net/vbulletin/showthread.php?t=87918) 
[http://www.nvnews.net/vbulletin/showthread.php?t=83479](http://www.nvnews.net/vbulletin/showthread.php?t=83479)

p.s. For what I had seen thus far, it seemed that only 7300 cards were affected; but now I see that even your 7800 suffers such locks-up :(

---

### Post by fain on 2007-05-24
i experience random lock ups but only when SLI is enabled. other than that 3d and the rest runs fine

---

### Post by atonello on 2007-05-29
@ fain
I see your motherboard is different (Nvidia chipset if I'm not wrong; while mine's from Ati - *regarding its chipset*). In the first thread I linked (Nvidia linux forum) some users suspected some form of incompatibility between NV7300 cards and motherboards with Ati chipsets for AMD cpus. I was also thinking of replacing the troublesome card with a 7600...
tp241303's post made me stop!

Anyhow - after 6 months, I got rid of the 7300 and put an old AtiX300: in no more than 5 minutes I got 3d acceleration with its (so blamed - on the forums) proprietary drivers! And not even one trouble...

Funny thing is that I bought Nvidia right because of its - supposed - better driver support in linux... :(

---

### Post by fain on 2007-05-29
im not positive yet but i haven't had a lockup since the kernel update that just hit. not sure why or even if thats it.
b4 the update i enabled sli after a fresh install, it worked great till i rebooted then it started locking up so i left sli enabled and just didn't run any 3d apps. now after the kernel up date i can run all my 3d apps and havent locked up yet /crossesfingers and /knocksonwood

---

### Post by fain on 2007-05-29
haha so much for stupid superstition's. i just opened a wmv file in totem and it locked up. :(

---

### Post by atonello on 2007-05-29
> **fain said:**
> haha so much for stupid superstition's. i just opened a wmv file in totem and it locked up. :(

I'm sorry that you didn't sort the problem out, yet

---

