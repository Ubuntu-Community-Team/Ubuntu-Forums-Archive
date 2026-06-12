---
title: "VLC does not work"
date: 2012-01-05
forum: Multimedia Software
---

### Post by simba23 on 2012-01-05
I have Ubuntu 11.10 64 bit.  When I install a dvd into my drive VLC opens but nothing happens. I try to hit play and still nothing.  I have VLC 1.1.13.  I have search the forums but can't find nothing yet. Can any one help? Thanks:)

---

### Post by cottfcfan on 2012-01-05
In a terminal try:
```
sudo apt-get install libdvdread4
```
then:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
and then try with VLC again.

---

### Post by simba23 on 2012-01-05
thanks for your input. I entered both lines and retested system. Then installed dvd. VLC started up and ran the movie like it should.

Thanks again, have a great day:)

---

### Post by cottfcfan on 2012-01-05
No problem. Glad you sorted it.

---

### Post by blacklabs on 2013-01-02
Yes, cottfcfan, your suggestion worked for me also.

Thank you very much.

---

