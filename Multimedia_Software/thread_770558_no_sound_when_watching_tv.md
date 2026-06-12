---
title: "no sound when watching tv"
date: 2008-04-27
forum: Multimedia Software
---

### Post by terry_gardener on 2008-04-27
hello 

i have been trying to get so working when watching tv i have tried tvtime and mythtv and still get no sound. 

i have checked the alsamixer and things looks ok but dont know what i am looking for really. 

when i watch in mythtv there is no sound i did manage to get some very poor quality sound by changing the audio device to dsp1 and using alsa:default. 

in tvtime i did manage to get some sound by using sox terminal command.

sox -c 2 -t alsa hw:1,0 -t alsa default (got same sound as in mythtv very poor quality)

when changed it to

sox -c 1 -t alsa hw:1,0 -t alsa default is did get ok sound but every couple of seconds (about 10 secs) it jumped/went daft for a second or 2. which became very annoying. 

any ideas 
Thanks

---

### Post by terry_gardener on 2008-05-03
this has now been sorted using the guide in wiki called saa7134-alsa 

[http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa](http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa)

---

