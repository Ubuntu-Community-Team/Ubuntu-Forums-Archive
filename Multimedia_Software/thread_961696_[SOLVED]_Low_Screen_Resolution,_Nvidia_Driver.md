---
title: "[SOLVED] Low Screen Resolution, Nvidia Driver?"
date: 2008-10-28
forum: Multimedia Software
---

### Post by Life.exe on 2008-10-28
I just previously finished installing Ubuntu. Knowing that I would also have to install a driver for my graphics card I followed the guide ([http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)) however after I re-booted my computer it did not seem any changes took place. My screen resolution was still very low, (640x480), so I decided to see if I could change it, I could not :(. Even though the "Hardware Drivers" under System->Administration says that my graphics card is enabled it dose not seem like it is functioning properly. I could be wrong, but then how come I can't change my screen resolution? Is my driver installed properly?

My graphics card is:

GeForce 6800 GT 256MB

I am very worried I hope that this issue can be solved because I would really like to use Ubuntu, Linux.

---

### Post by Chris Lopez on 2008-10-28
I've been having the same problem with two sli'd 6600's. I'm running 8.04 64bit version of Ubuntu. 

*Ps: I'm a linux n00b so please could you respond in n00bish.* :)

---

### Post by Life.exe on 2008-10-28
I have been doing some further research on others with this problem and I stumbled across this after searching through almost 50+ forms.


 Re: Post the way you got the Nvidia driver to work
0000:05:00.0 0300: 10de:00c3 (rev a2)
nVidia Geforce 6800GT (Asus PCI Express x16)
tweak - edited xorg.conf to include 1280x768 @60Hz for my 32" Viewsonic N3200W LCDTV (native res is 1366x768 - haven't tried that yet though - afraid! (edit: I actually read my manual and the max input resolution is in fact 1280x768 @ 60hz - it looks good so I'm happy.)

downloaded required packages using Synaptic and rebooted. All is well running 6.06.1 LTS Dapper Drake.

This is my first Linux distro and other than a slight leanring curve and LOTS of reading and searching How Tos to get everything to work right, I'm a very happy newcomer. These forums are priceless. Thanx to all here that are dedicated to making Linux a viable option to Windows. I plan on sticking around to learn and hopefully contribute! First post too BTW -
Last edited by ridgeone; February 27th, 2007 at 08:58 AM.

The thing is I have no idea what he has done to get his graphics card working. Could someone please explain? Would this work for me?

---

### Post by Life.exe on 2008-10-29
*Bump*

I know it has not been a day since I made this post, but i really need this issue solved. If someone could at least point me in the right direction or give me some assistance i would really appreciate the help!

---

### Post by xc3RnbFO8P on 2008-10-29
In Terminal:
> gksu displayconfig-gtk
see if your monitor is supported,
if not choose Generic
and resolution that your monitor supports.

---

### Post by Chris Lopez on 2008-10-29
> **Ringi said:**
> In Terminal:

see if your monitor is supported,
if not choose Generic
and resolution that your monitor supports.

You rock! Works like a charm. Never thought that I would have to configure the monitor drivers as never had to on windows. I bet this would solve a lot of newbies NVIDIA driver problems.

Thanks very much!

---

### Post by Jim Lewis on 2008-10-29
I'm coming in late here, but I have the same problem.  I went to the terminal and typed the command and I got:

jim@jim-desktop:~$ gksu displayconfig-gtk
jim@jim-desktop:~$ 

That tells ME nothing.  How might I set my terminal to "generic"?  I can find nothing  in System Preferences or Administration that lets me set that.

---

### Post by xc3RnbFO8P on 2008-10-29
What did you install, Intrepid Ibex or Hardy Heron?

---

### Post by Jim Lewis on 2008-10-29
Afraid I had an old 7.04 version.  I'd used it in a dual-boot system, also and had a 1200x??? setup then.

---

### Post by avibp on 2009-01-01
> **Ringi said:**
> What did you install, Intrepid Ibex or Hardy Heron?

I am having the low screen res issue with my Intrepid Ibex install using a Nvidia GeForce FX 5200.

After typing ```
gksu displayconfig-gtk 
``` and entering the password, I am left back at the blinking cursor as well.

SYSTEM-> ADMINISTRATION-> NVIDIA X-server settings 
X-Server Display Configuration
Display - Model "CRT-0 (CRT-0 on GPU-0)"     [SIZE="4"]<-=== WRONG === <[/SIZE]-

I am using an MAG 32" LCD (I'd find the model but dont think it matters at this juncture)

Any help would be appreciated.

---

### Post by Sofa_King_Cool79 on 2009-01-06
*Bump* I too am having the same problem
I have an 18 in LCD made by NEC
I tried this command:

gksu displayconfig-gtk

I enter the password and it returned nothing. my res is stuck at 640X480

---

### Post by msboston01 on 2010-09-24
Same issue here. When I run 

```
gksu displayconfig-gtk
```

I see a window labeled "starting administrative task" which disappears. Nothing happened.

Any help around that?

---

### Post by lkjoel on 2010-09-24
> **msboston01 said:**
> Same issue here. When I run 

```
gksu displayconfig-gtk
```

I see a window labeled "starting administrative task" which disappears. Nothing happened.

Any help around that?
Instead of "gksu", use "sudo".
To the OP, go to Thread Tools->Mark this thread as solved.

---

### Post by overdrank on 2010-09-24
> **msboston01 said:**
> Same issue here. When I run 

```
gksu displayconfig-gtk
```

I see a window labeled "starting administrative task" which disappears. Nothing happened.

Any help around that?

Hi and when this thread was started in 2008 the command was a useful tool. :)
Thread closed.

---

