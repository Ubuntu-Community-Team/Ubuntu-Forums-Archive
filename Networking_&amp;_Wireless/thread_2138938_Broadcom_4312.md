---
title: "Broadcom 4312"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by Karasawa7 on 2013-04-25
Ok. Windows 8, sucked.
Got Ubuntu 13.04.
My wireless card is Broadcom4312.
My system is a 64 bi system.
I've tried other threads, and other sites, but everytime I put anything into the command, I either get nothing, or a random program. (For example, the code 'lspci' brings up my brightness settings....not wireless settings)

I'm literally confused. 
Can I get some help? I just want to get my wireless running.

---

### Post by kdawg3 on 2013-04-25
Use the gui for networking in the bottom right-hand corner. Should be simple point and click, enter your access settings and you will be good to go just like before windows 8.

---

### Post by Impavidus on 2013-04-25
You may be confusing terminal commands with searches in the dash.

First try: get a wired internet connection, open the dash and search for "additional hardware". I think it's called like that, but I don't run your version, so I can't be sure. See if any broadcom drivers are mentioned there and install one.

---

### Post by Karasawa7 on 2013-04-25
Er, I'm running 13.04. There's literally nothing in the bottom right corner, and I'm probably mixing the two up. Yaknow, I'm a Computer Science major and all, I feel like this should come easy to me. I'm just VERY (like, been working with this for a couple house) new to this interface.

---

### Post by Feathers McGraw on 2013-04-25
I think kdawg3 meant top right.

I take it you've tried clicking on the wireless symbol (desktop, top right...), entering your wifi password etc... so if that's not working, try:

1. Connect to wired connection temporarily
2. Click the ubuntu logo in the top left to open the dash
3. Search "software"
4. Click software and updates
5. Click on the "Additional Drivers" tab
6. Select the proprietary driver and apply changes to download and install it.
7. Afterwards, unplug the ethernet cable and reboot.


Some drivers don't work with certain routers. you can always revert to the older driver if you fancy.

Feathers

---

### Post by Feathers McGraw on 2013-04-25
Also, if you have a problem with the interface you can always try another distribution, e.g. [Kubuntu](http://www.kubuntu.org), which has a more traditional desktop layout... 

It's the best thing about Linux imho, there are so many choices that there's something for everyone. Plus, you don't need to install to try each distribution, you can run it from a disk to get a feel for it.

The choice is yours :)

---

### Post by Karasawa7 on 2013-04-25
Haha! Wonderful! That worked perfectly! Now the menu popping up for all detected wifi signals are in and I can connect! Worked like a champ! Thanks! Hopefully all the people I've seen with this problem stumble here.

---

### Post by Kopkins on 2013-04-25
To help people find your solution, please mark your thread as solved by editing your first post and changing the prefix from [Ubuntu] to [Solved]

And welcome to Linux!

---

### Post by Feathers McGraw on 2013-04-25
> **Karasawa7 said:**
> Haha! Wonderful! That worked perfectly! Now the menu popping up for all detected wifi signals are in and I can connect! Worked like a champ! Thanks! Hopefully all the people I've seen with this problem stumble here.


Ha, glad to be of assistance :) such a small thing, but a show stopper when it doesn't work.

Seriously though, "standard" ubuntu with the unity desktop is geared towards being the same, and therefore familiar and easy to use, on all devices (tablets, desktop, phones etc.). Consequently, a lot of things on it seem like they're in strange places for a PC desktop... but are in a sensible place on a touchscreen. Have a think about it as you use it and you'll see what I mean.

Feathers

---

