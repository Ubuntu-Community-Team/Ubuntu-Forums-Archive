---
title: "Fuzzy Screen"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by AquaFox90 on 2006-09-22
I changed my ATi to an Nvidia Geforce and now my screen looks fuzzy. I don't know why this is happening and I would appreciate help. Maybe double anti-aliasing is happening but I really don't know.. Please help.

---

### Post by tseliot on 2006-09-22
Try this:
```
sudo dpkg-reconfigure xserver-xorg
```

and press ENTER whenever you don't know the answer to a question.

---

### Post by p.n on 2007-08-18
I have similar problems and running

```
sudo dpkg-reconfigure xserver-xorg
```

does not work either.  I am using the exact refresh rates and screen res published in the monitor manual but I still get a very fuzzy screen.  My onboard graphics card gives much clearer picture.

Any help?

Regards
p.n

---

### Post by p.n on 2007-08-18
OK, so it was not the driver of the card.  It was the monitor.  I did a auto adjust from the monitor menu (on the physical monitor, not Ubuntu) and all was crisp and clear again.

Sorry for the ignorance.

Regards
p.n

---

