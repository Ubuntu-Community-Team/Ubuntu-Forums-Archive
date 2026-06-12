---
title: "Painless ATI driver install for x300"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by Bohlio on 2007-05-17
Hey guys, I'm new to Ubuntu and loving it so far. does anyone happen to know what the quickest, most painless way to install the newest (or a decent) driver for an ATI Raedon x300 card in Fiesty Fawn? Currently I am using the one in the Restricted Drivers Manager... Is this one good enough? is it bad? the only problem I've had is that it wont let me run desktop effects with it. Is it even a good idea to use the desktop effects with this card?

Any help would be great! Thank you.

---

### Post by stchman on 2007-05-17
> **Bohlio said:**
> Hey guys, I'm new to Ubuntu and loving it so far. does anyone happen to know what the quickest, most painless way to install the newest (or a decent) driver for an ATI Raedon x300 card in Fiesty Fawn? Currently I am using the one in the Restricted Drivers Manager... Is this one good enough? is it bad? the only problem I've had is that it wont let me run desktop effects with it. Is it even a good idea to use the desktop effects with this card?

Any help would be great! Thank you.

Yes, those are the drivers that ATI provides.  I think it is 8.34.xx

They will be just fine.

---

### Post by Bohlio on 2007-05-17
The restricted drivers are the newest ones provided by ATI ?! Thats great!, I was almost about to track down another driver to use! Do you happen to know why the desktop effects dont work correctly? When i start it, I get an error saying "The composite extention is not available" I didnt recieve this error before I installed the restricted drivers.
Thank you very much.

---

### Post by luisromangz on 2007-05-17
If you want to use Compiz/Beryl, you should try using XGL, not AIGLX as this extension is not supported in ATI drivers. There are lots of tutorials in the Internet on how install XGL properly.

Hope it works, my desktop effects looks awesome in my laptop's x300 :)

---

### Post by Bohlio on 2007-05-17
Thank you, I'll keep that in mind if i ever want to go above and beyond on my desktop with Beryl :-P

---

### Post by stchman on 2007-05-18
> **Bohlio said:**
> The restricted drivers are the newest ones provided by ATI ?! Thats great!, I was almost about to track down another driver to use! Do you happen to know why the desktop effects dont work correctly? When i start it, I get an error saying "The composite extention is not available" I didnt recieve this error before I installed the restricted drivers.
Thank you very much.

The desktop effects don't work either on my ATI equipped laptop.  I get the same error.  I was able to Enable composite extensions in the xorg.conf file but the desktop effects still did not work.

Desktop effects would be nice but it is just eye candy.  Also Google Earth stopped working when I enabled Composite Extensions.

---

### Post by Bohlio on 2007-05-18
Is it something just with the restricted driver? Because the default driver that it used right after i installed Fiesty let me enable the effects, although i occasionally got ghosting and the whole system froze :-/

---

### Post by HydroDiOxide on 2007-05-29
> **luisromangz said:**
> If you want to use Compiz/Beryl, you should try using XGL, not AIGLX as this extension is not supported in ATI drivers. There are lots of tutorials in the Internet on how install XGL properly.

Hope it works, my desktop effects looks awesome in my laptop's x300 :)

Did you get tv-out (video output on tv) to work on your x300 as well?

---

### Post by SirPerigrin on 2007-08-18
[http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty](http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty)

Using this wiki i was able to not only get good X300 Drivers, but get Direct Rendering to work as well! Just a sidenote, dont copy the Xorg.conf file entirely, unless you by some weird chance have the EXACT same laptop as the author. I made that mistake back when i was a total linux noob.

---

