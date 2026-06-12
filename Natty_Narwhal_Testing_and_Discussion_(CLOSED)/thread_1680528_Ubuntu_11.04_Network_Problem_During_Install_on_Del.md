---
title: "Ubuntu 11.04 Network Problem During Install on Dell Inspiron E1505"
date: 2011-02-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kj4ohh on 2011-02-02
A friend of mine is trying to install Ubuntu 11.04 on a Dell Inspiron E1505 laptop.

It has a broadcom ethernet adaptor on it as well as a ricoh wireless adapter.

He hasn't had any problems with former version of ubuntu on it in the past but he's having an issue during install.

It's not bringing up the ethernet interface.  When you do ifconfig in console it only shows the loopback device and nothing else.

he's disabled software updates during install but it still gets to one point where it says it's waiting on the network interface card before continuing.

---

### Post by overdrank on 2011-02-03
Moved to Natty Narwhal Testing and Discussion

---

### Post by donniezazen on 2011-02-03
I never has any problems with broadcom before but i don't know what's going on with natty. My ethernet is working but broadcom STA isn't. Hope they fix it soon.

---

### Post by Starks on 2011-02-03
I have 640m/E1405.

No problems during install.

Try modprobe b44

---

