---
title: "Cannot read from resourse?"
date: 2011-07-28
forum: Multimedia Software
---

### Post by oxf on 2011-07-28
Hi

 When I try to play a DVD using several common players I get the error message " cannot read from resourse"

What does this mean and what am I missing?

Thanks

---

### Post by mc4man on 2011-07-28
Most times it means you don't have libdvdcss2 installed
Search out medibuntu or just run a small script included in libdvdread4

If libdvdread4 isn't installed this will ck, do so if need be and install libdvdcss2 - copy & paste as 1 command in a terminal
```
sudo apt-get install libdvdread4 && \
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by oxf on 2011-07-29
> **mc4man said:**
> Most times it means you don't have libdvdcss2 installed
Search out medibuntu or just run a small script included in libdvdread4

If libdvdread4 isn't installed this will ck, do so if need be and install libdvdcss2 - copy & paste as 1 command in a terminal
```
sudo apt-get install libdvdread4 && \
sudo /usr/share/doc/libdvdread4/install-css.sh
```

That seems to ahve fixed it. Thanks!

libdvdread4 was already there but not livdvdcss2

---

