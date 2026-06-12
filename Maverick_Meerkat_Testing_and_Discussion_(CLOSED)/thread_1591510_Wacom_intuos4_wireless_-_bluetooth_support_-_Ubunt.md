---
title: "Wacom intuos4 wireless - bluetooth support - Ubuntu 10.10 (Maverick Meerkat)"
date: 2010-10-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by landandy on 2010-10-09
Hi,
my intuos4 works fine, connected to USB, but i think there is no support for connecting it with bluetooth. (It connects via bluetooth, but it es recognised as mouse and does not work.)
Is there someone who can help me?
Thank you!
by!
Andy

---

### Post by Favux on 2010-10-10
Hi landandy,

Welcome to Ubuntu forums!

To figure out the bluetooth we'll have to look at a few things.

The thread for the Wacom Graphire bluetooth is here:  [http://ubuntuforums.org/showthread.php?t=674738](http://ubuntuforums.org/showthread.php?t=674738) along with the associated community wiki:  [https://help.ubuntu.com/community/WacomGraphireBluetooth](https://help.ubuntu.com/community/WacomGraphireBluetooth)  The thread is where you would normally post bluetooth questions.

What output are you looking at that says it is a mouse?

Let's look at the output of the following (with your bluetooth on):
```
xinput --list
```
and
```
dmesg | grep [Ww]acom
```
and
```
lsmod | grep [Ww]acom
```
and
```
more /proc/bus/input/devices
```
and see what you have.

Hope this helps.

---

