---
title: "Can't seem to lock alsamixer input source"
date: 2008-12-20
forum: Multimedia Software
---

### Post by martmonkey on 2008-12-20
I am trying to lock the alsamixer input source to mic but it is just not having. Alsamixer input source changing by itself while on skype or even just by itself. 

I thought saving alsamixer settings should lock the input source but nope it has to change itself to cd  by itself later on. This happens just after 5 or 10 minutes after i save the settings.

I just can't bare it anymore. 
I am about to mount /hand/coffeecup /to/mymonitor

Please helpppp !!!!

---

### Post by peyu on 2010-01-11
Hello martmonkey,
same problem here... I changed the input sound level with alsamixer and also the input source. The level doesn't change, but every reboot I have to set the input source to internal microphone (by default it puts microphone, which is the plug for an external microphone on my laptop).
If somebody can help, thanks !

---

### Post by Fernando Negro on 2010-03-08
I you have installed it, try uninstalling the "pulse" audio system.

I have just finished configuring Xubuntu 9.10 on a laptop and was also having the problem of alsamixer apparently not saving the input source. I would change it to "Front Mic", save the configuration by executing "alsactl store" as root, and every time I rebooted there it was back again as "Mic" instead of "Front Mic".

I found out it was apparently because I had installed the "pulse" audio system.

Wanting a sound recording program, I had installed the "gnome-media" package with which the "pulse" audio system was also installed.

I could see that changing the volume settings with the "pulse" volume control would affect the alsamixer settings as well, so I suspected "pulse" might be screwing with alsamixer's microphone settings on it's own.

(Maybe "pulse", for some reason, would automatically change the input source on every reboot.)

I uninstalled the "pulseaudio" package along with three others starting with the same name, rebooted the computer, changed the alsamixer settings to what I wanted again, saved the settings with the "alsactl store" command as root, rebooted the computer, and now the input source remains unaltered as "Front Mic" every time I reboot.

---

