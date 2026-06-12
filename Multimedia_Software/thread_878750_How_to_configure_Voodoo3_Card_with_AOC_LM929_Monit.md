---
title: "How to configure Voodoo3 Card with AOC LM929 Monitor"
date: 2008-08-03
forum: Multimedia Software
---

### Post by BenOfLondon on 2008-08-03
I seem to have an issue in trying to locate the driver manager for making the Voodoo3 card work with my monitor. 

At the moment when i look in "System -> Preferences -> Screen Resolution" it tells me that my refresh rate is 61Mhz and stuck at 1024x768.

I did a search for a package update and found Voodoo Drivers in the Package Update Tool ... but i can not see where to configure ubuntu to use these drivers.

Where's the application for controlling my display look at feel ?

---

### Post by xc3RnbFO8P on 2008-08-03
Try
atl+f2
> gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports

---

### Post by BenOfLondon on 2008-08-03
> **Ringi said:**
> Try
atl+f2

Choose Generic
and resolution that your monitor supports



Thanks to letting me find the application, but when i now select 3dfx Voodoo3 driver, and select LCD 1280 x 1024, and click, it just tells me "Configurations Test Fails" Thats after a short black out on my screen.

I know my Monitor can do 1280 x 1024 at 75Mhz, but it looks like i am using basic VGA setup

---

### Post by biomedtech on 2008-08-03
I think 12 x 10 was a little later than a v-3's native resolution

---

