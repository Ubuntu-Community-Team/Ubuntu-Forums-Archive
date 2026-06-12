---
title: "onboard sound problems"
date: 2009-04-19
forum: Multimedia Software
---

### Post by EnioG on 2009-04-19
Hey everyone!!

I really need some help here!!!! Im a new bee in linux!!

Im running linux mint on my toshiba a60, every thing was fine apart from the sound stopping after a couple of minutes. I was trying to get it fixed and some how screwed up my system so much that my soundcard isnt recognised. 

I've tried so many different things which i found on google and in this forum but nothing seems to work!!!!!!

I've tried reinstalling a new alsa kernal with the instructions found on this link "http://ubuntuforums.org/showthread.php?t=205449" but to no avail!!! when i tried using module-assistant it failed and then i tried 

cd /usr/src sudo tar xjvf alsa-driver.tar.bz2 cd modules/alsa-driver
and
sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes 
sudo make  
sudo make install

I changed the driver to atiixp which is the one i need (i think) but it comes up with 

 sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards= <atiixp> --with-oss=yes sudo make
bash: atiixp: No such file or directory

Pls help!!

---

### Post by EnioG on 2009-04-20
I eventually regained sound by installing alsa 1.0.19. But!!!! my sound still stops after afew seconds or minutes.....

One more thing, I was told that ubuntu had the best support but it doesnt seem like it!!!!! I have had nothing but problems with ubuntu so far and this forum has never responded to almost anything when i needed help.....

---

### Post by markbuntu on 2009-04-20
You really need to provide more information before anyone can really help you. it would also help if you used a more specific description for your thread title like.

Toshiba a60 intermittent sound

The version of ubuntu you are using is very important, so is more specific hardware information. For sound problems there is directions for gathering that information here.

[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

---

