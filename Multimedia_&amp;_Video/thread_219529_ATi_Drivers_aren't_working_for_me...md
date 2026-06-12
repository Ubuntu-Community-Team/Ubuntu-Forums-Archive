---
title: "ATi Drivers aren't working for me.."
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by Cyclohexane on 2006-07-20
Hey guys.. 

Just like the title says, my ATi fglrx drivers aren't working. Every time I try a new guide, reinstall, or even install a clean ubuntu, fglrxinfo still gives me a prompt telling me the Mesa drivers are still in.. 

I think I might have isolated the problem this time, though.. 

When I was messing with my xorg.conf, I did something wrong, apparently, and the xserver wouldn't load.. So I logged in and typed:```
sudo dpkg-reconfigure xserver-xorg fglrx
```It gave me the normal menu (as if I hadn't typed fglrx), and when I got through it, it gave prompt telling me it didn't recognize the command fglrx.. It said the package wasn't installed.. So I tried ```
sudo apt-get install xorg-driver-fglrx
``` and that said it WAS installed.. That makes me think it was only a bad command, but I don't know for sure.. 

By the way, I have a Radeon 9800 Pro.. 

I've tried numerous guides on these forums, the Ubuntu Documentation guide, the Ubuntu ATi Wiki guide, and the guide on the ATi site.. Nothing seems to work at all.. I would bet money that I am inputting the commands correctly.. 

Please help, thanks..

PS: and here is my xorg.conf

---

### Post by matthew on 2006-07-20
What happens when you just use this?
```
sudo dpkg-reconfigure xserver-xorg
```If that gets you to a series of menus/questions, then just choose the defaults for everything except when it asks which driver you want to use. Scroll down the list and choose "fglrx." After the command has completed and returned you to a prompt, reboot.

EDIT: your xorg.conf file looks fine. I think running the command above and following through with a reboot ***should*** take care of your problem.

---

### Post by Cyclohexane on 2006-07-20
Yeah.. I know that command.. When I did that command with fglrx added at the end, it went through that process.. I've tried that numerous times, too.. No luck..

---

### Post by Cyclohexane on 2006-07-20
I've tried almost everything there is.. For some reason, the ATi drivers aren't installing over the Mesa drivers.. Do you think it's just a problem with the 9800 Pro?

---

### Post by mister_eko on 2006-07-20
I might be able to help but, not tonight I need to get some sleep before I fall asleep in this chair. Which versions of the ATI drivers have you tried?

I'll try to give you an answer by tomorrow if you haven't solved it yet. Cool?

---

### Post by gruvsyco on 2006-07-20
on my system, the only thing I did to configure X was, after I installed the fglrx driver from the Ubuntu Dapper repos, from a terminal do:

```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```

Radeon 9600 here.

no compiling or anything.

---

### Post by Cyclohexane on 2006-07-21
I tried that, too.. I tried installing the newest one, and the one before that.. Both failed to work..

---

### Post by mister_eko on 2006-07-21
Hi

I had similar problems with my X1600 and I had some other issues too. After numerous re-installs, many different guides and making sure, just as you are doing, that the commands I was giving were character correct I got my driver working properly.

Anyway this is what I did, I got the system to use the vesa driver.    After rebooting I killed X and worked in the command line. I followed this guide [Howto: Fglrx 8.26.18 Driver Install (works With Xpress Series Cards Now!)]("http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+mesa+install") and it worked.

Somewhere on the net I read this guy removed the mesa driver from his system in order to get his ATI card to work with the new driver.

I hope this helps you.

---

### Post by Cyclohexane on 2006-07-21
I'll check that out.. Can anyone tell me how I would remove my Mesa drivers manually?

---

### Post by dillanlaughlin on 2006-07-23
Similar problem here trying to get the ATI drivers working on an Asus Barebones kit. I have tried following all of the install methods mentioned on this thread without any luck. My system is using ATI's Xpress 200 and the 8.26.18 driver.

---

### Post by Cyclohexane on 2006-07-23
Alright.. I was just reinstalling Ubuntu on a friend's computer for him, and for the hell of it, I tried installing the drivers.. He has a Radeon 9600 SE in there.. And, it worked on the first try..

---

### Post by dillanlaughlin on 2006-07-23
What the heck? That's incredible. I have been working at this for 4 days now trying everything that I see on different websites. I really want to get this going but it's really kicking me in the butt.

Congradulations to all of those who have gotten it sucessfully installed!

---

### Post by Seamus on 2006-07-23
I also am trying to get this going, but with joy. I did a Xorg reconfig, chose the fglrx drivers and rebooted.

Still I get this:

> $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


I have a 9250

> $ lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)



I desperately want to get dualhead monitor working...

---

