---
title: "MF637U USB modem in Ubuntu 10.04"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by rooroo on 2010-05-04
Hi all, I am completely new to ubuntu but I have great interest in how to use it.

I get a problem of getting it connected to internet with my usb modem MF637U.
May anyone please help me out? 
million thanks!

---

### Post by dv3500ea on 2010-05-04
I'm sorry, but USB modems work terribly in linux because they require Windows software to work. You can try to get a [driver from here]("http://eciadsl.flashtux.org/")

---

### Post by pdc on 2010-05-05
hmmmmmmmmmmmmm

> *work terribly in linux because they require Windows software to work*.

Phew !! that is an extreme statement  ............. in fact many would say that is sadly wrong ................

we'll see if we can help;

plug in your modem

type

> lsusb in a terminal

if it says 

> ID 19d2:0031 

it is ready to configure

.. configure by following the advice on this thread ..

.. half-way down the page .."Create a mobile broadband connection .."

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

you need to know the country you live, and the network you have joined ..

let us know how you get along

---

### Post by dv3500ea on 2010-05-05
I didn't realise it was a 3g modem, I thought it was an ADSL [winmodem]("http://en.wikipedia.org/wiki/Softmodem")
I used to have one which only worked in Windows XP but not Ubuntu or Vista.

---

