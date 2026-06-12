---
title: "bluez-pin in Synaptic?"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by -DarkAceZ- on 2011-06-24
I read in [this thread]("http://ubuntuforums.org/showthread.php?t=10500") that I need bluez-pin, but it's no where to be found in synaptic. Do I need to get it a separate way?

---

### Post by bruno9779 on 2011-06-24
I have bluez package in synaptic. That will probably pull all the dependencies needed.

On the other hand, the thread you link to is 6 years old.

Someone is having issues with Bluetooth after upgrading to 11.04 : [http://ubuntuforums.org/showthread.php?t=1726717](http://ubuntuforums.org/showthread.php?t=1726717)

If that is the case, you can install other builds from launchpad : [https://launchpad.net/ubuntu/+source/bluez](https://launchpad.net/ubuntu/+source/bluez)

---

### Post by -DarkAceZ- on 2011-06-24
That doesn't appear to be my problem though. Zire 72 stops at "Signing on" with an Error: PPP timout (0x1231). I thought either it has to be because I never saw bluez-pin or it's because I have the wrong Pin numbers in /etc/ppp/peers/dun. (I KNOW I have the wrong ones, so if bluez-pin isn't the issue, its this!)

I'm not sure how to get my Palm pin number, since I haven't connected yet. In my Palms Connection settings I have Query DNS checked and IP address Automatic.

---

### Post by bruno9779 on 2011-06-24
Bluez-pin is nnot available since dapper.

Have a read at the replies on this launchpad page, it may help clarifying:

[https://answers.launchpad.net/ubuntu/+question/28044](https://answers.launchpad.net/ubuntu/+question/28044)

---

### Post by -DarkAceZ- on 2011-06-24
OK, I see. Now what should I do about /etc/ppp/peers/dun?

---

### Post by -DarkAceZ- on 2011-06-24
Was /etc/bluetooth/pin Changed to /etc/ppp/peers/dun?? (Because I don't have /etc/bluetooth/pin...)

SOLVED:Bluez-pin is not available since dapper.

---

