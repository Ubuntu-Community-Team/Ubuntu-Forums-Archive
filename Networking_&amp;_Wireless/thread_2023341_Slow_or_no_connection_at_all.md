---
title: "Slow or no connection at all"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by Frekker on 2012-07-12
I went on vacation for a week some days ago, and when i came back my internet was really slow (about 1-6 KB all the time) i couldn't figure out what the problem was, so i connected to the other internet in our house which worked great. i then turned off my pc and went back on it later, but now my pc was unable to connect or even find the other connection that worked. apart from these problems my pc is unable to connect to LAN, it says that there's no  LAN connection even though it is trying to connect to it.

---

### Post by Kirk Schnable on 2012-07-13
> **Frekker said:**
> I went on vacation for a week some days ago, and when i came back my internet was really slow (about 1-6 KB all the time) i couldn't figure out what the problem was, so i connected to the other internet in our house which worked great. i then turned off my pc and went back on it later, but now my pc was unable to connect or even find the other connection that worked. apart from these problems my pc is unable to connect to LAN, it says that there's no  LAN connection even though it is trying to connect to it.

We're there any occurrences while you were gone (power fluctuations, weather events, etc) which may have damaged your hardware?

Sounds like a physical problem to me. Have you tried using different ports in your switch/router? It sounds like only this machine has the issue... So could be a bad port on the switch, bad cable, or bad card. 

I assume there wouldn't have been any software changes taking place while you were on vacation?

Kirk

---

### Post by Frekker on 2012-07-13
it seems like it, we got a new router but that shouldn't change anything. even on my friends 60 Mb connection, my pc receives all from 2,00-600 Kb/s. i don't know why but the other router on the top floor works much better than the one in the basement in the room next to mine. the one on the top floor hasn't got that good of a connection, but it uploads and downloads more securely than the one in the room next to mine. the one next to me gives me a great connection, but is very slow, this connection is around the 2 Kb/s- 500 Bytes/s sometimes 0,0. i think i might have updated some files on my pc before i left, but nothing else i'm not even certain if i actually did.

---

### Post by robtygart on 2012-07-13
Try using a live CD and see if the problem stil happens.

Have you also un-plugged your router and plug it back in?

---

### Post by Frekker on 2012-07-13
What do you mean live CD?
but yes, i did try turning the router on and off

---

### Post by robtygart on 2012-07-13
> **Frekker said:**
> What do you mean live CD?
but yes, i did try turning the router on and off

With your Ubuntu CD or USB you installed your operating system with, it will give you two options, "Try Ubuntu" and "Install" 

Click "Try" then use that to see if you can get online and surf, if your internet works like it should then you know your hardware is fine.

---

### Post by Frekker on 2012-07-14
alright i'll try that!
i do have a suspicion that it's something with my network card. how do i uninstall my network card drivers (to then reinstall and check if that helped)?

---

### Post by Kirk Schnable on 2012-07-14
> **Frekker said:**
> alright i'll try that!
i do have a suspicion that it's something with my network card. how do i uninstall my network card drivers (to then reinstall and check if that helped)?

That sounds like a Windows fix to me. :mrgreen:

Let's worry about one thing at a time.  Try the Live CD, and if it works we'll compare its kernel version and module version with your current setup.  That should give us some clues as to how to proceed, but first thing's first, test it out on a Live CD and let us know.

Kirk

---

