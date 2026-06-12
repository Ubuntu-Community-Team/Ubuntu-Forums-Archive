---
title: "Setup laptop running ubuntu 10.04 into router"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by robteh on 2010-06-18
Hello guys. How can i setup my computer (currently running Ubuntu 10.04 lts) into a router so that other laptop can have a wireless connection to it and be able to access the internet?

---

### Post by wojox on 2010-06-18
[Setting up an Ubuntu Wired/Wireless Router]("https://help.ubuntu.com/community/Router")

---

### Post by robteh on 2010-06-18
Thanks for the useful link, but I've stumbled on another problem. I am supposed to edit /etc/network/interfaces  but it shows up in my gedit as a read-only and so i'm unable to make changes to it. How can I solve this?

---

### Post by robteh on 2010-06-18
never mind, I fixed the above problem by using nano

---

### Post by Iowan on 2010-06-18
> **robteh said:**
> never mind, I fixed the above problem by using nano
**sudo** would be the secret... or **gksudo** **(gksu**) with a graphical editor (**gedit**).

---

