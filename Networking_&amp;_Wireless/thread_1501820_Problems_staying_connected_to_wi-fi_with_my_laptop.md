---
title: "Problems staying connected to wi-fi with my laptop."
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by pyromaniacwolf1994 on 2010-06-04
Hi, I am relatively new to Ubuntu, and Linux, and I am having a problem with it that I was hoping to get fixed. Whenever I try to connect to my home wi-fi network, on Ubuntu 10.04 Lucid Lynx, it keeps disconnecting and reconnecting...which makes it really hard to download various things. It works just fine whenever I used "shudders" Windows Vista but whenever I try to use it on Ubuntu, it won't work properly. The router I bought, to replace my old, broken one, was Linux compatible, or at least that's what it was advertised as... Anyway any help would be very much appreciated. The laptop is an HP G70 and the method I used to download Ubuntu was the Windows Installer. Thanks and have a great day.

---

### Post by madverb on 2010-06-04
Try:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

