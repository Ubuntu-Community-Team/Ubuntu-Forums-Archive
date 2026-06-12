---
title: "dvd wont play"
date: 2013-11-20
forum: Multimedia Software
---

### Post by Brotell1950 on 2013-11-20
i am using both vlc and kaffine neither will play my dvds but will play audio cds i have installed the restricted codecs but to no avail any help will be appreciated.



Terry

---

### Post by sammiev on 2013-11-20
Have added the following?

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

A reboot is required.

---

### Post by Brotell1950 on 2013-11-20
thankyou solved

Terry

---

