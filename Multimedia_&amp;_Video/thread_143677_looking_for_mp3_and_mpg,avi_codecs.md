---
title: "looking for mp3 and mpg,avi codecs"
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by macgip on 2006-03-12
hello guys I'm trying to play mp3 files and mpeg,ave files were do i go to get the codcs?:confused:

---

### Post by John.Michael.Kane on 2006-03-12
```
## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free


```

sudo gedit /etc/apt/sources.list add the list to bottom, and look for what you want in synaptic. **also make sure it is legal for you to use said codecs in your country....**

---

### Post by Darkness3477 on 2006-03-12
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

I had to try a fw of the methods there to get the mpg's working properly, but it only took about 30 mins.

---

### Post by red_shrike on 2006-03-15
you can also use Automatix or simply search "codecs" with Synaptic. Select everything you need (w32codecs,...). Install xine and mplayer too.

---

