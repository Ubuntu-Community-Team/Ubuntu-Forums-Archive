---
title: "S video works on boot but shuts off upon login"
date: 2009-10-03
forum: Multimedia Software
---

### Post by jchambers on 2009-10-03
I have done this a million times on windows and the last time I remember having an issue with something like this is with windows ME. I ran my S video out to my tv to run concurrent sessions with my ubuntu box and it works while booting but when it switches over to the login screen it stops sending video to the tv....I am new to LInus and any advice is appreciated!

---

### Post by jchambers on 2009-10-03
I figured it out finally - it just needs to be told what to do - I love linux it does not make many decesions for me and although it can be frustrating figuring this stuff out I am glad to no longer on MS stuff. 

run this in the terminal 

xrandr --output S-video --mode 800x600

---

### Post by lavadisco on 2009-10-10
When I do that I get:

> Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing


How can I fix this?

---

