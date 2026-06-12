---
title: "From ATI to nVidia"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by flummoxed on 2006-11-15
I'm probably going to get my friend's evga 6600gt sometime within the next few days for really cheap, so I'm going to replace my 9800 pro in this system. I already have kubuntu 6.10 installed. What would be the best way to switch the drivers around? I didn't install the proprietary fglrx drivers. I'm using the ati ones in xorg.conf. What should I change in the xorg.conf file so that I'm using the nvidia default drivers so after I reboot and put in the new card I can start up X?

---

### Post by dutchmega on 2006-11-15
If you didn't install any fglrx drivers, you can just install the nvidia drivers.

sudo apt-get install nvidia-glx

Also, change "ati" to "nvidia" under Device in /etc/X11/xorg.conf

---

### Post by earobinson on 2006-11-15
you should just be able to install the nvidia drivers "over top" of the ati ones. I was able to go nvidia to ati by doing this :)

---

### Post by Chippendale on 2006-11-15
I also have ATI drivers which i Installed and configured. I'm using the same card 9800 Pro however, I will be switching to an Nvidia card on the weekend. How would i go about it? Any ideas or suggestions? if not, I'll just figure it out =) thanks!

---

### Post by earobinson on 2006-11-16
> **earobinson said:**
> you should just be able to install the nvidia drivers "over top" of the ati ones. I was able to go nvidia to ati by doing this :)
Chances are just installing the nvidia drivers as if you never installed the ati ones should work :)

---

### Post by Chippendale on 2006-11-16
thanks for the reply..I'll try that and see what happens :)

---

### Post by earobinson on 2006-11-16
np, let us know how it works and if everything went fine mark the thread as resolved :)

---

### Post by Nythain on 2006-11-18
So i stumbled upon this thread while researching the process because im switching over also. After reading that it should be as simple as just installing the nvidia over/on top of the ati i loaded up adept (yeah i know, ick, buggy, lame, whatever) filtered nvidia, requested install on everythign that applied, previewed changed and realised that adept is at least smart enough to automatically remove all my fglrx packages in the process... so im not really installing over/on top of... wich eases my mind a bit, hopefully it will ease anyone elses too :)

---

### Post by tseliot on 2006-11-18
> **Chippendale said:**
> I also have ATI drivers which i Installed and configured. I'm using the same card 9800 Pro however, I will be switching to an Nvidia card on the weekend. How would i go about it? Any ideas or suggestions? if not, I'll just figure it out =) thanks!

There's no problem if you use the "ati" (opensource driver).

If you're using the "fglrx" driver (the ati proprietary driver) you will need to uninstall it before installing the nvidia driver.

---

### Post by Chippendale on 2006-11-19
what was suppose to be a video card upgrade became a whole system upgrade =)   so that's my little adventure, i reinstalled windows and edgy

---

