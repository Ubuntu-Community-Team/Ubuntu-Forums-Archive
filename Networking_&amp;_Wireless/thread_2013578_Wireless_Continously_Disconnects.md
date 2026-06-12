---
title: "Wireless Continously Disconnects"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by MckayKnight on 2012-07-01
[FONT="Georgia"]Hi all, I have Ubuntu 12.04 installed and lately I have been getting disconnected from my wifi connection almost every 30 minutes to an hour.

It could be from watching something on youtube, downloading a file, or overall just on xchat.

Ever since I upgraded the kernel it's been acting up the only way I can get my Internet connection to work is to reboot Ubuntu.

I can't tell if it has to do with some type of network kernel bug or some recent update.

Is there anyway I can go about fixing the issue from the terminal or by somewhat downgrading to a older kernel my guess is it could also be a driver problem.

By the way this is an late 2011 System76 model that contains a Intel Centrino Ultimate-N 6300 - 802.11A/B/G/N Wireless LAN Module.[/FONT]

---

### Post by jackyboy633 on 2012-07-01
Hi there,

I don't have a laptop with this wireless module. However, I have googled your problem, and found that you will have to change a driver parameter with these two terminal commands:
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```
This will unfortunately disable Wireless-N so you will not get the fastest speeds, but hopefully the connection should be more stable.

Hope this helps :)

Jackyboy633

---

### Post by wildmanne39 on 2012-07-01
Hi, that most likely will solve the issue if it does it will need to be made permanent.
Thanks

---

### Post by MckayKnight on 2012-07-01
Thanks I'll be sure to remind myself to check it out.

---

