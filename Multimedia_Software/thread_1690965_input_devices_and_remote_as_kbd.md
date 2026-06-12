---
title: "input devices and remote as kbd"
date: 2011-02-19
forum: Multimedia Software
---

### Post by stevezau on 2011-02-19
Hi All,

Im struggling to understand how the linux kernel uses input devices for keyboard input..

I have a few different tv tuner cards and a few different remots that im trying to get working with lirc..

In almost all of them they seem to register them selfs as keyboards. I can use the devinput driver for LIRC which works fine BUT i seem to get double key presses.. 

Can someone point me to some doco on how to stop ubuntu from listening to the input device for the keyboard event?

I've tried to look at HAL and udev and nothing has worked :(.. I can even go to a tty console (alt f2) and press left on the remote which moves the cursor left.. how do i stop this???

thanks!

---

