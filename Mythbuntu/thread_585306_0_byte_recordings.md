---
title: "0 byte recordings"
date: 2007-10-21
forum: Mythbuntu
---

### Post by Lem on 2007-10-21
After a while running mythtv, I tend to get 0 byte recordings. mythbackend.log reports no errors though!?

I'm stumped, any ideas?

---

### Post by tgm4883 on 2007-10-21
What tuner?  Have you checked your permissions in your recording dir?

---

### Post by Lem on 2007-10-21
it's a nova t 500. Permissions should be ok as other recordings are working and it's a fairly default mythbuntu install from the iso other than some tinkering to get the card and remote working. A reboot fixes it (temporarily)

---

### Post by Lem on 2007-10-21
I've added a 200msec tuning delay (apparently a good thing for nova t cards - although it doesn't suggest a figure). Will see how that works (or not!)

---

### Post by johnsto on 2007-10-21
I used to get that when my (USB) tuner wasn't working or had been sent bad commands. Usually I had to turn off the machine, unplug and replug the tuner (so it lost power and hence memory) and turn the machine back on again. 

Worked every single time, simply due to presumably dodgy drivers.

---

### Post by Lem on 2007-10-22
The delay seems to have got it working again without restarting. I'll try scheduling some random recordings and see how I get on.

---

