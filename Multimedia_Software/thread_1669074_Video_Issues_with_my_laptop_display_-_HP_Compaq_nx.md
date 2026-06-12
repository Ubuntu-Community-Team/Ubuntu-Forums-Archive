---
title: "Video Issues with my laptop display - HP Compaq nx9010"
date: 2011-01-17
forum: Multimedia Software
---

### Post by bullmoose81 on 2011-01-17
I have a HP Compaq nx9010 laptop with 1 gig of memory and 128mb being dedicated to video memory.  The graphics chip is ATI Radeon IGP 345M.
I can only set my resolution to 1024 X768.  If I try to change it to any other size or try
to play any games, the video has millions of jerky horizontal lines going through it.
If I hookup an external monitor the video works just fine.  Being new to linux and even
newer to installing on it laptops, can anyone tell me what if any thing can be done to correct this.  I am running Ubuntu 10.4 LTS.
Thanks!

---

### Post by Lukiwuki on 2011-01-17
First I would upgrade to Ubuntu 10.10.
Open a terminal ( Alt + F2 and enter gnome-terminal ) and then insert:

```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

Then reboot!

Second I would install the newest driver version. You can get it via "Restricted Drivers" in your Menue or by downloading it manually at the website of your graphic card producer.
Of course this could work for 10.04 too so if you dont want to upgrade your distribution try it first.

---

