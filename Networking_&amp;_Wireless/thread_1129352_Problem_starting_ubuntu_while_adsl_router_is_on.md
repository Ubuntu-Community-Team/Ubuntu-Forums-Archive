---
title: "Problem starting ubuntu while adsl router is on"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by haho13 on 2009-04-18
Hi everybody!
I have a problem that couldnt solve for the last few days searching the net please HELP!!!

Im with ubuntu 8.04, the problem is that when i start ubuntu and my adsl router is on at the same time, ubuntu doesnt start i.e. after the logon proceedure the screen is blank for more than 5 minutes and than it starts, giving me an error message that it is immpossible to load the standart desktop and loads a desktop with icons, colors etc. changed, and ubuntu runs really slowly.

If the router is off at startup, Ubuntu loads normally.

It is really annoyng and disturbing me very much pls help!!

---

### Post by sgosnell on 2009-04-18
Are you certain that isn't just a coincidence?  I don't see how a router being on or off could affect a boot sequence.

---

### Post by haho13 on 2009-04-18
Im absolutely sure it happens every time the modem is on and never when it is off. I suspect it has to do something with pppoeconf but cannot immagine what exactly. I edited etc/peer/dsl-provuder file commenting all the strings but nothing changed.

---

### Post by lisati on 2009-04-18
It does seem rather odd that having your router on could prevent a proper start up. I'm inclined to the opinion that it's probably not your router *per se*, but something else that kicks in at start up that might want to access your router (or internet connection), that says "I'm outta here" then it can't detect a connection, but hangs around when there is a connection.

---

### Post by haho13 on 2009-04-18
Lisati I think probably you are right but how to determine which program is doing this

---

