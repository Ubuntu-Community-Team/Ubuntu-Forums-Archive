---
title: "capture board - pixelview play tv pro ultra"
date: 2005-11-06
forum: Multimedia &amp; Video
---

### Post by xlobo on 2005-11-06
Hi! I'm a Linux beginner and I'm trying to install my capture board (pixelview play tv pro ultra). But I can't. I don't watch nothing! What do I have to do (from the beginning) to install it?

Thanks any way

---

### Post by kakashi on 2005-12-02
you can try gogle. 
i am about to buy a pixel view play tv card today (about to leave to get it) so i'll answer your question. in the mean time do tell us  what chipset it is, and any other info you can give. 
als ocheck out [http://www.exploits.org/v4l/](http://www.exploits.org/v4l/)

---

### Post by kakashi on 2005-12-03
ok here you go. 
first you have to find out what card and tuner you have. 
min was pixel view play tv pro with conexant tuner.

next dl a kernel source from kernel.org.
unpack it. 
look in the documentation for videoforlinux and in there for CARDLIST.bttv and CARDLIST.tuner. use that to figure out the number of your card and tuner. 
do 
[code]
modprode bttv card=?? tuner=??
[code]
build xawtv from source. (cvs)(imo its best)
use 
xawtv -hwscan to see if your card is ok.
install tvtime from synaptic. 
run tvtime-scanner. see if it pickup any channels.

i will write a full how to this in a while once i perfect this. in the mean time try it and please give feedback.

---

### Post by acegautam on 2008-01-21
Hi kakashi,

Eve i am a newbie to linux and am already lovin ubuntu gutsy :-) I was really interrested in your detailed writeu tht u were plannin to put.. wud b really helpful if u cud do tht asap... thanx...

adios,
gautam

---

### Post by b0rka7a on 2008-01-23
> **acegautam said:**
> Hi kakashi,

Eve i am a newbie to linux and am already lovin ubuntu gutsy :-) I was really interrested in your detailed writeu tht u were plannin to put.. wud b really helpful if u cud do tht asap... thanx...

adios,
gautam

**kakashi - Last Activity: August 15th, 2007**
:lolflag:
btw, what is "asap" ? :D

---

