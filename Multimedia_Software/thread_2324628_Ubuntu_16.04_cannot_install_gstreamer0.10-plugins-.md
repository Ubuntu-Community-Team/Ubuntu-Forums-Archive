---
title: "Ubuntu 16.04 cannot install gstreamer0.10-plugins-bad / ugly"
date: 2016-05-15
forum: Multimedia Software
---

### Post by uli9 on 2016-05-15
I am trying to rip a DVD with handbrake. Some documentation seems outdated. It looks like I need to install 'gstreamer0.10-plugins-bad and ugly'. Not simple. I added 'http://security.ubuntu.com/ubuntu' to the download repositories, as suggested in some documentation. But now Synaptic has a dependency issue. How can I get the DVD to work.

---

### Post by mc4man on 2016-05-15
Use handbrake from here, it will install all needed deps except libdvdcss2 (if dvd is encrypted
handbrake uses gstreamer1.0*
[https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases)

---

### Post by uli9 on 2016-05-15
OK I did that. Still not getting anywhere. Totem doesn't play the DVD.
In handbrake, what do I choose as the source? It doesn't just accept the DVD drive. There are so many video / audio files?

---

### Post by uli9 on 2016-05-15
OK, so I installed libdvdcss2 and it looks like everything works now.
Thanks for all your help......

---

