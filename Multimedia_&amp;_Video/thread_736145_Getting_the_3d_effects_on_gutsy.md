---
title: "Getting the 3d effects on gutsy?"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by Loonux on 2008-03-26
I've finally managed to sort my wifi problems out in gutsy so have downloaded the latest drivers from the ATI and installed them. This worked well and my Dimension 6400 laptop now runs at its correct resolution (1200x800) and i've installed the ttf fonts which has made things look a million times nicer. 
However, I still cannot get the compiz 3d effects working with my Radeon x1400 128mb video card. When I click then normal or extra on the visual effects tab (which, I assume, Is how one enables compiz in gutsy?) I get a message saying 'Desktop effects could not be enabled'.

Am I missing a step or not doing something correct? the driver is showing up as fglrx, so I dont know where to go from here.....

Thanks for any advice.

---

### Post by CheShA on 2008-03-26
Try  installing Envy (a utility to install the latest ATI / nvidia drivers) from [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)   then run it from a command line

```

sudo envy -g 
```

Choose to install the ATI driver and when it has finished, reboot as it tells you. You should then be able to select desktop effects.
EDIT: I have only ever run desktop effects on an ATI 1300 and it didn't work particularly well - i ended up having to go back to standard desktop because it crashed my X session every 5 minutes.  It works a-ok on my nvdia 7600 at home though, and plenty of other people use it under ATI so  YMMV

---

### Post by Loonux on 2008-03-26
Thanks for the reply. Will that install a different driver to that I downloaded and installed from the ATI/AMD website then?

---

