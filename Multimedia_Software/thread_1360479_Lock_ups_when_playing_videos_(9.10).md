---
title: "Lock ups when playing videos (9.10)"
date: 2009-12-20
forum: Multimedia Software
---

### Post by G00D_GUY on 2009-12-20
My system locks up when playing videos on Youtube (or any place else), Hulu application, or when playing any games (except solitaire). 

This problem started after upgrading to 9.04, and continued till now with 9.10. I even reformated and installed a fresh 9.10, but still it continues. 

I have a 6600GT AGP and have tried all of the drivers. Also, I am duel booting with XP and play CCS and COD4 with out any problems. When in locks up the screen freezes up, and the music or sound will continue for a couple of seconds and then it is just frozen. The only thing I can do is reboot.

If someone can just point me in the right direction, it would be appreciated.

---

### Post by lovinglinux on 2009-12-21
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by G00D_GUY on 2009-12-21
I don't know if this is the answer yet, but it has already improved my CPU usage. I had no idea that I was using about 98% of my CPU while watching youtube vids. I loaded a downloaded youtube vid up in movie player, and only used 30% just like the it said. Strange.

Thanks for the info. I will work on it.

---

### Post by lovinglinux on 2009-12-21
> **G00D_GUY said:**
> I don't know if this is the answer yet, but it has already improved my CPU usage. I had no idea that I was using about 98% of my CPU while watching youtube vids. I loaded a downloaded youtube vid up in movie player, and only used 30% just like the it said. Strange.

Thanks for the info. I will work on it.

There are several things there, not exactly related to flash, but that will help improve your Firefox experience.

Flash uses a lot of CPU cycles, but your CPU usage is still high, even with mplayer, which should be just about 10% or less. What CPU do you have?

Check if you have "Remote Desktop" enabled and disabled it. Go to "System >> Preferences >> Startup Applications (aka Sessions)" to do that. Also see **Solution** [*[COLOR="Red"]**FOT010**[/COLOR]*] and disable Java (not javascript) in the browser preferences.

---

### Post by G00D_GUY on 2009-12-21
I did a lot of the Firefox optimisation steps, and decided to roll back the driver to 173, and this brought the CPU usage down to 60% max. I have an AMD Athlon 2800, and this seems good now. No lock ups so far.

I have my fingers crossed, but I think this is it.

Thanks so much.

---

