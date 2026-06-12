---
title: "totem won't let the computer go into sleep mode after movie finishes"
date: 2010-12-16
forum: Multimedia Software
---

### Post by soad6 on 2010-12-16
Hi, I think i may of previously listed that this was solved, but its not so i'm making this a new thread also this is also a new thread because there was something i forgot to mention. 
Ok so my problem is that after totem is done playing a movie from my external harddrive ( usb 2.0 750 gb Western Digital HDD) the computer screen will go blank but the computer will not suspend or hibernate. I have gnome-power-manager to go to suspend after 30 min of inactivity. I will usually fall asleep during the movie and the laptop will remain on. I will wake up to find the laptop on for the whole night and that it didn't go to sleep or suspend power after the movie stopped. Any ideas?? 
Note ** I have already tried reinstalling gnome-power-manager & totem ...
Also have turned on and off Dbus plugin, and totem is not set to always on top. Thanx for any help in advance. Its ubuntu 10.10 if that helps.

---

### Post by siam.a on 2010-12-22
I am having this issue as well.
I have also tried a re-install of gnome-power-manager.
I am also observing that that this occurs when totem is left open not necessarily only when it finished playing a movie.

Anybody have any ideas?

---

### Post by soad6 on 2011-01-19
I have wrote a bash script and c wrapper to go with it. place the c wrapper in /usr/bin and run the totem.sh script. This will make the computer shutdown after 2 hours of movie playback.

---

