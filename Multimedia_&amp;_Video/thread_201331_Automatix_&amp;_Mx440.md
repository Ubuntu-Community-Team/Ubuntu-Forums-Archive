---
title: "Automatix &amp; Mx440"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by dgrafix on 2006-06-21
Ive run automatix and got the nvidia driver installed.
card is a gforce mx440

Problem is, the screen is now 640,480 with no other options in the system>preferences.

I seem to have all the correct modes listed in xorg.conf

](*,)

Edit:

Ive done some experiments and if i enter (driver = "vesa") in xorg.conf, all is fine and i get max res.
However when i change it to driver="nvidia" i only get 640x480

---

### Post by jrib on 2006-06-21
In a terminal, run ```
dpkg-reconfigure xserver-xorg
``` and setup the resolutions you want.

---

### Post by dgrafix on 2006-06-21
Ive already tried that and it just sets it back to vesa. I need nvidia for the open gl

---

### Post by jrib on 2006-06-21
does nvidia not show up as a choice for the video driver?

---

### Post by dgrafix on 2006-06-22
it does... now ( not sure what ive done there)

but,

puts me back to square 1 640x480

#-o

---

### Post by tseliot on 2006-06-22
Try point 7 of the problems section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")


And as far as resolution is concerned, see point 5 and 10

---

### Post by dgrafix on 2006-06-22
Thanks, seems to work now 3d and all

---

