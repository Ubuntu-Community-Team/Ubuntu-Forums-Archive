---
title: "make ssh persistent?"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by irishetalon007 on 2012-08-06
Is there any way to make ssh terminal persistent?

ex. I ssh into a computer, run "sudo apt-get install upgrade," then logout of the ssh session and the upgrade continues?

---

### Post by Grenage on 2012-08-06
You'll want to look into *screen*.  It basically does what you want; creating terminal instances and detaching/reattaching from them.

---

### Post by irishetalon007 on 2012-08-06
brilliant! thanks

---

