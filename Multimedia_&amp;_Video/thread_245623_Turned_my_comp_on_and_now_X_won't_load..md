---
title: "Turned my comp on and now X won't load."
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by Jolly Roger on 2006-08-28
The other day I turned on my computer and for whatever odd reason the X server won't load anymore. I hadn't done anything to it as far as I knew. When X is trying to load after the splash screen I get a BSOD and get dumped to the command line. I have my error log and the only errors I find in it are:

(EE) fglrx(0): DRIScreenInit failed!

I have no idea how to fix that. I'm running a x850xt PE card with the 8.27.10 drivers. I've tried reinstalling drivers already and that didn't work. 

I have the rest of my error log attached in case anyone wants to look at it.

---

### Post by tseliot on 2006-08-28
First of all upgrade the system:
```
sudo aptitude update && sudo aptitude dist-upgrade
```

Then type:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "ati" driver. Press ENTER whenever you don't know the answer to a question.

then:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

if that doesn't work try with "vesa" instead of "ati"

---

### Post by Jolly Roger on 2006-08-28
I tried your solution and when I select ati it doesn't work. But when I select vesa it worked. But then I tried to install the ati drivers and after it was completed I got a black screen once Ubuntu finished loading up. I used the same method to install the ati drivers as I have in the past and this has never happened.

---

