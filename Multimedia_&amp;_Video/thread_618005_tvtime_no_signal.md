---
title: "tvtime no signal"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by srasiroslayer on 2007-11-19
Hello,
i have tried locating a subject as close as possible to this but to no avail.

i have a mercury philips 7130 tv tuner
after reading many posts i was able to detect it correctly with tvtime following this procedure since ubuntu 7.10 automatically detects it as sound:
rmmod saa7134_alsa
then
rmmod saa7134
then modprobe saa7134 card=20
if in the above command i add tuner = "any number" the tvtime scanner won't recognise it.
so now that i have everything setup i open tvtime and i have 5 input options to choose from:
-television
-tv (mono)
-composite 1
-composite 2
-s-video

since everything is working fine all i have to do is run tv-time scanner with input set for television
and i get no signal from 45Mhz to 958Mhz
hope its an easy one.
thank you.

---

