---
title: "possible to increase sensitivity of wacom touch on hp tx2"
date: 2009-08-11
forum: Multimedia Software
---

### Post by wolfgangpauli on 2009-08-11
Hey,

Thanks for the previous help. I tried to increase the sensitivity of the touchscreen because we are planning to use it with kids and it is important that it is really sensitive ...

I tried to work with xsetwacom set while running an x session. So far no results with changing

PressCurve (is always -1, or 255 255 255 255, depending on whether i use -s option)
Capacity (also -1)
ClickForce (did not change anything)

I have not tried putting those params into the xorg file and restarting the x server, so i am going to do that now, but something tells me that it won't make a difference, because setting Buttons with xsetwacom worked without restart ...

Thanks for any suggestions.

---

### Post by Favux on 2009-08-12
Hi wolfgangpauli,

Did you comment out the n-trig subsection of the 10-wacom.fdi?

---

### Post by wolfgangpauli on 2009-08-20
Amazing! Thanks so much. I read something about commenting out the ntrig stuff, but i think it was a different context, so i had forgotten about it. thanks! so glad we don't have to use vista ...

---

### Post by Favux on 2009-08-20
Hi wolfgangpauli,

You're welcome.  Sounds like you're good to go.

---

