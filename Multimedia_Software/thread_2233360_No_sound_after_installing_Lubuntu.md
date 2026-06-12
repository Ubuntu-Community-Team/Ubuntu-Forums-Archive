---
title: "No sound after installing Lubuntu"
date: 2014-07-08
forum: Multimedia Software
---

### Post by tranceslave on 2014-07-08
Hello guys, after using ubuntu 12.04 on my packard bell laptop (an old one) I decided to switch to Lubuntu 14.04 to make it run smoothlier. After I install the OS the laptop cannot detect any sound. Here is my alsa information [http://www.alsa-project.org/db/?f=319cfa5af4aac4bbe974026e9b74a923d6a86e73](http://www.alsa-project.org/db/?f=319cfa5af4aac4bbe974026e9b74a923d6a86e73)

---

### Post by patsev-anton on 2014-07-12
lspci -knn | grep "Audio" -A2

---

