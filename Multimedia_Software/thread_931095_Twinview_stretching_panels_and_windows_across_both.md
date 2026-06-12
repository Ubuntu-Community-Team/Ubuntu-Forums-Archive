---
title: "Twinview stretching panels and windows across both screens, not acting like it should"
date: 2008-09-26
forum: Multimedia Software
---

### Post by Kuroyume on 2008-09-26
I recently installed 8.04.1, and trying to use Twinview from my 7300GT, i've noticed it isn't working like it used to (i change OSes every once in a while). It used to think of both screens as separate entities, with panels and maximized windows being confined to one screen or the other. (It even works like this on the Intrepid Alpha, which i was testing before going back to Hardy).

Instead, now it's treating both screens as one, stretching the panels and maximized windows between the two. Is this a specific issue with the driver version used on Hardy or something like that? or do i have a bad install?

---

### Post by SuperSonic4 on 2008-09-26
TwinView stretches your desktop across all available screens by default.

If you want your monitors to act as separate windows set them as separate X screens. This can be done by pressing alt+f2 and typing ```
gksudo nvidia-settings
``` or,for the small chance that you don't have nvidia-settings: ```
sudo apt-get install nvidia-settings
```.

After that you can set them as separate X screens and because you're root you can save it to Xorg and restart X. With separate X screens you will need to open an application in one or the other (you can't drag an app over) but you can drag files over.

I use it to play US DVDs on my tv as though I used my own dvd player :p

---

### Post by Kuroyume on 2008-09-26
it's not working as usual... the whole point of using twin view is supposed to be that both screens are semi independent, but you can drag stuff between them... but now even the login screen spans both screens, with the text box right in the middle, which it certainly didn't do in 7.10, and it doesn't do in 8.10.

---

### Post by overdrank on 2008-09-26
> **Kuroyume said:**
> it's not working as usual... the whole point of using twin view is supposed to be that both screens are semi independent, but you can drag stuff between them... but now even the login screen spans both screens, with the text box right in the middle, which it certainly didn't do in 7.10, and it doesn't do in 8.10.

HI and have you tried to change your panels to just one screen. I have setup a dual monitor system with Hardy that way. But not in intrepid yet.

---

### Post by geogur on 2008-09-26
yess i have tried for i am having the same problem with my 2 head display ubuntu 7 has the code to allow this  ubuntu 8 dose not want to do this

---

