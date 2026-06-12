---
title: "at&amp;t with aircard 875u on 10.04"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by vfds34 on 2010-05-11
Hello,

I am trying to use aircard 875u with ubuntu 10.04

The card seems to instal well, and it shows up under network manager... it is there under accelerated mode

but then when I try to connect to it/click on it, it asks for password for mini card or something Incorporated? I mean.. does it mean the cingular1 as password...? cant seem to get it to work.

---

### Post by pdc on 2010-05-11
so have you configured it to the network you will use it on?

eg as here:

half-way down page: create a mobile broadband connection

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

I enclose a screenshot from network manager of one type of cingular setup

does this help you? You surely need to select the plan you are subscribed to, and select it from the AT & T option that network manager gives you?

---

### Post by vfds34 on 2010-05-12
> **pdc said:**
> so have you configured it to the network you will use it on?

eg as here:

half-way down page: create a mobile broadband connection

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

I enclose a screenshot from network manager of one type of cingular setup

does this help you? You surely need to select the plan you are subscribed to, and select it from the AT & T option that network manager gives you?

this particular usb modem supposed to work straight out of the box with gnome networking.

The gnome recognized the card, and recognized the network, and even assigned appropriate APN if I am not mistaken

The pharscape pics are for a much older version of the manager, and new manager seems to have set upped/recognized everything just right... recongized the usb device, recognized the network it should work with(guess from the sim card), assigned APN and what have you.. but still asks for password. My guess was a cingular1 for password... but, no luck.

And the question asks for the password for the mini card/device Incorporated? not log in to internet or anything... probably it is something stupid.

---

### Post by vfds34 on 2010-05-16
Solution found. All works fine now... but is it just me... or is Ubuntu 10.04 slower than 9.10? 9.10 seemed to me to be working overall much faster at least on older machines... such IBM x31 notebooks. Anyways... device works fine now. Cheers.

---

### Post by pdc on 2010-05-16
well done to get all working

> [I]but still asks for password. My guess was a cingular1 for password... but, no luck.

And the question asks for the password for the mini card/device Incorporated?[/I] not log in to internet or anything... probably it is something stupid.

> **Solution found. All works fine now.**.

Do tell us how you got it working: it will help others 

... and ..... if you mark your thread as **SOLVED** that will help others too

---

### Post by vfds34 on 2010-05-16
The problem in this case was not with linux and there wasn't any real  solution to be posted here, I had an older plan with att and me crossing  canada-us border apparently triggered something(if i understood them  right)... I called att support and they did reset something on their  side. That is all.  (Although figuring it out took a bit of time)

Asides from above... remember to have username and password field empty,  APN is ISP.CINGULAR (at least for me, it might be different for you  depending but at least 10.04 should recognize what it supposed be for  you). Not sure what more to say... the entire thing supposed be  relatively simple...

also, don't be afraid to call your tech support center... that is why  they are there... either att or sierra wireless might help you with some  detail, true they might hold you on the line for hours(Especially if it  is a weekend) but they can be very helpful(sometimes)

---

### Post by pdc on 2010-05-16
many thanks; this is very helpful; all best wishes

---

