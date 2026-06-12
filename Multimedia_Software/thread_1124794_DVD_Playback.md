---
title: "DVD Playback"
date: 2009-04-13
forum: Multimedia Software
---

### Post by NSAJEFF on 2009-04-13
I'm currently using Ubuntu 9.04 but this issue is identical in 8.10. I insert a dvd(known to work on other systems). I'm prompted to choose which application I want to use and I select "Open Movie Player". Totem? opens up and tells me, "Could not read from resource."

I've installed every single other media player in the repos with no luck.

---

### Post by RedSingularity on 2009-04-13
sudo apt-get install ubuntu-restricted-extras

---

### Post by NSAJEFF on 2009-04-13
Thanks for the help but that didn't fix it.

---

### Post by RedSingularity on 2009-04-13
Now you need the codecs.  Try this in the terminal

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs

---

### Post by RedSingularity on 2009-04-13
The above is if you are using a 32 bit version of ubuntu.  Change the last part "w32codecs" to 64 if you have a 64 bit.

---

### Post by NSAJEFF on 2009-04-13
> **Shadow121 said:**
> The above is if you are using a 32 bit version of ubuntu.  Change the last part "w32codecs" to 64 if you have a 64 bit.


Clever bugger, thanks for your help!

---

### Post by RedSingularity on 2009-04-13
No problem :)

---

### Post by mc4man on 2009-04-13
While it's of no concern in terms of  libdvdcss2 and w32codecs  it's better in the long run not to add sources for different ubuntu releases.
Again because medibuntu is becoming of less and less value no big deal here though very little else in the hardy medibuntu repo will be installable in jaunty

Alternate method in jaunty to installl libdvdcss2 (jaunty uses libdvdread4

```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

