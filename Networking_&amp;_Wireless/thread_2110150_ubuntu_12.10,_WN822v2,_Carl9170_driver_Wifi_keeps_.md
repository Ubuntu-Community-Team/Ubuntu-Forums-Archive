---
title: "ubuntu 12.10, WN822v2, Carl9170 driver Wifi keeps dropping"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by Onyx879 on 2013-01-29
Hello
I am a new linux user and recently had installed it as dual boot with windows 7 as i had been wanting to try linux for months now however one of the problems that i have came across is that my WiFi keeps dropping every 5-10 minutes or seconds (if im downloading)
i had listed what i am using in the title and will gladly assist if you require me to run a command or download something.

Thanks

---

### Post by chili555 on 2013-01-29
Will you please try a temporary driver parameter:```
sudo modprobe -r carl9170
sudo mpodprobe carl9170 noht=1
```If it helps, we'll write a quick file to make it persistent.

---

