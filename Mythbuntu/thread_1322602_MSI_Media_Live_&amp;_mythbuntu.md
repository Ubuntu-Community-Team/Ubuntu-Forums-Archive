---
title: "MSI Media Live &amp; mythbuntu"
date: 2009-11-11
forum: Mythbuntu
---

### Post by bobthebob1234 on 2009-11-11
Hi.

I have recently purchased a MSI media live box. I have got most things working apart from the LCD panel at the front.

I have followed the instructions at [http://www.mythtv.org/wiki/MSI_Media_Live](http://www.mythtv.org/wiki/MSI_Media_Live) and [http://www.mythtv.org/wiki/Futaba](http://www.mythtv.org/wiki/Futaba).

If i start it using ```
sudo LCDd
``` it will display some stuff
(Client :0, Server:0) or words to that effect. However mythtv don't want to show anything on it when I play a dvd or anything. I have ticked use LCD in the config, but still nothing.

Ideally I want the chapter and time displayed when I play a dvd, and just a clock when nothing is playing.


Also the power button on my remote does nothing. Can I make this do something (like standby the box (will it still show the clock?))

Thanks

---

### Post by madverb on 2009-11-11
For the power button you will need to create a bash script that is run via irexec.

---

### Post by bobthebob1234 on 2009-11-11
Thanks, any suggestions? Kinda new to the whole bash scripts

---

