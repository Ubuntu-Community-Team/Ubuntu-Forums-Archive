---
title: "Using the hcitool to detect RSSI"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by tianshiz on 2009-01-09
Hey guys, 
I just installed ubuntu the other day, so i'm a complete newbie. I would appreciate it if i could get some help here!
I've been trying to create a setup with:
-ubuntu hardy + bluetooth adapter
-Sparkfun bluesmirf gold
My plan, at least for now, is to measure the RSSI signal between the bluesmirf and the computer on every room in the floor. 

i have the bluesmirf paired via minicom, and when i run this:
```
$ sudo hcitool rssi 00:xx:xx:xx:xx:xx
```
I get return value that ranges from 0 to 36. In a fixed position, the rssi reported is pretty consistent after many trials. However, I recall that rssi values goes up alot higher. I only get 36 when I put the bluesmirf right next to the adapter. If I move say 5 meters or so, the value drops to 0. This doesn't make any sense, as the bluesmirf has a range of 100m and does not lose its pairing anywhere on the floor.

Does anyone know what could be the problem here? 
Thanks for the help!

---

