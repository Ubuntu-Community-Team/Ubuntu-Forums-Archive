---
title: "output over hdmi is too large (nvida)"
date: 2010-03-28
forum: Multimedia Software
---

### Post by DR.cable on 2010-03-28
hi im running ubutu 9.10 with the standard nvida proprietry drivers as a media center. the output is over hdmi, through a a/v reciver and onto a lcd television. my proble mis that the output is too large for the screen even whan outputting at a smaller resoultion than the native resolution of the television. this means that the top, bottom, left and right of the output is chopped off. in windows i can adjust the size of the output useing some sliders to get the image to fit the screen. however these are only available in the windows drivers and i cannot find a substitute in the ubuntu ones. one way of doing it may be to output black bard at the sides of the screen but i have no idea how to do this. thanks for any help DR.cable

---

### Post by DR.cable on 2010-03-29
bump with more information
the model of the tv is a panasonic viera th-37pxoba.
thanks again gor any help

---

### Post by doas777 on 2010-03-29
the options you are looking for are called "overscan" (or more precisely in your case, underscan).

look in the nvidia cp to see if your card/driver allows you overscan control. it varies by model of card. my 7950 has it, but every card I've tried in the 8200-8600 series have not been compatible with overscan control

hopefully it will be there, and work out for you.

---

