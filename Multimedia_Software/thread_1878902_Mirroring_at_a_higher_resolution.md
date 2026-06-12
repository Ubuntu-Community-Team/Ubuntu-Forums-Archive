---
title: "Mirroring at a higher resolution"
date: 2011-11-10
forum: Multimedia Software
---

### Post by mightybuddha on 2011-11-10
Hi guys,

I'm doing a presentation using an external monitor on a Dell Mini 9 (with a touchscreen).  For this I am mirroring the display on the mini to the external monitor.

Problem is, the maximum resolution it will allow them to mirror is 800 x 600 :(  so the external monitor doesn't look good for the presentation.

is there any way to force mirroring at a higher resolution?

Cheers!

(I'm using 11.10 and the mini has intel graphics, and the ideal resolution of the external monitor is 1280x1024)

---

### Post by papibe on 2011-11-10
May be could work if you set separate X screens instead of mirroring?

Just a thought,
Regards.

---

### Post by mightybuddha on 2011-11-10
thanks for the suggestion, though it does need to be mirrored since I won't be able to see the other screen. :(

---

### Post by mightybuddha on 2011-11-12
bumpity :)

---

### Post by BicyclerBoy on 2011-11-12
You can change the framebuffer size of the (smaller) netbook screen to match the external & then 'pan' around the desktop..

xrandr --fb 1280x1024 --output LVDS1 --scale 1x1

Try changing scaling..

---

