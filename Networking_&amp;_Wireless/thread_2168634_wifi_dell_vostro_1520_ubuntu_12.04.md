---
title: "wifi dell vostro 1520 ubuntu 12.04"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by sandrum on 2013-08-18
I have a dell vostro 1520 with ubuntu 12.04. The by default controller for wifi conection doesn't work inmedialely. It worked once I used these commands I've found on forums:

sudo rmmod dell_laptop
echo 'blacklist dell_laptop'
sudo tee /etc/modprobe.d/blacklist-custom

It did work, but I have to enter those commands everytime I restart my laptop. I'd like some solution for this problem, Is there someone who knows what is wrong?

Thanks

Sandra

---

