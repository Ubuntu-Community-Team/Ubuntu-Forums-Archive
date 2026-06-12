---
title: "rocketfish webcam drivers"
date: 2011-07-03
forum: Multimedia Software
---

### Post by mxyzptlk on 2011-07-03
hello guys

I have a rocketfish RF-NBCAM webccam but it doesnt seem to work as it should be, the image is dark and the blue light infront of it that helps with low light enviroments is not working.

i have found some drivers for other ubuntu distros but i have the dependencies trouble

any suggestion

is what I am looking for in this page??

[http://cateee.net/lkddb/web-lkddb/US...A_SN9C20X.html](http://cateee.net/lkddb/web-lkddb/US...A_SN9C20X.html) and the driver is on this link

[http://lxr.linux.no/#linux+v2.6.36/d...spca/sn9c20x.c](http://lxr.linux.no/#linux+v2.6.36/d...spca/sn9c20x.c)

if yes how can I use it???

---

### Post by mxyzptlk on 2011-07-03
> **mxyzptlk said:**
> hello guys

I have a rocketfish RF-NBCAM webccam but it doesnt seem to work as it should be, the image is dark and the blue light infront of it that helps with low light enviroments is not working.

i have found some drivers for other ubuntu distros but i have the dependencies trouble

any suggestion

is what I am looking for in this page??

[http://cateee.net/lkddb/web-lkddb/US...A_SN9C20X.html](http://cateee.net/lkddb/web-lkddb/US...A_SN9C20X.html) and the driver is on this link

[http://lxr.linux.no/#linux+v2.6.36/d...spca/sn9c20x.c](http://lxr.linux.no/#linux+v2.6.36/d...spca/sn9c20x.c)

if yes how can I use it???

well it seems that no one has a clue about this problem

---

### Post by dyem1 on 2011-07-03
So can you see your webcam but the light doesn't work and it has dark image?
If you have already tried to configure the webcam settings (saturation, contrast...), i don't know what could be the problem.

PD: The links are broken.

---

### Post by mxyzptlk on 2011-07-04
> **dyem1 said:**
> So can you see your webcam but the light doesn't work and it has dark image?
If you have already tried to configure the webcam settings (saturation, contrast...), i don't know what could be the problem.

PD: The links are broken.

yes i see the image but its too dark and yes those are not the links sorry

this is the link for the driver

[http://lxr.linux.no/#linux+v2.6.39/drivers/media/video/gspca/sn9c20x.c](http://lxr.linux.no/#linux+v2.6.39/drivers/media/video/gspca/sn9c20x.c)

---

### Post by no2498 on 2011-07-04
install v4lucp
it comes up in system , preferences . as video4linux control panel
it should help with the dark image

it wont fix every thing but it does help some

---

