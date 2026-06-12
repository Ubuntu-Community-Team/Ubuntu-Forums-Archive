---
title: "Dual screen works in gdm, but not after login"
date: 2009-05-15
forum: Multimedia Software
---

### Post by martin_legion on 2009-05-15
Hello. I once booted with the supervideo cable connected to my TV and automatically set the dual screens. Perfect!, but what happened then is that I disconnected the cable, and the resolution in my laptop was changed, and I wanted to go back to the normal resolution, so I go to Screen and change the resolution. I don't remember if the resolution I wanted was listed or not, so I can't say if I changed there or I had to reboot. The thing is that when I did, it said that a Virtual line was to be added to the config file, and I said yes. Big mistake. After that, never again the dual screen worked. I tried booting with the supervideo connected, connecting it after boot, with cloned output, extended desktop, everything.
I removed the lines added to xorg.conf, but nothing happened. Now if I boot with the TV connected, I can perfectly see the login screen, gdm, but as soon as I log with my user, the TV turns black, and that's as far as I can get. :(
How in hell do I make it work again, and if possible not having to reboot each time I connect or disconnect the supervideo cable!
THANK YOU

---

### Post by martin_legion on 2009-05-15
Solved.
first, boot normally, log ing, connect the TV and then:

xrandr --output LVDS --mode 1024x768
xrandr --output TV --mode 1024x768

that clones the output. When I want to go back to single screen and with a better resolution, I do:
xrandr --output TV --off
xrandr --output LVDS --mode 1280x800

I've put both commands on scripts, and then assigned key-bindings, so with a single keystroke I can change the dual screen mode.
Bye!

---

