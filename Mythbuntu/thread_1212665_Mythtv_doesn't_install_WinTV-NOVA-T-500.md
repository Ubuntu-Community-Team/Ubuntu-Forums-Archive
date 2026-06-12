---
title: "Mythtv doesn't install WinTV-NOVA-T-500"
date: 2009-07-13
forum: Mythbuntu
---

### Post by ubn2usr on 2009-07-13
Hi I'm new to Mythtv mostly because it doesn't detect my win nova card.
I have installed Mythtv on a new machine. I'll list the specs at the end of this post.
Firstly the card does work. I've been using it with cyberlink cinema on a dual boot machine.
I know that I said I was new to Mythtv/Mythbuntu. I am familiar with Linux and happy to use the command when needed.
j Folsom
Now for the specs.
XFX 9300 motherboard
Intel core duo cpu E8400
4gig ram

---

### Post by striscio on 2009-07-14
I'm having trouble with the same card. I followed instructions found here [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI"). I recompiled kernel modules and now the card get recognized, but the scan doesn't find any channel. I didn't try to turn on the onboard amplifier. I will try later at home.

Anybody has some hint?

---

### Post by fatmonk on 2009-07-14
ubn2usr> Which version of Myth are you using? Is it a Mythbuntu distro? This card is very common  and works well with Mythbuntu as you'll see in these forums (it was detected no problem with v8.04 and 8.10 for me). Version info might help someone spot where your problem is.

striscio> The internal amp (LNA) is a must on this card. It seems as though everyone has to enable ths to get any channels tuned. Once you enable that the scan shoudl work fine.

-FM

---

### Post by ubn2usr on 2009-07-20
ubuntu version Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4)
lsusb gives
Bus 003 Device 002: ID 2040:9950 Hauppauge 
Not really sure what I should do if you say that the card is supported out of the box.
Sorry it's taken so long to get back to you.

---

### Post by nasha on 2009-07-21
Ive had no personal experience with this card, but was looking at getting one and have done plenty of research about getting it going. 

ubn2usr: All that is required is to follow the steps at the link below:
[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Installing](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Installing)
striscio: From what i have read the on-board amplifier is a must.

And in order for any of the problems to be solved, please please post some info about what problem you are experiencing. 'doesn't detect my win nova card' just doesn't cut it. Post some logs and error outputs.
Supported out of the box means that with the correct installation & fw, it will work correctly, as with any OS

---

### Post by ReddogOne on 2009-07-21
> **striscio said:**
> ... [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI") ...

Anybody has some hint?

First time I installed mythTV I followed the link you gave. Now I've done a few install over the last year or so I'd say "Those instructions will not being you joy and probably result in a few tears of frustration"!

Whether you are install ubuntu and then mythtv or mythbuntu, you should already have all you need!!!!!!

(But after install of mythTV I've found its best to power cycle your PC. As it take the plug out of the wall so that card does a cold restart [if that's the correct term]. Not always needed but seems to help on other occasions)

For the capture card setup, choose "DVB DTV capture card (v3.x)" and not the other one that mentions PVR-500 (or something else tempting...it is like the snake in the tree offering you the apple... it is evil... well maybe not but it does not work, no idea what it is for).

You have to do that twice... one for each tuner but it sorts it [mythTV] all out for you.

---

