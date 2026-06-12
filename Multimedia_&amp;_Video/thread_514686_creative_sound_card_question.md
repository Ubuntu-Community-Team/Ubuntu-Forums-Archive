---
title: "creative sound card question?"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by cooldudeny on 2007-08-01
Hi i have a creative sound blaster audiogy and i was wondering if there is a driver for the ubuntu ? 
for me to use it 

thanks

---

### Post by wolfen69 on 2007-08-01
it says here [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs) that it is

---

### Post by BobLand on 2007-08-01
I have the Audigy SE.  The driver is ca0106.  Not sure if it's the same as the audiogy(???).  Follow this [[COLOR="Blue"]_link_]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound")[/COLOR].  It should get you up and running.

---

### Post by cooldudeny on 2007-08-02
hey i have the audigy SE too

---

### Post by fredj on 2007-08-03
There is a driver in Ubuntu for the audigy not sure about the audigy se which is a very different card.
Open a terminal (Applications-Accessories->Terminal) and type sudo lshw -class sound
to see if your soundcard has been detected correctly and to see the name of the driver being loaded
for it.

---

### Post by sbazin on 2007-08-06
If your are looking for Creative drivers this is a good place to start:
[http://opensource.creative.com/](http://opensource.creative.com/)

Also this page can tell you if your Creative sound card is supported by ALSA drivers and specifically with what driver.
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

good luck

---

