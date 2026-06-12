---
title: "sound not muted when headphones are inserted"
date: 2012-01-05
forum: Multimedia Software
---

### Post by oh my on 2012-01-05
i have a problem with my oneiric install.. when I plug in the headphones the speakers don't get turned off... The sound is transmitted through my normal speakers and the headphone at the same time. 
I need to go to alsamixer and turn down the sound for the speakers manually. Every time I use sound-control (kmix) the speakers get turned on at full power again.

I would very much like it back to the normal way that the speakers are turned off when the headphone is inserted.

I think this issue appeared only recently, about 3-4 weeks ago. But I can't remember when I last used headphones on the laptop before that, so it may in fact have been broken for longer. It definitely used to work fine before I upgraded to oneiric (I just can't say whether it never worked on oneiric or just broke more recently)

regards oh my

---

### Post by inobe on 2012-01-05
hello.

the feature is called, headphone jack sense.

edit: i googled the results for that, i have no idea how to fix that since i never use headphones, hope i was of some help.

[https://www.google.com/search?aq=2&oq=Headphone+Jack+Sense&sourceid=chrome&ie=UTF-8&q=headphone+jack+sense+ubuntu+11.10](https://www.google.com/search?aq=2&oq=Headphone+Jack+Sense&sourceid=chrome&ie=UTF-8&q=headphone+jack+sense+ubuntu+11.10)

---

### Post by oh my on 2012-01-05
Thanks! I guess I was missing the right search terms. This fixed it:
[http://www.incunabulum.de/blog-archive/ubuntu-11.10-and-a-missing-headphone-jack-sense-flag](http://www.incunabulum.de/blog-archive/ubuntu-11.10-and-a-missing-headphone-jack-sense-flag)
(so just going into alsamixer and switching automute from disabled to enabled)

Great work and thanks again! :)
ohmy

---

### Post by inobe on 2012-01-05
thanks for marking your topic as solved and providing the fix.

glad you found the solution:D

---

