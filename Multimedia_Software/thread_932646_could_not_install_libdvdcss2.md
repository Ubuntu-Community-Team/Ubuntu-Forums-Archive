---
title: "could not install libdvdcss2"
date: 2008-09-28
forum: Multimedia Software
---

### Post by sdybruce on 2008-09-28
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

what should i do?
thanks

---

### Post by lisati on 2008-09-28
Depending on your system setup, the following entered in the terminal might work, without the need to add extra repositories:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by sdybruce on 2008-09-28
That worked and my dvd player works now this is great, thanks so much!!:D

---

### Post by ssivaguhan on 2010-06-06
Thanks, that worked for me.

I used sudo /usr/share/doc/libdvdread4/install-css.sh on my Lucid.

---

