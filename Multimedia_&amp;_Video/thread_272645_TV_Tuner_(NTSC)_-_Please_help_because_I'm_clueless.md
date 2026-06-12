---
title: "TV Tuner (NTSC) - Please help because I'm clueless!"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by insub2 on 2006-10-06
I Have a [nVIDIA GeForce FX5600/XT]("http://www.chaintechusa.com/tw/eng/product_spec.asp?MPSNo=14&PISNo=197") and i need to know how to use the tv tuner (NTSC) with linux.  I have no idea how to do this so please be detailed if you can.

---

### Post by mindstorm011 on 2006-10-07
```
sudo apt-get install nvtv
```
You can even use it with the open-source nv driver

---

### Post by insub2 on 2006-10-07
> **mindstorm011 said:**
> ```
sudo apt-get install nvtv
```
You can even use it with the open-source nv driver

Thank you!  I'll give that a try tonight when I get home and let you know how it works out.

---

### Post by insub2 on 2006-10-08
oops.  nvtv is for tv out.  i want tv in.  what should i do for that?

---

### Post by woekele on 2006-10-09
Uhm, I use 'xdtv' with my tv-card, gues it will also work with a tv-in, if it's supported.

---

### Post by gandalf2041 on 2006-10-09
There are several programs you could try. I use xawtv but, I'm not thrilled with it.  There's also: zapping, tvtime or kdetv (if you're running Kubuntu).  Any of these programs should work if your card is supported.

---

