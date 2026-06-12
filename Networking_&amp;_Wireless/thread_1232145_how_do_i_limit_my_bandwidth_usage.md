---
title: "how do i limit my bandwidth usage???"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by burmanabhay88 on 2009-08-05
i want to limit the max bandwidth of my computer. how to go about it????

---

### Post by snek on 2009-08-05
There's no nice GUI app like Netlimiter for Linux.
You'll be stuck with using the ones provided in applications themselves (which I know can be a problem for things like DC++ where the server will ban you for limiting) or going command-line.

Have a look at these 2 applications:
- trickle
- wondershaper

Especially wondershaper is easy to configure if you just want to limit your total up and download. Trickle can be used to limit a certain application as well, but so far it always causes 100% CPU usage on me when I've used it.

I know it's a bitch that there's nothing decent out there, if I knew the right languages and had the right skills I'd program it myself. But I'm a webdeveloper and can only script a mean PHP/MySQL application :P

---

### Post by burmanabhay88 on 2009-08-05
> **snek said:**
> There's no nice GUI app like Netlimiter for Linux.
You'll be stuck with using the ones provided in applications themselves (which I know can be a problem for things like DC++ where the server will ban you for limiting) or going command-line.

Have a look at these 2 applications:
- trickle
- wondershaper

Especially wondershaper is easy to configure if you just want to limit your total up and download. Trickle can be used to limit a certain application as well, but so far it always causes 100% CPU usage on me when I've used it.

I know it's a bitch that there's nothing decent out there, if I knew the right languages and had the right skills I'd program it myself. But I'm a webdeveloper and can only script a mean PHP/MySQL application :P

thanks for the help... but i found something better. it's called pyshaper.
[INSTALL PyShaper: http://ubuntuforums.org/showthread.php?t=993210]("http://ubuntuforums.org/showthread.php?t=993210")
it's similar to NetLimiter

---

