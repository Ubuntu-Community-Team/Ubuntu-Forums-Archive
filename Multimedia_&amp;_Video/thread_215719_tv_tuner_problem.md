---
title: "tv tuner problem"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by darcu on 2006-07-14
I have a problem with my tv tuner (generic 878a). On boot up the card is beeing detected but tuner type is set to -1 . I've tryed to set it to type=3 with modprobe but I get "type" unrecognised option or smt like that. The tuner is working properly with Composite input. How can I set the tuner type ?

---

### Post by leo_m on 2006-07-14
With my saa7134 driver, I can specify the options card=<card-type> and tuner=<tuner-type>.  Maybe you need to specify tuner=3 instead of type=3? (I have not checked 878a documentation however).

---

### Post by darcu on 2006-07-15
Yeah I tried that too . I didn't get any errors but it still didn't work. I'll try again maybe I'll get some results.

---

