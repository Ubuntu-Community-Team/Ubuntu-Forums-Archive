---
title: "Laptop display issue when have external monitor also"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Blasphemist on 2011-04-04
I have a toshiba satelitte l505 laptop and external acer monitor. I don't clone the displays but rather extend the desktop. If I don't match up the resolutions of the two monitors carefully, I have an issue.

You can move the mouse off the top of the laptop monitor. If you move the mouse to left side or bottom, it stops at the edge. Move it to the right and it goes to the external as it should. Move it to the top and it keeps going past the edge of the physical display. The panel is correctly at the top of the screen on both monitors. Windows that open are often placed such that the top of the window is off of the top of what I can see on the laptop monitor.

In monitors, one of the windows that opens partially off the top of the display, I can press detect monitors and it does seemingly nothing. If I set the resolutions of both monitors to the same low resolution all works fine but I can't stand the resolution. I currently am using 1366x768 (16x9) on the laptop and 1280x800 (16x10) on the external. It seems like you can move the mouse about a panel width off the top of the screen. If I set the external to 1600x900 (16x9) displays shows the external get taller and when set like that the problem gets worse than when the external is set to the lower 16x10 resolution. Go figure. 10 vs. 9 you'd think 10 would be the worse setting since it doesn't match the internal display.

I installed ARandR and that went fine until I tried to launch it. I have a bug report [https://bugs.launchpad.net/bugs/750427](https://bugs.launchpad.net/bugs/750427) in on it not being able to run. I'm looking for someone to help me understand this better and to help me solve it if it doesn't require ARandR. It seems that compbiz is no longer installed with natty and I don't know if it would help me if I installed it. This install is from the daily build I downloaded April 3.

---

### Post by Blasphemist on 2011-04-07
I finally decided to install what I had used in maverick to try and solve this issue. From the software center you can install Multiple Screens (grandr). The description is that it is a simple gtk interface to allow changing the resolution and frequency of your monitor dynamically using a simple interface. It also says that for drivers that support it, it can also configure the relative positioning of multiple monitors.

Using this I now see the top of the monitors at the same level. I changed my external monitor to its highest, and my preferred, resolution of 1600x900 and left my laptop display at 1366x768. On the layout tab I dragged the external monitor to the right hand box. And actually this left me with my extended desktop not filling the whole external monitor. I eventually ran out of ideas of how I could fix that and decided to reboot. And what do you know, it came up right.

I am using unity and haven't yet loaded the gnome desktop to check it but I don't expect a problem with it. I will advise that everytime I load this program it still comes up with both monitors in the middle box on the layout tab. I have been cancelling out because I don't to screw with something that is working.

Windows that come up do now respect the top of the laptop monitor correctly and the mouse won't go off the top of the screen. That was a pain of a problem. The mouse will now go off the bottom of the laptop monitor but I think windows and the launcher are respecting the bottom of the physical display on the laptop.

---

