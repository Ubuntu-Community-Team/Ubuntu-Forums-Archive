---
title: "Good linux friendly capture card?"
date: 2009-01-20
forum: Multimedia Software
---

### Post by thegreenblob on 2009-01-20
Basically I want to hook my game consoles up to a capture card so I can play them on my monitor while easily switching and using my PC. :)

And maybe some occasionally recording. So... does anyone know of a linux friendly capture card? (AKA has drivers and is not a hassle to set up) And any recommendations on software to use it with? (To do the above)

It can be internal or external, I don't really care. (As long as it doesn't cost a fortune :lol:) I tried searching but couldn't find a thread with recommendations. Thanks in advanced. :p

---

### Post by xzero1 on 2009-01-20
I recommend the older bt878 based cards. I have a Hauppage wintv go which would work fine if you don't need s-video. You might have problems with unaccelerated graphics cards though. You probably don't want a hardware encoding card because this could delay the sound. I can easily monitor a composite video signal real-time with tv-time. Check the [http://linuxtv.org/v4lwiki/index.php/Main_Page](http://linuxtv.org/v4lwiki/index.php/Main_Page) for more info.

---

### Post by wolfen69 on 2009-01-20
i use a Hauppauge PVR150 pci card. all that's needed to get it going is ```
sudo apt-get install ivtv-utils
```

---

