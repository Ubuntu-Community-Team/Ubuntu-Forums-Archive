---
title: "Kworld UB445-Q TV tuner not working"
date: 2011-08-03
forum: Multimedia Software
---

### Post by userdce on 2011-08-03
Can anybody help me to make Kworld UB445-Q TV tuner work in Ubuntu?


Product page:
[http://www.kworld-global.com/main/prod_print.aspx?mnuid=1248&modid=6&pcid=&ifid=&prodid=512&noframe=1](http://www.kworld-global.com/main/prod_print.aspx?mnuid=1248&modid=6&pcid=&ifid=&prodid=512&noframe=1)

---

### Post by userdce on 2011-08-24
plz anybody answer

---

### Post by madvinegar on 2012-01-17
Plug the tuner and run dmesg.

You will probably find a sentence saying: Error. firmware XXXX-vXX.fw not found.

Find the exact firmware from the internet, download it and copy same to your /lib/firmware file.

Reboot and hopefully your kworld tv card will be working.

---

