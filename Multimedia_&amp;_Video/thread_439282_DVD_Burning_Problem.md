---
title: "DVD Burning Problem"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by Angelbeast on 2007-05-10
I just tried to burn a dvd by using DeVeDe to convert an avi file to an iso image. Then burning it to a 4.7g dvd-r using KB3. The end result isshown in the attached screenshot. What didi do wrong?

---

### Post by taurus on 2007-05-10
It would be nice if you would also include which release you are running and which version of devede you are using.

---

### Post by Angelbeast on 2007-05-10
> **taurus said:**
> It would be nice if you would also include which release you are running and which version of devede you are using.

Oops, sorry...DeVeDe 2.9 and K3b 1.0 and Ubuntu 7.0.4

---

### Post by taurus on 2007-05-10
I suppose you installed the older version of devede from synaptic.  What if you remove it and install the latest version from this site, [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)?

```
sudo aptitude remove devede
```

---

### Post by Angelbeast on 2007-05-10
> **taurus said:**
> I suppose you installed the older version of devede from synaptic.  What if you remove it and install the latest version from this site, [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)?

```
sudo aptitude remove devede
```

Okay got it...Now how do i install this pacckage?

---

### Post by taurus on 2007-05-10
You download the devede-2.13.tar.bz2 (at the bottom of the page).  Then, open a terminal and do

```
cd ~/Desktop
tar xvjf devede-2.13.tar.bz2
cd devede-2.13
sudo ./install.sh
```

---

### Post by Angelbeast on 2007-05-10
It went through all of this and then stopped. I don't see DeVeDe in the apps menu

---

### Post by Angelbeast on 2007-05-10
Okay it's there now...So i'll give it another try and see if the quality is any better...Thank you so much...

---

### Post by Angelbeast on 2007-05-10
the quality is still the same. Is there something better that i can use that will convert and burn?

---

### Post by taurus on 2007-05-10
Another option is tovid.

[http://www.videohelp.com/tools/tovid](http://www.videohelp.com/tools/tovid)

---

### Post by kelvin spratt on 2007-05-10
I downloaded te latest version from [http://www.getdeb.net/](http://www.getdeb.net/) its a deb file used Gdeb installer works excellent for 
me

---

### Post by kelvin spratt on 2007-05-10
forgot de ve de i'm talking about

---

### Post by Angelbeast on 2007-05-11
> **taurus said:**
> Another option is tovid.

[http://www.videohelp.com/tools/tovid](http://www.videohelp.com/tools/tovid)

do i install this the same wy?

---

### Post by Angelbeast on 2007-05-12
*bump*

---

### Post by Angelbeast on 2007-05-16
Hello?

---

### Post by Angelbeast on 2007-05-16
anybody?

---

### Post by emperorming on 2007-05-17
try setting Devede to deinterlace in the quality options menu & try again...mine did the same thing

---

### Post by Angelbeast on 2007-05-17
> **emperorming said:**
> try setting Devede to deinterlace in the quality options menu & try again...mine did the same thing

that did the trick! thank you so much...

---

