---
title: "Configuring iPod video with Amarok"
date: 2008-11-24
forum: Multimedia Software
---

### Post by BartGunn on 2008-11-24
I much prefer the look and feel of Amarok compared to Rhythmbox which is a bit plain, but I can not get my iPod video to connect. I've been searching the forums and tried mount '/media/disk' instead of '/mnt/ipod' and neither work for me, still getting 'no ipod found' anyone know a solution........driving me mad :mad:!!

PS - How do I get thanks against my name and others? I've replied to people thanking them for their help before, but don't know how to make it official?

---

### Post by poebae on 2008-11-24
> **BartGunn said:**
> I much prefer the look and feel of Amarok compared to Rhythmbox which is a bit plain, but I can not get my iPod video to connect. I've been searching the forums and tried mount '/media/disk' instead of '/mnt/ipod' and neither work for me, still getting 'no ipod found' anyone know a solution........driving me mad :mad:!!

PS - How do I get thanks against my name and others? I've replied to people thanking them for their help before, but don't know how to make it official?
Have you confirmed the directory in which your ipod is mounted? Find that in your /media folder first, and type the correct mount point into Amarok.

Have you tried Autodetecting your device? I don't remember the last time I configured my iPod in Amarok, but as far as I can remember it was a painless process.

Re: thanks - to give thanks, click the gold medal icon on the bottom right of people's posts. If you hover over the button, the hover text should say "Thanks".

---

### Post by Predatorian on 2008-11-25
i am having almost the same problem, i have found where my ipod is mounting, my ipod opens up with rythmbox, gtkpod and hippo managment tool, but i cant add music with those 3 programs. so i wanted to try amarok, i just finally figured out the whole local collection thing with mysql, but now im not getting the ipod. at first it told me that it was locked, so, i renamed the file itunes_lock to NoUse_itunes_lock. k, then it told me:

> No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window

well, too bad im running gnome, i tried that command and i got a bad call error. then, i tried adding the device manually, and then it told me no ipod loaded, when ican just right click on the icon and open the damn thing with rythmnbox. this problem has been bugging the crap out of me for a good month now, and ive been pouring over forums and other peoples ideas, and they are all the same and i get the same problems. is there something else im missing?

---

### Post by BartGunn on 2008-11-25
Well I'm still in exactly the same situation too, also on Gnome. Love the Amarok look and GUI, but need this sorted big time

---

### Post by sanjit on 2008-11-30
> **Predatorian said:**
> i am having almost the same problem, i have found where my ipod is mounting, my ipod opens up with rythmbox, gtkpod and hippo managment tool, but i cant add music with those 3 programs. so i wanted to try amarok, i just finally figured out the whole local collection thing with mysql, but now im not getting the ipod. at first it told me that it was locked, so, i renamed the file itunes_lock to NoUse_itunes_lock. k, then it told me:



well, too bad im running gnome, i tried that command and i got a bad call error. then, i tried adding the device manually, and then it told me no ipod loaded, when ican just right click on the icon and open the damn thing with rythmnbox. this problem has been bugging the crap out of me for a good month now, and ive been pouring over forums and other peoples ideas, and they are all the same and i get the same problems. is there something else im missing?

Are you sure you needed to rename that? When Amarok gave me that message about the lock, it also gave me the option to remove it just by clicking a button. I did, and now I'm enjoying my iPod 6G.

Songbird might work out, if you can't do it with Amarok.

I'm using 8.10 with GNOME and Amarok 1.4.10, by the way.

---

