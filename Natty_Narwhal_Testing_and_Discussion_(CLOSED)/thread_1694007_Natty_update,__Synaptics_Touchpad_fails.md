---
title: "Natty update,  Synaptics Touchpad fails"
date: 2011-02-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by david stevenson on 2011-02-23
Todays updates have stopped all pointer movement from the touchpad.
Dmesg and Xorg.log look much the same as a working system.
Any suggestions as to where else to look?
David

---

### Post by donniezazen on 2011-02-23
Yeah happened to me too.

---

### Post by mc4man on 2011-02-23
same here, couldn't find bug though can't imagine one or more hasn't been filed.
so reported anyway
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/724051](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/724051)

---

### Post by ventrical on 2011-02-23
yepp, yepp.. same thing here after update. Poof! No more touchpad mouse pointer!!

Acer Aspire 3620

---

### Post by Kelvari on 2011-02-23
Sadly, the same to report on a Toshiba Satellite L45. Glad to know that I'm not the only one, but here's hoping that they manage to get it fixed soon. Not posting on the actual bug report, though, because I don't want to add just another "me too" post on there.

In the meantime, though....:popcorn:

---

### Post by Harry33 on 2011-02-24
> **Kelvari said:**
> Sadly, the same to report on a Toshiba Satellite L45. Glad to know that I'm not the only one, but here's hoping that they manage to get it fixed soon. Not posting on the actual bug report, though, because I don't want to add just another "me too" post on there.

In the meantime, though....:popcorn:

If you have this installed, there is something wrong with this new buid:
xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu4

---

### Post by hapee on 2011-02-24
Same here on a Compaq 6720s luckily my usb mouse still works

---

### Post by MacUntu on 2011-02-24
Guys, please don't just "me too" here - follow the instructions/questions in the [bug report](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/724051).

If you have some time, you can also check IRC (#ubuntu-devel, user RAOF).

---

### Post by david stevenson on 2011-02-24
Excellent service, I ask for advice on how to check out my problem, and I get a bug report and a fix within 20hours.  :)
 sudo apt-get install libutouch-frame1
and I have a working mousepad.
Now to learn about these new multi touch actions.....

---

