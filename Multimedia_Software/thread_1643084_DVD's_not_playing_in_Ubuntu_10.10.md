---
title: "DVD's not playing in Ubuntu 10.10"
date: 2010-12-11
forum: Multimedia Software
---

### Post by colkey on 2010-12-11
Hello
I am trying to get some DVD's to play in Ubuntu 10.10 but whenever i try to play them i get an error message saying "Could not read from resource". 
I am pretty new to Linux and Ubuntu
Thank you in advance!
Colkey

---

### Post by slooksterpsv on 2010-12-11
Click Applications -> Accessories -> Terminal, a purple window should appear, run the following command (you can copy then edit paste in Terminal):
```

gksudo apt-get install libdvdread4 && gksudo sh /usr/share/doc/libdvdread4/install-css.sh

```
After you paste that in, press Enter. It'll prompt you for your password and install the necessary components.
After that's done, close down your media players open and test! =D

---

### Post by colkey on 2010-12-11
thanks 
that seems to have improved the situation but now it asks me to install a plugin but when i click search for required plugin, the search returns no results. The plugin is called dvd source

---

### Post by slooksterpsv on 2010-12-11
Have you installed the: ubuntu-restricted-extras ? You can find it in Software Center. If not install that.

---

### Post by colkey on 2010-12-11
Yes

---

### Post by Yellow Pasque on 2010-12-12
Look in Synaptic and make sure that libdvdcss2 and libdvdnav4 package are actually installed.

---

### Post by Rocko262c on 2011-01-14
Hey Everyone,
I have the same problem with 2 fresh installations of Ubuntu 10.10.  I have followed all your directions and made sure that libdvdnav4 and libdvdcss2 are installed, but I can't play any DVD's on my computers.  I have always been able to play DVD's before with both of these computers.  Can you please help with more suggestions than above?
Thanks,
Rocko262c

---

### Post by E3SEL on 2011-01-22
get vlc media player from the ubuntu software centre

---

### Post by SGT Pete on 2011-06-05
> **slooksterpsv said:**
> Click Applications -> Accessories -> Terminal, a purple window should appear, run the following command (you can copy then edit paste in Terminal):
```

gksudo apt-get install libdvdread4 && gksudo sh /usr/share/doc/libdvdread4/install-css.sh

```After you paste that in, press Enter. It'll prompt you for your password and install the necessary components.
After that's done, close down your media players open and test! =D


This solved my problem, my DVD is playing with VLC just fine now.

Thanks!

---

### Post by grabledj on 2011-11-17
Worked great - thanks for the information!!

---

