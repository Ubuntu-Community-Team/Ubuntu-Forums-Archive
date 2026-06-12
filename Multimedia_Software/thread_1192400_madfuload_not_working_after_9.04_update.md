---
title: "madfuload not working after 9.04 update"
date: 2009-06-20
forum: Multimedia Software
---

### Post by digitoxin on 2009-06-20
Hello!

Yesterday i updated to version 9.04. Since then, madfuload does not work anymore. 

Madfuload uses udev to load a driver to the soundcard, in my case m-audio Transit.
But udev does not catch on to this.
lsusb shows: Bus 003 Device 002: ID 0763:2806 Midiman M-Audio Transit DFU
Thats the id that should trigger the firmware loading process but nothing happens.

I had 8.10 before that and it worked fine, also on 8.04 it worked....

messages log shows the madfuload programm is simply not started by udev.

Here comes the interesting part: If i do /etc/init.d/udev refresh-devices then sometimes it works but sometimes i end up with a new soundcard device thats a copy of my internal intel one, that is i suddenly get another intel soundcard device added for every udev refresh-devices call but not the transit one (also firmware not loaded, just the intel soundcard added another time).
 
For me this looks like a serios bug.. any help with that?

---

