---
title: "Hardy PulseAudio with Montego DDL?"
date: 2008-06-30
forum: Multimedia Software
---

### Post by NoThanksM$ on 2008-06-30
I've done a bunch of searching but have not found much information on this.  Does anyone know how well (or even if) the Turtle Beach Montego DDL card works in Hardy? It has worked well right out of the box for me in both Feisty and Gutsy, but I didn't know how the change to PulseAudio might affect things.

---

### Post by gleenn on 2008-09-25
Nope, I've had all kinds of trouble with my Montego DDL that were non-existant in previous versions. I bought the card just because of the hardware mixer which meant better linux support I thought, and now it seems I have spent quite a lot of time getting no where. I finally got sound after I reverted to an earlier kernel, and I lost my hardware mixing again which means I can't listen to two sound sources simultaneously.

---

### Post by NoThanksM$ on 2008-09-25
Really?  I honestly haven't had a hitch with it since upgrading to Hardy. That card has always worked for me without any special configuration (literally plug-n-play) in Ubuntu, and 8.04 was no exception. 
You mentioned listening to two sound sources simultaneously - I don't know that I've ever tried to do that (I'm not at that computer right now so I can't test it).  When you weren't getting sound, was it not working out of both the analog and digital outputs?

---

### Post by gleenn on 2008-10-18
I can't check the digital out, I don't have digital speakers, but it definitely doesn't come out of the analog. I since reverted to a previous kernel 2.6.24-16 and it works in there but without multiple sources and still doesn't work in either 2.6.24-19 or 2.6.24-21. Quite disappointing. It didn't give me any trouble before either in Gutsy.

---

