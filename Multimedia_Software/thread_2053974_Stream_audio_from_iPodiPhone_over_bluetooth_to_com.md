---
title: "Stream audio from iPod/iPhone over bluetooth to computer"
date: 2012-08-31
forum: Multimedia Software
---

### Post by aventrax on 2012-08-31
I'm wondering about doing the stuff described in this thread [[http://ubuntuforums.org/showthread.php?t=1464189]](http://ubuntuforums.org/showthread.php?t=1464189]) but WITHOUT pulseaudio.

I tried pulseaudio loopback module for my DVB-T card and the biggest problem was about the delay added by pulseaudio server (~600ms).

I'm going to use my linuxbox with bluetooth a2dp sink to stream audio from my macbook, so I can watch a movie using the speakers attached to the linuxbox. I CAN'T have delay.

So, bypassing pulseaudio, does anyone know if is possible to use the ALSA loopback kernel module instead? 

[http://www.alsa-project.org/main/index.php/Matrix:Module-aloop](http://www.alsa-project.org/main/index.php/Matrix:Module-aloop)

---

### Post by aventrax on 2012-09-06
I also would want to initiate the connection from the source, not from the sink device. Is it possible?

---

### Post by oldos2er on 2012-09-06
Posts moved to new thread. Rather than post a new question in an old thread (which few people are likely to see), please start a new thread.

---

