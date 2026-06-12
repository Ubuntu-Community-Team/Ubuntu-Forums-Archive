---
title: "Unintelligible screen corruption"
date: 2008-10-08
forum: Multimedia Software
---

### Post by ph1 on 2008-10-08
Hi all,

I've been having a problem recently where my screen goes all wonky; it's difficult to describe, but it becomes covered in fine lines that shimmer or skate across the screen and allow some partial hues of the screen beneath through (e.g. if my desktop background is green, the lines are greenish).  This happens randomly after any period of use--sometimes I'll use the system for hours, leave it on overnight, and then the next morning after 20 minutes it will happen; other times it will happen after a mere 15 from boot time.  When it happens, the system is still responsive--Ctl+Alt+F1 takes me to a text only terminal, and then I can log in and sudo reboot (all without being to read, of course, just guessing what the next step might be).  When the computer reboots, the screen is fine.

My system has an Nvidia GeForce Go 7950 GTX, and I'm dual booting with Windows Vista (where this weirdness never happens).  I'm using Hardy and the most recent Nvidia driver available (I think 177.xx...), and I've run Ubuntu with this problem occurring rarely and spontaneously for about a year, though it's become so often recently that I can't physically use Ubuntu to get anything done (right now I'm trapped in horrid horrid Vista).  

I suspected heat, but the thing is, my laptop runs _cooler_ under Ubuntu than it does in Windows (at least as far as I can tell), and I use i8k to make sure that my GPU temperature never gets above 65 C or so (nice and cool for a GPU) according to the nvidia-settings temperature sensor.  Thus I'd like to hear if anyone else has any suggestions about what it might be, or what I could do to fix it.

Many thanks in advance to this awesome community.

---

### Post by fearful on 2008-10-08
I would suggest that you would re-install your media graphics driver firstly. You might have mis intentionally modified a config file while installing something. Check your logs also they are found in '/var/log' directory. Post your results, good luck

---

### Post by hulleye on 2008-10-24
My machine seems to be displaying exactly the same symptoms. Though I am running Xubuntu 8.10 on a Pentium 3 with an Intel graphics card (not too sure how to check on the command line).

The screen corruption starts slowly, usually instigated by launching Firefox, and continues to spread throughout the xfce environment. Affects text, menus, panels, sidebars, buttons, everything.

I found this problem started once i upgraded to the 8.10 beta. Everything worked fine under Xubuntu 8.04.

not too sure how to go about reinstalling graphics media. But willing to follow instructions if anyone can help.

thanks

---

### Post by Coreigh on 2008-10-24
Make sure it is not over-heating. Carefully clean out any dust deposits from the inside of the case, clear any heat-sinks, especially on the graphics card. Make sure all the fans are operating properly and that any vents are not blocked.

---

### Post by hulleye on 2008-10-25
Does not seem to be overheating. The machine is a Dell Latitude X200. And though its a little warm at the bottom, nothing alarming to indicate that it might be overheating. Although admittedly, it's also not very easy for me to get to the insides to check whether the graphics card heatsinks are dust-free or not.

---

### Post by ph1 on 2008-10-25
My computer doesn't seem to be overheating either.  I overheated it once in Wintendows playing Half-life 2 on 1920x1200 resolution, but it never gets about ~65 C in Linux.  However, when it does run cooler--at about 58--it's better.

I also rolled back the video driver from 177.xx--I think I'm using 171.xx now--and the screen corruption hasn't occurred since, even when I've left the system on overnight and such.

---

### Post by ph1 on 2008-11-07
So for a while, I've thought that this was a heat-related problem, but I've started to think differently.

The thing is, when I use the 177 driver, my screen goes all wonky after 30 minutes or so, no matter the temperature of the GPU--I'm even using i8k and nvidia-settings to keep track of it and attempt to keep it cool, below 60 degrees, which should be more than acceptable for a GPU with 512 MB of onboard memory.  So it's possible that my GPU is little by little frying itself, but it seems highly unlikely, given that these spasms have been occurring for something like 8 months now, that it wouldn't have fried itself already over that period of time.  Also, though the GPU tends to heat up significantly while I'm gaming in Windows, it has yet to "spasm" except in Linux.

It also seems strange to me that the frequency of these "spasms" changes based on which driver I'm using--for example, the 177.80 driver seems to cause a lot of total corruption incidences, but the 173 driver seems to cause fewer.

I suspect that there's something at work here in the kernel interface or in the driver itself, as killing X and restarting via a text-only terminal doesn't do anything to help.  Does anyone who's experienced this or has at least seen reports of it have any clues that could point me toward a solution, or at least a bug report?

Thanks in advance.

---

