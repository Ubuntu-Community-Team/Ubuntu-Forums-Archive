---
title: "Dual monitor...same image on both monitors stays checked"
date: 2011-02-15
forum: Multimedia Software
---

### Post by jl2035 on 2011-02-15
Strange problem here...

I have a problem finding the resolution that will fit my secondary monitor(24). If I check "Same image in all monitors" I can only choose resolutions that laptop can display. I don't want laptop monitor to work when I'm using secondary monitor(I close the lid)...  

If I want to uncheck "Same image in all monitors"(just to find the right resolution)...the system tells me to log out and back in again. When I do that, there's the same image on both monitors and the checkbox was automatically checked again...

I have an Asus N71J Series laptop.
Video card: ATI Mobility Radeon HD 5730 1GB

---

### Post by jl2035 on 2011-02-17
anyone?

---

### Post by raphaelviera on 2011-05-23
Hi, I had the same problem as you and I solved with the following command bellow, note that I'm using HDMI you may use VGA, see the specifications with xrand.


On terminal:
xrand
xrandr --output LVDS1 --off --output HDMI1 --mode 1920x1080


You can initiate the command in startup.
System>Preferences>Startup Application Preferences

Best Regards,
Raphael Viera

---

