---
title: "banshee media player is quiet"
date: 2009-08-24
forum: Multimedia Software
---

### Post by jomex on 2009-08-24
how do i get the volume back to normal?
volume bar in player and Ubuntu is up to max
in other players the actual volume is loud

---

### Post by x33a on 2009-08-24
is it showing any errors?

maybe some plugin is missing.

try starting it from the terminal and look for any errors.

---

### Post by jomex on 2009-08-25
no errors

> [Info  13:30:39.628] Running Banshee 1.4.3: [Ubuntu jaunty (development branch) (linux-gnu, x86_64) @ 2009-03-22 17:00:13 UTC]
[Info  13:30:45.950] All services are started 5.123852s
[Info  13:30:47.617] nereid Client Started
[Info  13:30:49.719] Sync calculated for Music Library: to add: 899 items, remove 0 items; sync_src.cacheid = 82, to_add.cacheid = 90, to_remove.cacheid = 98
Sync calculated for Video Library: to add: 0 items, remove 0 items; sync_src.cacheid = 100, to_add.cacheid = 102, to_remove.cacheid = 110
Sync calculated for Podcasts: to add: 0 items, remove 0 items; sync_src.cacheid = 114, to_add.cacheid = 118, to_remove.cacheid = 126


which plugin could possibly be missing concerning such an essential feature as volume? :)

---

### Post by x33a on 2009-08-25
have you got gstreamer plugins installed. 

take a look at these dependencies, and install the one (if any) missing.

[http://packages.ubuntu.com/jaunty/banshee](http://packages.ubuntu.com/jaunty/banshee)

---

### Post by jomex on 2009-08-25
shouldn't apt take care of this, if i do:

apt-get remove banshee
apt-get install banshee

still quiet

---

### Post by x33a on 2009-08-25
well actually, i am not using ubuntu these days (arch), and i have never used banshee, though i agree that apt-get shouldn't miss important dependencies.

try purge removing it, and then, try installing banshee along with all recommended packages, through synaptic.

```
sudo apt-get remove --purge banshee
```

---

### Post by peepingtom on 2009-08-26
Hi,

It's only banshee that's quiet and not everything else, right? Do you have some sort of "audio normalisation" option set in banshee? If you want to wipe out the banshee settings, open a terminal and ```
rm -rf ~/.config/banshee
```. 

If this doesnt fix it I bet you have some extra pulseaudio volume controls installed, they'll be on the Applications -> audio & video menu.
To wipe out per-user pulseaudio settings: ```
rm -rf ~/.pulse
```
If you make another user account and the problem persists there, this issue might be complicated.

---

### Post by jomex on 2009-08-26
found it, the PCM volume (?) was down!

thanks anyway :)

---

