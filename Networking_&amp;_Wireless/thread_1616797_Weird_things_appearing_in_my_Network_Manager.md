---
title: "Weird things appearing in my Network Manager"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by fabjoa on 2010-11-08
Howdie Ubuntians,

So i have two wireless interfaces. One is a built-in wifi card (atheros) and the other one is a USB antenna (realtek). right now, i'm a little bit far away from my router, so I use the antenna which has a wider range. usually, atheros finds few or none access points. But (see attached screen shot), it began displayed new APs with weird characters in it. What do you think it is? Also, what does the symbol circled in blue means (out-of-subject, i know ...)

Thanks!

---

### Post by spiky001 on 2010-11-08
I found these as well the little tele screen is an adhoc connection, Have you setup a adhoc connection? The 1's with th charactures will connect to that

---

### Post by fabjoa on 2010-11-08
I did actually, not knowing what I was doing :) But the one I created was called "test". Maybe the neighbours are setting ad hoc connexions and I can see them. But shouldn't a ad hoc be visible only to people sharing the same router?

---

### Post by spiky001 on 2010-11-08
Not sure what happens but I set 1 as well at weekend got the same as you but they were all mine yes I got more than 1 as well but they all connected to my adhoc No they will show up if they broadcast, I just set up 1 machine connection as adhoc no router involved found it with 3 other machines

---

### Post by uncaspi on 2010-11-08
You can set your card to managed mode.
sudo /sbin/iwconfig (your card i.e eth1,wlan0 or whatever) mode managed

---

