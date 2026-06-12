---
title: "x11vnc error after changing video driver"
date: 2015-10-12
forum: Mythbuntu
---

### Post by John_Kreis on 2015-10-12
I believe my issue is actually with the X server as opposed to VNC but the manifestation is that my VNC server is not starting and I am getting error "XOpenDisplay failed (:0)". I was using the generic Xorg display and I was not able to figure out how to change the screen resolution so I changed to the latest AMD Driver (I have a GeForce 8300) through the Additional Drivers app. 

echo $DISPLAY returns nothing, ps aux | grep X (as well as x) returns nothing of interest.

---

### Post by steeldriver on 2015-10-12
Hello and welcome to the forums

Do you have physical access to the machine? if the "real" X server isn't starting then I think you are correct, it's not really anything to do with x11vnc

What version of Ubuntu are you running?

---

### Post by John_Kreis on 2015-10-13
No video directly connected , I am running 14.04.3 LTS

---

### Post by John_Kreis on 2015-10-14
My x server user was set to console, I changed it anyone. Fixed it

---

