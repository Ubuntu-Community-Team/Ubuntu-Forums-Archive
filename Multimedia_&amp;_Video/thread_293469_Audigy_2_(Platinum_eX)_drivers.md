---
title: "Audigy 2 (Platinum eX) drivers?"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by supaboy on 2006-11-05
Hello,

I am an Windows XP user and would like to switch to Ubuntu, after seeing it yesterday.

But unfortunately Creative doesn't support official drivers for Linux (at least Audigy 2 series), so are there any modified drivers for Audigy 2 Platinum eX (same as ZS)?

Would be great if someone could give me tips and/or tutorial how to do it exactly (don't forget, i don't know anything about Linux CL nor anything close to it).

thanks,
supaboy :)

Edit: Forgot to mention that i have a 6.06 build, because i've heard it is said to be more stable and better for older computers (like mine). Is that so? :)

---

### Post by jamesford on 2006-11-05
ive got the audigy 2 zs, it works out of the box (which it didnt in xp)
the only thing u may have to do is to type 'alsamixer' in a terminal and change hte values for surround and so on and unmute some things to get all speakers working if u got a 5.1 or similar. theres a gui way of doing the same i think but ive never used it, alsamixer in terminal is easy

---

### Post by supaboy on 2006-11-05
> **jamesford said:**
> ive got the audigy 2 zs, it works out of the box (which it didnt in xp)
the only thing u may have to do is to type 'alsamixer' in a terminal and change hte values for surround and so on and unmute some things to get all speakers working if u got a 5.1 or similar. theres a gui way of doing the same i think but ive never used it, alsamixer in terminal is easy

Alright, thanks man (fast response, hehe)! :KS 

Anyway, i will try with this tutorial as well:
[http://files.printf.dk/guides/audigy2.htm](http://files.printf.dk/guides/audigy2.htm)

---

### Post by jamesford on 2006-11-05
id be very surprised if u have to mess with any guide, i can guarantee with 99.9% certainty that it will work without any fiddling unless the platinum ex is very different from the zs (but u say its the same thing)

regarding 6.06 (dapper) or 6.10 (edgy) i dont think either is any better on old hardware than the other, you can have a look at 'choosing an ubuntu release' here [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

id go with edgy, newer software than in dapper

edit: if uve got really old hardware maybe xubuntu will be better. its using the very lightweight xfce desktop environment that will run better on really old computers than ubuntu running gnome (u can install xfce in ubuntu too or gnome in xubuntu by installing the xubuntu-desktop or ubuntu-desktop package, and choose between then at the login screen)

---

### Post by .t. on 2006-11-05
Creative does in fact support Linux. I believe they're the ones that wrote the specs (and perhaps even the code) for the driver.

---

