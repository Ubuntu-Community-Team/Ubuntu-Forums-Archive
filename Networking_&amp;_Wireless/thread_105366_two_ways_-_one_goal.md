---
title: "two ways - one goal"
date: 2005-12-18
forum: Networking &amp; Wireless
---

### Post by ossi on 2005-12-18
Hello!

I use two different ways to get to the web - wireless and cable. For wireless I just got to use a shortcut and it will work. Anyway, if i use cable connection, i do have to go to console and use ifdown and ifup. Isnt there a programm that could check if there is a signal and then use that way? How could it be configured better?

---

### Post by daschl on 2005-12-18
well let the tim taylor-spirit flow and write a script :D

you can send a ping or something like this to a known host and if the host answers, there is connection. (ok at first you have to rund dhclient or set the ip-adress manually)

this you can bind on a shortcut (if you place the script in /usr/bin/ you only have to write the name) dont forget to make the script executeable :)

hope this helps

---

