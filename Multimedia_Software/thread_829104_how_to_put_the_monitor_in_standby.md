---
title: "how to put the monitor in standby?"
date: 2008-06-14
forum: Multimedia Software
---

### Post by Clive McCarthy on 2008-06-14
I want to turn the display monitor off, from within a C program. Clearly the OS can sends control signals via the graphics card to put the monitor in standby mode. I guess there is a system call to do this?

Standby: Back-light off. Not hibernate where the state of the machine is saved to disk. I want my program to just power down the monitor to save power and, most importantly, the monitor's life. An LCD display is good for three years running 24/7 but I want my application to run just from 7:00am to 11:00pm _every_ day. If can save 8 hours in 24 that increases the life by 18 months.
When 7:00am comes around I want my program to wake the monitor up.

---

### Post by HyperHacker on 2008-06-22
Run "xset dpms force off" (replace off with standby or suspend if it doesn't work) to power off the monitor, "xset dpms force on" to turn it on again.

---

