---
title: "CPU Frequency Scaling stuck at 1ghz"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by puccaso on 2010-09-03
i am using the new maverick beta, upgraded from lucid lts.

the cpu frequency scaling is stuck at 1ghz (or thats what the gnome-panel says)

when i try to put notch it up to 1.8ghz, it doesnt do anything.
i have a 'tail -f dmesg" in /var/log running in the background
but i see no changes

how can i fix this?

---

### Post by mc4man on 2010-09-03
While probably not your issue will mention - 
The only time here where I've seen scaling stay 'stuck' at the lowest is where, due to a combo of factors, allowed the laptop to hit the 'scale down' temp. (the temp where the cpu scales back in an attempt to control heat rise and  avoid a shutdown

After that the cpu is locked at min. until a reboot, even if the temp issue is under control and back to normal

---

