---
title: "Ubuntu only using onboard sound chip, not sound card"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by King_Critter on 2007-12-20
So yeah... a few days ago Ubuntu suddenly decided to shun my Sound Blaster card, and only output through the sound chip on the motherboard. Ubuntu seems to *see* the card, it's just not using it. Does anyone know how I can fix this?

---

### Post by nieekou on 2007-12-21
same here, i haven't solved it yet, check this [http://ubuntuforums.org/showthread.php?t=646299](http://ubuntuforums.org/showthread.php?t=646299)

---

### Post by Dave Otter on 2007-12-21
Try 
         Applications-Accessories-Terminal

                            type - sudo asoundconf set-default-cardCARD   
                                replacing CARD with the card you want to use. 

     You might also try (if the above fails) go to BIOS and disable internal soundcard

---

