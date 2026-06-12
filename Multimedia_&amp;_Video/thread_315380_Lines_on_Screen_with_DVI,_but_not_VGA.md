---
title: "Lines on Screen with DVI, but not VGA"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by soapergem on 2006-12-09
I have a 64MB Nvidia graphics card plugged into a 20" widescreen LCD. I had set the computer up with the short VGA cable that came with it, using a VGA-DVI adaptor to plug it into the main DVI port of my card.

Tonight I bought a 10' DVI cable, and when I started Edgy, the resolution had lowered itself and there were horizontal lines all through the screen. There was also a very faint effect that every object on the screen would have a shadow image of itself slightly to the right.

What happened? How do I fix it? It seemed to work fine with the VGA cable, but with this new one things got a little effed up.

---

### Post by soapergem on 2006-12-12
Okay, I think I realized that the problem is coming from the fact that the refresh rate X is trying to put out is all wrong. I've run dpkg-reconfigure on X, but it only lets me specify "1680x1050@75Hz," when in fact, my monitor wants "1680x1050@60Hz". However, this option is not even present. How can I add it in there? Anyone?

---

