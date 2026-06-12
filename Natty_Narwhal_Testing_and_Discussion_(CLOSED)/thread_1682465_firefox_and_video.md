---
title: "firefox and video"
date: 2011-02-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-02-05
I have been trying to watch news feed videos on firefox it flashes intermitent white flashes on the video screen has any one else noticed this
amd dual core processors ati radeon 3100 graphics

---

### Post by cariboo on 2011-02-06
Which version of Firefox and flash are you using?

---

### Post by rbrick49 on 2011-02-06
firefox 4.0b10 flash 10.1r102
thanks Ca

---

### Post by Harry33 on 2011-02-06
> **rbrick49 said:**
> firefox 4.0b10 flash 10.1r102
thanks Ca

Do you have 64-bit architecture? The latest square-flashplugin is 10.3d162.

Do you experience this with Chromium (stable 9.0.597.84~r72991)?

Are you using xserver-xorg-video-ati (not fglrx)?

---

### Post by rbrick49 on 2011-02-06
Harry hello yes amd x64 ati radeon card 3100 havent installed chromium might give it a shot and see what happens
regards Ron

---

### Post by rbrick49 on 2011-02-06
firefox is the problem chromium works just fine
thanks Harry

---

### Post by zenarcher on 2011-02-06
I'm noting the same thing with the same versions and architecture.

Regards,
zenarcher

---

### Post by rbrick49 on 2011-02-06
well next week I am going to update my graphics card to a radeon 6950 looks like I am going to have some fun with that if it works good if it doesnt more posts on here

---

### Post by Harry33 on 2011-02-06
> **rbrick49 said:**
> well next week I am going to update my graphics card to a radeon 6950 looks like I am going to have some fun with that if it works good if it doesnt more posts on here

For Radeon HD5*** and HD6*** series cards you need the newest open sourcer drivers.
And of course Natty's new kernel 2.6.38-* series.

As xserver-xorg-video-ati_6.14 is not yet in Natty repos, you need to try the latest git versions (xorgedgers PPA).

You might want to read this:
[http://lists.freedesktop.org/archives/xorg/2011-February/052420.html](http://lists.freedesktop.org/archives/xorg/2011-February/052420.html)

---

### Post by rbrick49 on 2011-02-06
Hi Harry thanks for the info mate I just got some new updates the 2.6.38 kernel was in there I will read up on the info you posted shortly
regards Ron

---

