---
title: "not able to get widescreen res. on ATI x1400"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by syxbit on 2006-06-01
i'm a little new, and i tried installing the ATI drivers using BUMPS, but it didn't seem to do anything.
i then tried following the WIKI for ati driver install on dapper, but got errors upon typing what they said in the terminal. i'm guessing this is cause i already changed stuff when i installed BUMPS
i'd tried on flight 5, 6 and beta, but i was hoping that since my graphics card is so popular, it'd be on the top of the list for Dapper final....i guess i was wrong.
is there a simple guide to follow, as i've been looking through different threads, and everyone manages it a different way.
i have a Dell e1505 laptop. Core duo with ip3945 and ATI x1400
any ideas ?

---

### Post by jecos on 2006-06-01
[B]sudo apt-get install linux-686 xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --ovt=Xv[/B]
reboot now

---

### Post by clarkeee on 2006-08-12
jecos, you are the man. Thanks a million!

---

