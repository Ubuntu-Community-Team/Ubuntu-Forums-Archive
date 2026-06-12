---
title: "networking"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by mirinamulhaq on 2010-03-07
hi
i used my internet connection on ubntu one month ago and at that time it was working well.now today i tried to connect to internet once again usuing the same settings but i was not able to connect to internet.moreover there used to be a network icon on right side of my pannel on my desktop  whenever i used to switch on my ubuntu os. but from last few days it has disappeared and i am no more able to sea this even though i tried to connect to internet.also my system reports me problem of some serious kernel crash i dont know what is going on please help

---

### Post by jamere on 2010-03-07
You can get the network applet to appear again by right-clicking in panel and adding back the "notification area". Worked for me anyway.:D

---

### Post by amrypma on 2010-03-07
if that doesn't work...

open a terminal and run nm-applet.
If the networking icon reappears you should look at gnome's startup programs in System-> preferences and add it.

---

### Post by mirinamulhaq on 2010-03-07
it appeared when i typed nm-applet on terminal but when i close terminal it disappears again

---

### Post by Iowan on 2010-03-07
Have you checked System>Preferences>Startup Applications to see if Network Manager is checked?

---

### Post by mirinamulhaq on 2010-03-07
there is no such icon present however i have a guest account on that as well and when i logged into that everything was alright there

---

### Post by amrypma on 2010-03-08
Then you just have to add it your self.
Go to startup applications and add nm-applet in the new item's command. It should run as a regular application.(not in a terminal like you did above.)

when you're done log out and log back in again and the networking applet should appear.

---

### Post by mirinamulhaq on 2010-03-09
thanku it worked well.

---

