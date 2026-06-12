---
title: "cant install a dial up modem"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by freeburn on 2009-04-30
i'm a new ubuntu user. i'm using ubuntu 8.04LTS. i'm facing difficulties to set up my modem. i've tried to follow the documentation but it didn't work. mine is a dial up modem."qualcom 3197".

i've tried to use wvdial but the whenever i try to edit wvdial.conf to include the details of dialing number and password, i cant save the file.it didnt let me to save it. 

and what is stupid mode?

---

### Post by coutts99 on 2009-04-30
Edit wvdial.conf in a konsole using sudo -:

> sudo nano -w /etc/wvdial.conf

---

### Post by freeburn on 2009-04-30
what is "-w" here? i was using "-c" ,i heard it from one of my friends

---

### Post by coutts99 on 2009-04-30
Don't wrap long lines, ignore just habit :)

---

