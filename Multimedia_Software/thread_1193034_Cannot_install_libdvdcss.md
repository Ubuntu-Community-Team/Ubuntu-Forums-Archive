---
title: "Cannot install libdvdcss"
date: 2009-06-21
forum: Multimedia Software
---

### Post by Onisutra on 2009-06-21
Every time I try to install I get this error: 

Package libdvdcss2 has no installation candidate
Package libdvdcss3 has no installation candidate
Package libdvdcss4 has no installation candidate

And I have tried everything I could.. I just cannot get it working. plz help, I would really like to play DVDs again.

Thanks

---

### Post by mc4man on 2009-06-21
Here's a slightly extended command that should work for you (just makes sure you have libdvdread4 first

```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```


or get directly or add medibuntu repo

[http://packages.medibuntu.org/jaunty/libdvdcss2.html](http://packages.medibuntu.org/jaunty/libdvdcss2.html)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by T.J. on 2009-06-21
There is a reason for that.  Libdvdcss is of highly questionable status in the United States and some other countries, subject to WTO treaties or local laws similar to the U.S.'s DMCA.  It's not in the regular archives. You can get it from Mediabuntu, but you might have legal troubles if you use it.  To my knowledge, libdvdcss's method of decoding has never been challenged in court, but you have a risk.

---

### Post by credobyte on 2009-06-21
You can get it from [Mediabuntu]("https://help.ubuntu.com/community/Medibuntu") ( keep in mind what T.J. said ).

---

