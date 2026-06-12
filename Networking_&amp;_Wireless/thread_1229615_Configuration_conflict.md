---
title: "Configuration conflict?"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by terryq on 2009-08-02
My setup is a desktop pc (ethernet internet connection)  with Jaunty installed and I have a Dell Netbook with Ubuntu 8.04.2 pre-installed. I have no problem connecting the netbook wirelessly to the internet but I cannot  access the same webpage from both the pc and netbook at the same time. For example, I am unable to play an online game with an opponent on the netbook or vice-versa. Can anybody advise what the problem is with my configuration settings?

---

### Post by Brandon Williams on 2009-08-02
It's quite possible that the web site in question is making use of specialized settings in your router, or that the web site is expecting only a single session from a specific IP address (the one being used by the router). Are there multiple sites that exhibit such problems? Or is it some site in particular?

---

### Post by terryq on 2009-08-02
Thank you for the reply Brandon.

I am not sure I understand entirely what you have tried to explain but with regard to your last point I am having trouble with one site in particular, namely Wordsteal. If you are not familiar with this site it is a word game. I login on my desktop and my opponent is then unable to login on the laptop.

---

### Post by Iowan on 2009-08-02
> **Brandon Williams said:**
>  or that the web site is expecting only a single session from a specific IP address (the one being used by the router). Just my translation (and I'm NOT King James):
If your router is a NAT (Network Address Translation) router, the website thinks both the desktop and laptop are the same machine (only the router knows otherwise), and it may not permit you to play against "yourself".

---

