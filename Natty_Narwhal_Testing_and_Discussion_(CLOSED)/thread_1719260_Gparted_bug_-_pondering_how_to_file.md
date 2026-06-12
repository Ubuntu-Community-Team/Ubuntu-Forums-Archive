---
title: "Gparted bug - pondering how to file???"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-04-01
I'm attempting to save the data from a torched laptop so I popped the drive in my box and I wanted to begin with Gparted just so I could see what I'm working with. No problem there:

[ATTACH]187792[/ATTACH]

But I knew I was running Natty on sda18. Look here:

[ATTACH]187793[/ATTACH]

You can see that df finds sda18 is mounted but Gparted doesn't display that with the typical lock.

So I'm wondering what package to file a bug against. I'm thinking libparted but I'm not sure. The currently installed version is "libparted0debian1".

Gparted is one of those apps that lacks "report problem".

---

### Post by kansasnoob on 2011-04-01
Ha, I just needed to wake up:

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/605975](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/605975)

---

