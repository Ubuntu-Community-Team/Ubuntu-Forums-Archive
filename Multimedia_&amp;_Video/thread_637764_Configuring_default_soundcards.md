---
title: "Configuring default soundcards"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by aarong on 2007-12-11
Im having a super hard time making the sound card i want to use toe overall default. It will work for anything but web browsing. The comprehensive sound guide section on this might just be a little too advanced for me to figure out. Any help would be much appreciated.

---

### Post by Dave Otter on 2007-12-11
Applications-Accessories-Terminal
                   type---  asoundconf list


                now type:-   asoundconf set-default-cardCARD  replaciing CARD with the soundcard you wish to use.

---

### Post by aarong on 2007-12-11
wow, that fixed everything...after like a month of trying...thanks

---

