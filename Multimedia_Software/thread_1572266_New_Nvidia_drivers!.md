---
title: "New Nvidia drivers!"
date: 2010-09-10
forum: Multimedia Software
---

### Post by BobvanderPoel on 2010-09-10
My system installed the new nvidia driver today. Version 260.19.04. Wow ... so much better than anything before. Even youtube videos are playing better!

If you've not got it in your updates, I highly recommend you check your repositories ... you might have to search around to get the right one (sorry, I don't recall what does which on my system anymore).

---

### Post by Yellow Pasque on 2010-09-10
Heh. Before you make a thread announcing the great new package you got, you might want to fire up Synaptic and use the 'Origin' filter to figure out where you got it from (unless it's in the standard repos).

---

### Post by JohnnyC35 on 2010-09-10
I'm currently running 260.19.04 I think it's from sudo add-apt-repository ppa:nvidia-vdpau/ppa
seems to run fine. had to go back to vesa mode and use jockey to get my display fixed though. Runs smooth now.

---

### Post by tommcd on 2010-09-10
> **JohnnyC35 said:**
> I'm currently running 260.19.04 I think it's from sudo add-apt-repository ppa:nvidia-vdpau/ppa

Is this the beta driver? The newest driver on the nvidia.com site is 256.53. The 260 driver is still listed as beta as of 09-08-10:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)
[http://www.phoronix.com/scan.php?page=news_item&px=ODU3NQ](http://www.phoronix.com/scan.php?page=news_item&px=ODU3NQ)

---

### Post by JohnnyC35 on 2010-09-11
Yes this is the one listed as Beta on the site:

> 
**[SIZE=1]Linux Display Driver - x86[/SIZE]**

[SIZE=1] [/SIZE]
 

[SIZE=1]
[/SIZE]**[SIZE=1]Version:[/SIZE]**

**[SIZE=1]260.19.04 BETA[/SIZE]**

**[SIZE=1]Release Date:[/SIZE]**

**[SIZE=1]2010.09.08[/SIZE]**

**[SIZE=1]Operating System:[/SIZE]**

**[SIZE=1]Linux[/SIZE]**

**[SIZE=1]Language:[/SIZE]**

**[SIZE=1]English (U.S.)[/SIZE]**

**[SIZE=1]File Size:[/SIZE]**

**[SIZE=1]26.9                           MB[/SIZE]**




---

### Post by dirty_harry on 2010-09-11
I've installed the lasted **website version **yesterday: 256.53

But this stuff about youtube etc. is true. Now I'm able to watch youtube with 480p and other streaming websites e.g. h264-streaming in full screen. 8)  The Flash hardware acceleration seems to work.

---

### Post by BobvanderPoel on 2010-09-11
> **Temüjin said:**
> Heh. Before you make a thread announcing the great new package you got, you might want to fire up Synaptic and use the 'Origin' filter to figure out where you got it from (unless it's in the standard repos).

Thanks for pointing this out ... next time I find something great I'll just keep it to myself. And, I did mention in the posting that I didn't remember which repository, etc ... oh well.

Oh, and I have no idea what the Origin filter is. Next time you post a snarky comment you might want to be more clear.

Sorry, I'm very tired and not having a great day.

---

### Post by gianluca.pettinello on 2010-09-12
Hi all
I tried to install nvidia 260.19 on my sony vaio f11b4e with nvidia gt330 m and have balnk screen. Is there any having the same problem?

Thanks
Gianluca

---

### Post by b0b138 on 2010-09-12
its this repo btw   ppa:ubuntu-x-swat/x-updates

---

### Post by BobvanderPoel on 2010-09-12
> **b0b138 said:**
> its this repo btw   ppa:ubuntu-x-swat/x-updates

Yes, that's the one. Thanks!

---

### Post by keypox on 2010-09-13
Did it break suspend for anyone else?  I have been using the x swat.  Not sure if its this driver or not that broked suspened but monitor no longer turns off, or computer fro that matter.

---

### Post by Linuxforall on 2010-09-13
> **keypox said:**
> Did it break suspend for anyone else?  I have been using the x swat.  Not sure if its this driver or not that broked suspened but monitor no longer turns off, or computer fro that matter.

Try reinstalling the driver, it works fine here on two machines, a dual XEON with nvidia 8400 and a laptop with nvidia graphics.

---

### Post by keypox on 2010-09-14
> **Linuxforall said:**
> Try reinstalling the driver, it works fine here on two machines, a dual XEON with nvidia 8400 and a laptop with nvidia graphics.

Didnt work, any other suggestions. 

Does anyone know of a suspend log or something?  Maybe something else is causing this. Suspend seems to be the bane of linux.

Well I ppa purged x swat.  But still suspend doesnt work.  I figured as much, ubuntu suspends just works for a little while then for some reason stops.  Even fresh installs never seem to fix it... ahhh sucks, i was enjoying it while it lasted.

---

### Post by keypox on 2010-09-14
well i have found the colprut has nothing to do with video and i got x swat back in.  Hopefully the problem fixes its self lol. 

This new driver is faster :)

---

