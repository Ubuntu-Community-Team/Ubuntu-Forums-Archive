---
title: "Commercial DVD Playback"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Steel-Bunz on 2011-04-11
Tried to play the rented DVD, "The Tourist" (from Redbox) in Natty. VLC played the first clip file (Sony Pictures) and thats it. Totem didn't even manage that. I am sure I had libdvdcss2 library installed already.
 
It has been long time since I tried an encrypted DVD movie in Ubuntu. Could anyone please throw some light on this issue? Do I have to install something else?
 
P.S: By the way, never imagined Johnny Depp can choose to act in such a crap story.:( What was he thinking?

---

### Post by thiebaude on 2011-04-11
try this in a terminal sudo /user/share/doc/libdvdread4/install-css.sh

---

### Post by Quackers on 2011-04-11
Have you installed ubuntu-restricted-extras?

---

### Post by go7Ul1ai on 2011-04-11
I just purchased the Fluendo DVD player software from the Ubuntu Software Centre and it works fine.

---

### Post by dnairb on 2011-04-11
IIRC you can run the following as a single command in terminal to add the Medibuntu repository (from which libdvdcss2 is installed), update the packages list and install libdvdcss2 and ubuntu-restricted-extras:


```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update && sudo apt-get install libdvdcss2 ubuntu-restricted-extras
```

---

### Post by ronacc on 2011-04-11
when all else fails [http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)
and get the one that hasn't been butchered by the censors and lawyers .

---

### Post by Steel-Bunz on 2011-04-11
Yes.. Ubuntu-restricted-extras installed. Will check libdvdread4 and mediubuntu repository once I get back to my laptop. Will report back the results..
 
Thanks everyone.. appreciate it..

---

### Post by gnomeuser on 2011-04-11
> **lee.jarratt said:**
> I just purchased the Fluendo DVD player software from the Ubuntu Software Centre and it works fine.

An excellent and universally legally acceptable solution. I, to, am a happy customer.

---

### Post by Steel-Bunz on 2011-04-11
> **thiebaude said:**
> try this in a terminal sudo /user/share/doc/libdvdread4/install-css.sh

Tried this first and it worked. Guess it pulls libdvdcss2 from Mediubuntu repositories..

Thanks again..

---

