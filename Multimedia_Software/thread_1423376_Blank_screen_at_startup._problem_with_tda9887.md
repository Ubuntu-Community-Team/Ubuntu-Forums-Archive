---
title: "Blank screen at startup. problem with tda9887 ?"
date: 2010-03-06
forum: Multimedia Software
---

### Post by morgan88 on 2010-03-06
When I boot, about 3 out of 4 times, I only get a black screen.

Bios and grub works as it should. after that I see a cursor blinking about 4 times, and then the white ubuntu logo for a few seconds. After that I can only see the cursor blinking 10 times or so and then a few lines of text is shown very quickly on the screen. After that the screen goes completely blank (sometimes the login screen flashes very fast before it goes blank).
However, I can hear the login sound, and I can reboot using ctrl-alt del

This have started just about a week ago. Im running Karmic, with kernel 2.6.31.20. The same thing happens on kernel 2.6.31.19, and I'm fairly sure that is also the case with 2.6.31.17.
Graphics: Radeon HD5770, catalyst 10.1

when checking through syslog I found out that every time this error occurs, I find the error

kernel: [   33.912946] tda9887 0-0043: i2c i/o error: rc == -6 (should be 4)

I dont get this error when it boot successfully.
As I understand, tda9887 have something to do with cx88 and my tv-tuner hvr-1300. This card worked fine in 9.04, but not at all in 9.10.

Anyone have any idea how to resolve this? Have kind of given up on the tv-tuner, but want to be able to boot more reliably

---

