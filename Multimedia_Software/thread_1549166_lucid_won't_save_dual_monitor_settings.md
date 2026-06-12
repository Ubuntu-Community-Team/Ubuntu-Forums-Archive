---
title: "lucid won't save dual monitor settings"
date: 2010-08-09
forum: Multimedia Software
---

### Post by har23 on 2010-08-09
I'm running kubuntu 10.04.  I have dual monitors (X1300 video card).  I can set the monitors up.  However when I reboot, the settings are not remembered and I end up with one monitor being a clone of the other. 

Searching has turned up a lot of stuff about nvidia drivers, but I'm not using that.  Plus as I said, I can get everything working correctly, I just can't get it to remember the settings.

What am I doing wrong and how do I get the settings to be retained?

Thanks in advance.

---

### Post by har23 on 2010-08-12
The solution was a pretty obscure hack.  

I had to create the file
/etc/X11/Xsession.d/45custom_xrandr

and put the single line ```

xrandr --output DVI-0 --mode 1280x1024 --pos 0x0 --output DVI-1 --mode 1280x1024 --right-of DVI-0

```

---

### Post by cj.surrusco on 2010-08-12
Well, to anybody referring to this thread, there was a much easier way. Instead of opening Nvidia Settings from the menu, you should open it with root privileges using:
```
gksudo nvidia-settings
```
Then you can make your changes, choose to save to the X configuration file, and the settings will stay there when you reboot.

---

### Post by har23 on 2010-08-12
> **cj.surrusco said:**
> Well, to anybody referring to this thread, there was a much easier way. Instead of opening Nvidia Settings from the menu, you should open it with root privileges using:
```
gksudo nvidia-settings
```Then you can make your changes, choose to save to the X configuration file, and the settings will stay there when you reboot.
If I'm using an ATI card instead of an nvidia card, will this still work?  nvidia-settings isn't installed for me and nvidia-detector returns "none"

---

### Post by cj.surrusco on 2010-08-12
> **har23 said:**
> If I'm using an ATI card instead of an nvidia card, will this still work?  nvidia-settings isn't installed for me and nvidia-detector returns "none"

That's what I get for skimming the first post ;). Sorry, I just saw the word Nvidia in the first post and figured you had the name problem that I did with my Nvidia card. But it might work for the ATI card, anyway.

---

### Post by realzippy on 2010-08-12
Nah,why should nvidia-settings work for ATI?

---

### Post by cj.surrusco on 2010-08-12
I'm talking about a similar solution, such as running the ATI settings manager with sudo privileges, not the same exact solution, of course.

---

