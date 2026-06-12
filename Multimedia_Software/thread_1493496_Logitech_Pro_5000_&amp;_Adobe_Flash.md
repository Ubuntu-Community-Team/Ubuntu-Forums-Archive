---
title: "Logitech Pro 5000 &amp; Adobe Flash"
date: 2010-05-25
forum: Multimedia Software
---

### Post by TNAFan on 2010-05-25
For some reason Adobe Flash does not even recognize that I have this webcam plugged in.  Does anyone out there know how to get this working?

---

### Post by no2498 on 2010-05-26
not sure this works on the 5000

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

910 and up cheese webcam booth is loaded
look in sound & video
try the cam in cheese first

hope it helps

---

### Post by TNAFan on 2010-05-26
cheese works.  As a matter of fact everything works but inside flash

---

### Post by no2498 on 2010-05-26
have you done this yet

sudo apt-get install ubuntu-restricted-extras



btw did you click allow and remember in adobe's settings manager

and look at all the sites that is listed

hope this helps

---

### Post by TNAFan on 2010-05-26
Actually, I just noticed the settings manager does not seem to want to load for me.

---

### Post by no2498 on 2010-05-27
you can get into it at adobe

---

### Post by no2498 on 2010-05-27
you may also try this

open a terminal type/put this in it

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash

and do not close the terminal

---

### Post by TNAFan on 2010-05-30
> **no2498 said:**
> you can get into it at adobe

Nope, tried, didn't load.

---

### Post by TNAFan on 2010-05-30
> **no2498 said:**
> you may also try this

open a terminal type/put this in it

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash

and do not close the terminal

justin@THEBEAST:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so flash
No command 'flash' found, did you mean:
 Command 'flasm' from package 'flasm' (universe)
flash: command not found

---

### Post by TNAFan on 2010-07-31
Giving this a bump, still doesn't work for me. :(

---

### Post by no2498 on 2010-08-01
i see firefox does not load flash
try getting and try the cam in/with opera browser

[http://www.opera.com/](http://www.opera.com/)

hope this helps

---

### Post by TNAFan on 2010-08-15
Bump? Not working?

---

### Post by no2498 on 2010-08-15
on my other computer with lucid on it
i had to uninstall what ubuntu put on/in it for flash
it was tiring to open mine in totem 
then went an got flash from adobe

hope this helps

---

### Post by TNAFan on 2010-08-15
Flash is actually loading now, but still not seeing my cam.

---

