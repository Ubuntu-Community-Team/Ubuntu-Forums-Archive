---
title: "enabling modprobe ath_pci on startup???"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by YasirMX on 2009-07-15
hello, i've got madwifi running on hardy on my pavilion dv6820ea but the peoblem is each time i have to type sudo modprobe ath_pci 

then wireless will start working..how do i integrate it into startup permanently??any suggestions??

---

### Post by grappler on 2009-07-15
I thought you  should just put it into /etc/modules.conf file but then I discovered that ubuntu no longer has one. This site explains what to do I think - though for sound modules. 

[http://www.devhardware.com/forums/operating-systems-18/ubuntu-question-no-modprobe-conf-91626.html](http://www.devhardware.com/forums/operating-systems-18/ubuntu-question-no-modprobe-conf-91626.html)

---

### Post by t0mppa on 2009-07-15
> **grappler said:**
> I thought you  should just put it into /etc/modules.conf file but then I discovered that ubuntu no longer has one.

Indeed, the .conf was taken away at some point and it is only */etc/modules* now, but it still works just the same.

---

### Post by ubunny on 2009-07-15
my /etc/modules file has

lp
ath_pci


that's it.  Thus it loads ath_pci on startup and my madwifi can connect.

Cheers

---

### Post by YasirMX on 2009-07-15
> **ubunny said:**
> my /etc/modules file has

lp
ath_pci


that's it.  Thus it loads ath_pci on startup and my madwifi can connect.

Cheers

Thanks man..problem solved :) penguin rocks :)

---

