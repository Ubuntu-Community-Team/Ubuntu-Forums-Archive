---
title: "Nvidia video stutter since latest update"
date: 2010-04-02
forum: Multimedia Software
---

### Post by Wobbo on 2010-04-02
Hello,

Since the latest update of Ubuntu Karmic I found a stutter on my screen. It occurs when i just move my mouse over my desktop (when not asking much of CPU or videocard) and it occurs when I play videogames as World of Warcraft (when asking alot from CPU and videocard). It's always there and it makes it impossible for me to do my work (with 3d rendering and audio) on my pc. The stutter seems to have a steady rythm.

When i disable Nvidia drivers the stutter is gone. I have two Nvidia videocards in my pc. I need them to work to be able to work on my pc. I tried using older drivers for Nvidia, but the stutter remains. Disabling desktop effects didnt help either.

I got one harddisk with Windows on it, it also uses the videocards and when i boot up on windows there is no stutter. So it seems to me to be a software issue from Ubuntu.

My system worked fine for a long time on Karmic. Never had this problem before.
I hope one of you has the solution for me!

Greetings,

Ernst Wobbo

---

### Post by Linuxforall on 2010-04-02
How bout trying latest nvidia drivers from nvidia site, they are version 195.36.15. Make sure to do a sudo apt-get --purge nvida before you install this. You also need to install build-essential 

I have been running this driver on a cheap nvidia 8400 and get full screen VDPAU on mplayer with hd movies.

---

### Post by Wobbo on 2010-04-02
I all ready just 195.36.15, stil the same problem.

---

### Post by canuckistani on 2010-04-02
I have the same problem, I'm running XBMC on Jaunty and now the display is corrupted and jumpy. lspci tells me:

VGA compatible controller: nVidia Corporation GT200 [GeForce GT 220] (rev a2) and I'de installed the latest drivers. Everything has been working great until the other day.

---

### Post by canuckistani on 2010-04-02
I see from my aptitude log that I updated the kernel *and* xorg on March 18. I'm going to re-install the NVIDIA driver to see if there is some odd mis-match, will report back as events warrant.

---

### Post by canuckistani on 2010-04-02
I just installed :

```
NVIDIA-Linux-x86_64-195.36.15-pkg2.run
```

The recent packages I installed that I mentioned were:

```
[UPGRADE] linux-image-2.6.31-20-generic 2.6.31-20.57 -> 2.6.31-20.58
[UPGRADE] xserver-common 2:1.6.4-2ubuntu4.1 -> 2:1.6.4-2ubuntu4.2
[UPGRADE] xserver-xorg-core 2:1.6.4-2ubuntu4.1 -> 2:1.6.4-2ubuntu4.2
```

---

### Post by Wobbo on 2010-04-03
> **canuckistani said:**
> I just installed :

```
NVIDIA-Linux-x86_64-195.36.15-pkg2.run
```The recent packages I installed that I mentioned were:

```
[UPGRADE] linux-image-2.6.31-20-generic 2.6.31-20.57 -> 2.6.31-20.58
[UPGRADE] xserver-common 2:1.6.4-2ubuntu4.1 -> 2:1.6.4-2ubuntu4.2
[UPGRADE] xserver-xorg-core 2:1.6.4-2ubuntu4.1 -> 2:1.6.4-2ubuntu4.2
```

And dit it work? What was the effect?

---

### Post by lidex on 2010-04-03
Did you un-install old drivers first? After install run:
```
sudo nvidia-xconfig
``` and reboot. Then go to Jockey (Hardware Drivers) and enable. Reboot again.

---

### Post by canuckistani on 2010-04-06
> **Wobbo said:**
> And dit it work? What was the effect?

Sorry, should have been clearer. It didn't change anything. I'll try un-installing the driver and cleaning things up and then re-installing to see if that improves it. It's more obnoxious in the XBMC menus than watching video ( this is my HTPC machine )

---

### Post by Wobbo on 2010-04-11
There was a update for the "nvidia-settings," now the problem is solved. Thanks all.

---

